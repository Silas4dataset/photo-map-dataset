# Merged-instance correspondence protocol

This document specifies counting and scoring. It does not include an executable
evaluator, predictions or model weights, and does not claim an independent test set.

## 1. Instance construction

A GT identity instance is an image-specific typed OSM identity. Merge all active
matched GT regions with the same typed ID in the same image. The same identity
in different images is counted separately. `way/123` and `relation/123` differ.

Merge predictions independently using their own submitted typed IDs. Do not use
GT to select correct components, discard wrong IDs or form groups. UNKNOWN,
no-candidate and abstained regions each remain separate prediction instances.
Geometric merging uses the union of component rectangles in upright image
pixels, preserving disconnected regions and counting overlaps once; it does not
fill the gaps between rectangles. This is rectangle-union scoring, not mask IoU.

Different IDs do not merge merely because they are adjacent or semantically
acceptable. Each instance participates in at most one geometric association.
Prediction grouping depends on submitted identities, so this is not an
identity-independent detector metric.

## 2. Geometry association

For GT rectangle union UG and prediction rectangle union UD:

```text
union_iou   = area(UG intersect UD) / area(UG union UD)
part_iou    = maximum IoU over a pair of constituent GT/prediction rectangles
support_iou = max(union_iou, part_iou)
```

The primary support-IoU threshold is 0.3, with 0.5 as a sensitivity comparison.
Compare unrounded values. Correct identity without qualifying geometry is not
a correct association.

Per image, maximize the number of one-to-one qualifying associations, then the
sum of support IoU among assignments with the same cardinality. Preserve source
ordering for ties and record the assignment implementation/version. Geometry
assignment does not use identity correctness; use the same assignment for
strict and tolerant identity scoring rather than rematching for better IDs.

The part-based criterion can accept low overall coverage. Report union IoU,
visible coverage and part-only association counts alongside identity scores.

## 3. Identity correctness

For a geometry-associated prediction with a valid submitted typed ID, accept
the first qualifying reason below, counting it only once:

| Reason | Evidence |
|---|---|
| Exact ID | Same OSM type and identifier |
| Relation or containment | One entity is a qualifying building, multipolygon or site parent of the other, including evidenced nested relations or containment |
| Same building relation | Shared relation with a building tag or type=building, including appropriate outline/part members |
| Adjacent building | Both have qualifying building evidence and actual footprint geometry; minimum boundary distance is at most 100 m |

The fixed adjacency tolerance does not require matching names or operators.
Compute local distances using 111320 m per latitude degree and cosine-scaled
longitude at the mean latitude, then minimum polygon boundary distance.
Intersection/containment has distance zero. Adjacency is not transitive, and
missing geometry must not be replaced by name-based guesses.

For spatial containment, at least 95% of the child area must lie in the container,
whose area must exceed the child area by more than 5%. A shared generic campus
relation alone does not establish that two distant buildings are the same.
Unrelated boundary/route relations do not qualify. An inner ring alone is not
a building; an inner member independently tagged building/building:part can
provide building evidence. Record typed IDs, the reason, evidence and distance.

Tolerant acceptance of nearby buildings is a position tolerance, not evidence
that the identities are factually identical. Report strict-ID scores using the
same geometry association. Do not compare changed counting/association rules
as though they were unchanged historical metrics.

## 4. Decisions, ignores and abstentions

| GT decision | Geometry GT | Identity GT |
|---|---|---|
| matched | Merged instance | Merged instance |
| osm_missing | Each reviewed region, without automatic ID merging | Not identity-evaluable |
| ambiguous / out_of_scope | Explicit ignore region | Explicit ignore region |
| false_positive / duplicate_instance | Not positive GT | Not positive GT |
| Missing/unreviewed state | Reject as completed evaluation data | Same |

Predictions associated with osm_missing GT are excluded from the identity
denominator. Ignore exclusion applies only to unmatched detections with at least
50% of their union area covered by the relevant ignore union and no qualifying
association to evaluable GT at that layer. Do not remove extra predictions on
evaluable GT as ignores. Record unmatched qualifying duplicate candidates as a
diagnostic rather than proof of duplication.

All output instances, including failures, no-candidate outcomes and abstentions,
must be accounted for. Missing/duplicate images, invalid IDs, nonfinite or
zero-area boxes and unknown assignment states invalidate completed scoring.
Success-only outputs without complete coverage cannot support output-denominator
precision or F1. Partial labels do not establish that unpaired predictions are
false positives. The current candidate excludes the legacy partial-label set.

## 5. Reported metrics

Let G be identity-evaluable GT instances, D all identity-evaluable predictions,
T geometry-associated instances, C identity-correct associations, and A
predictions with a valid submitted identity. Abstentions remain in D.

| Metric | Definition |
|---|---|
| End-to-end precision / recall / F1 | C/D; C/G; 2C/(D+G) |
| Geometry detection precision / recall / F1 | Tbox/Dbox; Tbox/Gbox; 2Tbox/(Dbox+Gbox), including osm_missing geometry |
| Conditional matching accuracy | C/T |
| Strict-ID precision / recall / F1 | Replace C with exact-ID correct count |
| Accepted precision | C/A |
| Assignment coverage / abstention rate | A/D; (D-A)/D |
| Mean union IoU | Mean over all geometry-associated instances, including wrong IDs and abstentions |
| Mean visible coverage | Intersection with GT union divided by GT union area, averaged over associations |
| Part-only associations | support IoU passes but union IoU fails the same threshold |
| Image hit rate | Positive images with at least one correct identity / images with identity GT |

Also report pre/post-merge counts, ignored counts, localization misses, wrong
identities, localized abstentions, unmatched duplicate candidates and correctness
reasons. Require 0 <= C <= T <= min(D,G). For nonzero denominators,
recall = (T/G) * (C/T). Zero-denominator ratios are N/A; F1 is zero when there is
GT or a prediction and no true positive. Aggregate counts before micro metrics.
Do not average subset percentages or introduce mAP/AUROC claims from fixed outputs.

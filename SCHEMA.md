# Portable schema v1 — candidate documentation

All file paths in the manifest and metadata are relative to the package root.
`img_0001` etc. are stable IDs within this draft, assigned by sorted group and
source image ID. Region IDs are `<image_id>_r001` etc., retaining source region
order. The local private ledger maps them back to original IDs. Future versions
must retain or explicitly map these IDs; do not silently renumber revised scope.

`metadata/images.json` records `image_id`, `group_id`, `path`, width/height,
SHA256, byte size, `method_input_prior`, `intrinsics` and metadata inventory.
Longitude/latitude are degrees; heading is degrees as stored by the source run.
The prior source is recorded, with no claim of surveyed accuracy or global
calibration. Missing provenance is null/unknown, not a guessed value.
Derived camera intrinsics are retained as structured source fields. Reference
poses in `annotation_reference_poses.json` are not method inputs or pose GT.

`annotations/<group>/label_data_sam3.json` has an ordered `images` list with
`id`, `name`, root-relative `image_path`, `image_size`, `bounding_boxes` and
`osm_entities`. A box retains the source numeric geometry (`x`, `y`, `w`, `h`,
`x2`, `y2`, or `xyxy`) and polygon when present. The evaluator uses continuous
xyxy rectangles [x1,y1,x2,y2], area=(x2-x1)*(y2-y1), without inclusive +1;
coordinates refer to upright original-sized pixels, never thumbnails.
Source outlying coordinates, if any, are not silently clipped by export.
Polygons and depth annotations are auxiliary, not a new mask/depth benchmark.

`groundtruth_pairs.json` contains ordered `pairings`: image IDs, `bbox_id`,
`bbox_xyxy` and existing OSM identifiers/name/center. `osm_type` defaults to way
in the frozen evaluator when omitted. A slash-typed `osm_id` has precedence.
`way/123` and `relation/123` are different identities. No aliasing or relabeling
is introduced by this export.

`annotation_decisions.json` retains decisions and optional identity fields:
`matched` requires a pairing; `osm_missing` participates in geometry but not
identity scoring; `ambiguous`/`out_of_scope` identify ignore regions;
`false_positive`/`duplicate_instance` are not positive GT regions.
Historical decisions for already removed proposals are retained with
`geometry_present: false` and an `_inactive_r` ID; no box is reconstructed and
they do not enter GT region counts or metric denominators.
Unreviewed states cannot silently become completed GT. Abstentions and UNKNOWN
are model outputs, not permission to remove them from the prediction denominator.

`maps/` contains byte-exact source files deduplicated by SHA256: processed maps
for inference and raw-context maps for evaluation. The semantic index loads the
evaluation map first, then the exported annotation map context, as in the frozen
evaluation. These maps have distinct roles. Snapshot download dates are unknown
unless recorded; the export date must not be substituted for them.

`metadata/rights_review.csv` in the source candidate is a pending author workflow,
not consent evidence. A public summary must omit internal evidence and private
mappings. Redistribution, privacy and metadata decisions must be explicitly
resolved before data publication.

# Provenance and known unknowns

This describes the source lineage and preparation of version v1-anonymous-20261029.
Remote availability is established only by a dataset asset on the release page.

## Photographs

The contributing team captured the photographs according to the organizer's
statement of redistribution authority. Individual collectors are not named
during anonymous review. Per-image capture instructions, devices and detailed
collection conditions are not available in the release-preparation records.

There are 114 staged upright photographs in 13 processing groups. The frozen local draft
retains the source staged bytes; this version adds documented privacy processing. Internal recorded
capture comparisons match 56 staged files and differ for 58; the byte comparison
does not establish the earlier transformations. The collection must not be
described as 114 unchanged raw camera captures.

Original file/person mappings and internal rights evidence are excluded from
public materials. Source IDs remain stable within the portable candidate.

## Annotations and metadata

Existing SAM3-assisted, author-reviewed region geometry, OSM pairings and review
decisions were exported without relabelling. There are 331 active regions, 325
pairings and 244 merged identity-evaluable instances. Seven historical decisions
refer to deleted proposals and do not reconstruct missing geometry. Thirteen
partially labelled legacy photographs are excluded.

Input position/heading priors and derived intrinsics come from the recorded
method inputs. Annotation-reference poses are separated and may include
annotation adjustments. Neither constitutes independently surveyed pose ground
truth, and the intrinsics do not establish independent camera calibration.

## OpenStreetMap

Frozen map files are deduplicated by SHA256 and have separate inference and
evaluation/context roles. The map role must be retained alongside the file hash.
Actual snapshot download dates are unknown where not recorded; preparation or
export dates must not be substituted for download dates.

OSM-derived content is also present in annotation fields. Preserve attribution
and applicable ODbL obligations throughout the release; see [LICENSES.md](LICENSES.md).

## Exposure, legacy overlap and final processing

Every candidate image was available during development. No untouched test split
or independent-site count is asserted. A previous 134-photo collection lacks an
authoritative per-image inventory in the checked records; overlap is unknown.

This version applies opaque masks to 81 photographs and strips embedded
identifying metadata from all 114. JPEGs with masks are re-encoded at quality 95
with 4:4:4 sampling; masked PNGs use lossless encoding. Unmasked JPEG compressed
scans and unmasked PNG decoded pixels are preserved. Dimensions, stable IDs,
region geometry, pairings, task input priors and intrinsics are retained.
Only anonymous format identifiers in annotation headers are renamed; labels
are not changed. Per-image operations and hashes are in the processing record.
Structured task position/heading and separate annotation references remain.
Scores from older inputs have not been verified on these distributed images.

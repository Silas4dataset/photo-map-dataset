# Dataset card

## Task and candidate scope

Single-photo visible-building region to typed OSM entity correspondence, using
coarse position and heading priors. The candidate contains 114 staged upright
photographs in 13 processing groups, 331 active source regions and 325 pairings.
The protocol merges these into 244 image-specific typed-OSM identity instances.
Seven historical decisions have no active geometry. Partially labelled legacy
photographs are excluded. Counts are provisional until the release scope is fixed.

## Collection and annotation

The organizer reports that the photographs were captured by the contributing
team and that the team has authority to redistribute them. Per-image collector
assignments, device models and detailed collection instructions are not supplied
in this documentation. No ethics approval, individual consent or independently
verified written permission is inferred from that organizer statement.

Existing annotations came from a SAM3-assisted, author-reviewed workflow. This
preparation does not introduce new labels, an independent second rater or an
inter-rater agreement claim. See the schema for decisions and the protocol for
the distinction between regions, pairings and merged instances.

## Inputs and reference information

Input position/heading priors and derived intrinsics reproduce the recorded
method inputs; they are not surveyed camera poses or independent calibration.
Annotation-reference poses are kept separately and must not silently be supplied
to inference. Maps have distinct inference and evaluation/context roles.

## Exposure and limitations

All photographs were exposed during development. No group is asserted to be an
untouched test split. Groups are processing units, not independent-site counts.
The small collection and OSM coverage/quality limit generalization. Packaging
does not establish navigation benefit, tourist usability or new model evidence.

Staged files are not all unmodified raw captures. The authoritative inventory
needed to establish overlap with a previous 134-photo collection is unavailable;
no subset, expansion or increment claim is made.

## Availability, rights and maintenance

Only documentation is currently present. The intended data ZIP will contain
photographs, annotations, metadata and maps, but no executable evaluation,
predictions, weights or application. Documentation alone does not promise model
result reproduction. The intended data terms are component-specific; see
[LICENSES.md](LICENSES.md).

Final privacy review and the structured-position release decision remain pending.
No automated metadata or identity-string scan constitutes final visual clearance.
Any pixel/input changes require updated hashes, scope records and appropriate
result checks before claiming reproduction on the released files.

Author identities are withheld during review. Dataset corrections will use
explicit versions and retained checksums, without silently replacing reviewed data.

# Photo–map correspondence dataset

Documentation for a dataset being prepared for anonymous peer review.

**Status: preparation in progress. No dataset ZIP, public data release or DOI is
available yet.** Final image privacy review, location-release decisions and the
data-component licence boundaries remain to be completed. This repository is
currently a documentation workspace.

## Scope

The current candidate collection contains 114 staged upright photographs in 13
processing groups for associating visible building regions with typed
OpenStreetMap (OSM) entities using coarse position and heading priors.

| Quantity | Candidate count |
|---|---:|
| Photographs | 114 |
| Processing groups | 13 |
| Active source regions | 331 |
| Region–OSM pairings | 325 |
| Merged identity-evaluable image–OSM instances | 244 |
| Inactive historical decisions without active geometry | 7 |

These quantities use different counting units. Counts will be updated if the
released scope changes. The 13 partially labelled legacy photographs are
excluded from the candidate collection.

All photographs were exposed during development. Processing groups are not
independent-site counts, and this collection is not an untouched test set.

## Documentation

- [Dataset card](DATASET_CARD.md): task, source scope, quality and limitations.
- [Schema](SCHEMA.md): files, fields, coordinates, IDs and annotation decisions.
- [Protocol](PROTOCOL.md): merged-instance counting and scoring definitions.
- [Provenance](PROVENANCE.md): collection, preparation and known unknowns.
- [Licence notice](LICENSE.md) and [component terms](LICENSES.md).

## Planned data release

After the remaining checks, a versioned ZIP and `SHA256SUMS.txt` will be attached
to a [GitHub Release](https://github.com/Silas4dataset/photo-map-dataset/releases).
The current source payload is about 623 MB. No final archive size or release
date has been assigned.

The planned ZIP includes photographs, annotations, method input metadata,
separate annotation-reference poses, frozen maps, schema, protocol, provenance,
licence notices and a payload manifest. Executable evaluation, model predictions,
model weights and an application are not included.

GitHub's automatic **Source code (zip)** contains repository documents, not a
separately uploaded dataset ZIP. When data are available, download the dataset
asset and its matching checksum file from the same specific release, then run:

```sh
shasum -a 256 -c SHA256SUMS.txt
```

Record the exact release URL, version and archive SHA256 used in research.

## Reuse and privacy

Repository documentation is licensed under CC BY-NC 4.0, excluding identified
third-party material. The intended terms for the photographs and independently
created author-owned data contributions are also CC BY-NC 4.0; the final data
scope and notices must be completed before data publication. Commercial use is
not granted by those terms. OSM-derived components retain applicable ODbL terms
without an added noncommercial restriction on OSM rights. See [LICENSES.md](LICENSES.md).

Withholding author identities does not anonymize people in photographs or remove
location information. The final image and structured-location release decisions
are still pending. Reference poses are for annotation only, not independently
surveyed camera-pose ground truth or inference inputs. Intrinsics are derived
values rather than independently measured camera calibration.

## Citation and contact

Author identities are withheld during double-blind review and will be restored
when the review process permits disclosure. For the documentation, credit
**Photo–map dataset contributors** and link to this repository. Once a dataset
release exists, cite its exact version rather than the moving main branch.

Questions about this preparation can be raised through
[repository Issues](https://github.com/Silas4dataset/photo-map-dataset/issues).
No personal contact details are published here.

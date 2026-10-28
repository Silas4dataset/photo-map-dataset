# Photo–map correspondence dataset

Version: **v1-anonymous-20261029**. Prepared for double-blind peer review; contributor
identities will be restored when the review process permits disclosure.

114 upright photographs in 13 processing groups support correspondence between
visible building regions and typed OpenStreetMap (OSM) entities, using coarse
position and heading priors. All photographs were exposed during development;
this is not an untouched test set. Groups are not independent-site counts.

| Quantity | Count |
|---|---:|
| Photographs | 114 |
| Processing groups | 13 |
| Active source regions | 331 |
| Region–OSM pairings | 325 |
| Merged image-specific typed-OSM identity instances | 244 |
| Inactive historical decisions without geometry | 7 |

These counts have different units. Thirteen partially labelled legacy
photographs are excluded. No new labels were introduced for this release.

## Obtaining and checking the data

The distribution location is [GitHub Releases](https://github.com/Silas4dataset/photo-map-dataset/releases).
The dataset ZIP is a separately attached asset; GitHub's automatic **Source code
(zip)** contains repository files and does not include the dataset asset.
If the dataset asset is absent, no data deposit has been completed at that URL.
No DOI is assigned.

Download the dataset asset and its matching `SHA256SUMS.txt` from the same
specific release. Before extracting it, run:

```sh
shasum -a 256 -c SHA256SUMS.txt
```

The ZIP contains a `data_only/` directory. After extraction, verify every file
against its manifest using [VERIFY.md](VERIFY.md). Record the release URL,
version and archive SHA256 used in research.

## Contents and use

- `images/`: privacy-processed photographs at the original upright dimensions.
- `annotations/<group>/`: reviewed geometry, OSM pairings and annotation decisions.
- `metadata/images.json`: stable IDs, relative paths, dimensions, hashes, actual
  recorded method priors, derived intrinsics and image-processing records.
- `metadata/annotation_reference_poses.json`: annotation references, separated
  from inference inputs; these are not independently surveyed pose ground truth.
- `metadata/privacy_processing.json`: public mask coordinates, categories and
  output hashes. Original photographs and private review crops are excluded.
- `metadata/rights_review.csv`: anonymous summary of organizer-declared rights
  and the processing performed; private evidence and collector mappings are excluded.
- `maps/`: frozen, hash-deduplicated OSM maps with roles recorded in the manifest.
- [Schema](SCHEMA.md), [protocol](PROTOCOL.md), [dataset card](DATASET_CARD.md),
  [provenance](PROVENANCE.md), [privacy](PRIVACY.md), [licences](LICENSES.md)
  and `manifest.json`.

Executable evaluation, model predictions, model weights and an application are
not included. Inspection and reuse follow the JSON schema. Distributed image
pixels differ from earlier experiment inputs: no unchanged model-score
reproduction is claimed without running the method again on this version.

## Reuse, attribution and contact

Photographs and independently authored documentation are **CC BY-NC 4.0**:
noncommercial sharing/adaptation requires attribution, a licence link and an
indication of changes. Commercial use is outside that grant. OSM and the mixed
OSM annotation databases retain **ODbL 1.0** obligations without added NC
conditions on those rights. See the exact file/field scope in [LICENSES.md](LICENSES.md).
The NC photo component means this is not an unrestricted open-data licence.

Credit **Photo–map dataset contributors**, this repository and the exact version.
OSM attribution: **© OpenStreetMap contributors**. A formal named-author citation
will follow after review; no named-author or DOI record is fabricated now.
Questions and corrections: [repository Issues](https://github.com/Silas4dataset/photo-map-dataset/issues).
For privacy reports, provide the image ID and approximate region without
reposting personal identifiers; request removal or a corrected version.

Structured positions/headings and visible geography are intentionally retained.
Withholding contributor identities does not guarantee geographic or author anonymity.

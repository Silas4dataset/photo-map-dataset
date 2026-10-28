# Component and field licence scope

There is no single NC licence over the entire collection. Separate photograph
files carry CC BY-NC 4.0. Maps and mixed OSM annotation databases retain applicable
ODbL obligations. NC conditions must not be applied to the OSM/database rights
granted under ODbL. In particular, an NC label on a photograph does not prohibit
commercial reuse of independently obtained OSM data.

| Component or fields | Origin and applicable scope |
|---|---|
| `images/**` | Team-created photographs, including privacy edits: CC BY-NC 4.0 to the extent of held rights. Incidental signs/artwork and other third-party rights are not transferred. |
| Independently authored `*.md`, privacy mask descriptions/coordinates in `metadata/privacy_processing.json`, anonymous rights summary | CC BY-NC 4.0 to the extent of held rights; third-party licence notices excluded. |
| `maps/*.json`, all map geometry, tags, IDs, names, centres, heights and derived map attributes | OSM-derived data: applicable ODbL 1.0 obligations and OSM attribution. No added NC restriction. |
| `label_data_sam3.json` → `images[].osm_entities[]` including `osm_id`, `osm_type`, `name`, `name_zh`, `center`, `polygon`, `polygon_holes`, `tags`, height fields | Copied/processed OSM context under applicable ODbL/OSM terms, including derived centres and attributes. |
| `groundtruth_pairs.json` → `pairings[].osm_*`; `annotation_decisions.json` → `decisions[].osm_*` | OSM identifiers/context and linked data retain applicable ODbL/OSM terms. |
| `annotations/**/*.json` as linked databases, including region/pair/decision organization | Mixed photo-region and OSM-linked database distributed under ODbL 1.0 for contributors' database rights and applicable derivative-database obligations. No additional NC condition is asserted over these database rights. |
| Region geometry (`bounding_boxes`, `bbox_xyxy`, polygons), stable IDs, statuses/confidence and model-assisted auxiliary values | Independently prepared annotation contributions within the mixed database. Contributors grant the rights they hold in those structured contributions as needed for the ODbL database distribution; no separate NC restriction is imposed on reuse of the structured annotation database. This does not grant use of the separate photos. |
| `metadata/images.json`, `annotation_reference_poses.json`, manifest technical index | Recorded factual/derived task values and database index. Applicable ODbL database obligations remain; no exclusive copyright claim in bare facts is made. The referenced photos retain their own NC licence. |
| Evaluation code, model predictions/weights, application | Not included. No rights to them are granted by this data package. |

For maps, retain source attribution and licence links when sharing. Public use
or distribution of an adapted database may require share-alike and provision of
the adapted database or an alteration file under ODbL. See the actual terms.
The databases are supplied in accessible JSON form. Snapshot download dates
are unknown where unrecorded; preparation dates are not download dates.

**© OpenStreetMap contributors** — https://www.openstreetmap.org/copyright

- CC BY-NC 4.0: https://creativecommons.org/licenses/by-nc/4.0/
- CC legal code: https://creativecommons.org/licenses/by-nc/4.0/legalcode.en
- ODbL 1.0: https://opendatacommons.org/licenses/odbl/1-0/
- ODbL legal text: https://opendatacommons.org/licenses/odbl/1-0/index.html

Attribution for contributor-owned components: **Photo–map dataset contributors**,
repository URL and exact version, plus an indication of changes. Contributor
names are withheld during double-blind review and will be restored afterward.
Noncommercial status depends on the purpose of use, not simply university or
company affiliation. Exceptions/limitations and third-party rights remain.

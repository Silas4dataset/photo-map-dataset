# Image privacy processing

This version retains structured latitude, longitude, heading, derived intrinsics
and separately stored annotation-reference poses because they are part of the
documented task. Visible buildings, public signs and geography remain. Do not
describe these photographs as geographically anonymous.

All 114 source overviews were manually inspected at up to 1200 × 1600 display
pixels, with selected enlarged detail crops. All processed images were reviewed
in contact sheets and selected processed details were inspected. The identified
faces/heads, vehicle plates, parcel labels and conservative possible identifiers
were covered by opaque neutral grey rectangles, with margins. Crowded scenes
use bands and parcel surfaces sometimes use larger rectangles. This may cover
nonprivate image content. The mask record currently contains 321 rectangles in
81 images; 33 images had no selected pixel redaction.

This was not exhaustive full-resolution tiling, an independent human privacy
audit or a guarantee that every small, reflected or occluded identifier was found.
No claim of individual subject consent or ethics approval is inferred. Reports
of missed identifiers should name the image ID and approximate region in
repository Issues without reproducing the identifier. Corrections require a
new explicit version and checksum, or removal of the affected asset.

The frozen local original is unchanged and is not included. Public processing
records contain stable image IDs, rectangle coordinates/categories and output
hashes; private review crops, original filenames/person mappings and rights
evidence are excluded. These masks are privacy records, not task ground truth.

## Encoding and metadata

Image dimensions, orientation, IDs, annotation geometry and task input values
are retained. Masked JPEGs are re-encoded with Pillow quality=95 and subsampling=0
(4:4:4); compression also changes pixels outside rectangles. Masked PNGs use
lossless encoding after applying the rectangles. Unmasked JPEGs have metadata
segments removed without re-encoding compressed scans. Unmasked PNGs retain
decoded pixels while metadata are removed. Colour ICC profiles, where present,
are retained; embedded EXIF/XMP/comments/text and identity metadata are removed.

All output dimensions, hashes, metadata and mask centre pixels were checked;
decoded pixel equality was checked for unmasked images. The processing record
identifies the operation for each image. No crops/resizes/rotations are applied
to the distributed image frame. Staged sources were already normalized in some
cases and must not all be called unchanged raw camera captures.

Masking and JPEG re-encoding change model inputs. Earlier model results were
not rerun on this version, and exact score reproduction is not promised. Retain
the version and checksum when reporting any new results.

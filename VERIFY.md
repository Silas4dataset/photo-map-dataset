# Verify downloaded files

First check the downloaded archive against `SHA256SUMS.txt` from the same release:

```sh
shasum -a 256 -c SHA256SUMS.txt
```

After extraction, change into `data_only/` and run this Python 3 command. It checks
file bytes, SHA256 values and unexpected files against `manifest.json`:

```sh
python3 - <<'PY'
from pathlib import Path
import hashlib, json
root = Path('.').resolve()
m = json.loads((root/'manifest.json').read_text())
for name, entry in m['files'].items():
    p = (root/name).resolve()
    assert p.is_relative_to(root) and p.is_file(), name
    assert p.stat().st_size == entry['bytes'], name
    with p.open('rb') as f:
        h = hashlib.sha256()
        for chunk in iter(lambda: f.read(1048576), b''):
            h.update(chunk)
    assert h.hexdigest() == entry['sha256'], name
actual = {p.relative_to(root).as_posix() for p in root.rglob('*') if p.is_file()}
assert actual == set(m['files']) | {'manifest.json'}, 'Unexpected or missing file'
print('Verified', len(m['files']), 'payload files')
PY
```

The manifest omits its own digest to avoid a circular hash. Its bytes are
protected by the external archive checksum. Integrity checks do not establish
privacy clearance, annotation correctness or model-result reproducibility.

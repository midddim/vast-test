# VAST Samples for QA and Integration Testing

This repository contains a set of static VAST XML files that can be used for:

- Manual QA of VAST URL input fields
- Integration testing with ad servers / bidders
- Player behavior testing (different durations, formats, bitrates)
- Error handling and edge-case validation

All files are designed to be served as static assets (e.g. via GitHub Pages) and referenced directly as VAST URLs.

---

## Files Overview

| File name                    | Type           | Description                                                  |
|-----------------------------|----------------|--------------------------------------------------------------|
| `vast-ok-30s.xml`           | Inline, valid  | Simple 30s MP4 video, single media file                      |
| `vast-ok-15s.xml`           | Inline, valid  | Simple 15s MP4 video, single media file                      |
| `vast-multi-mediafiles.xml` | Inline, valid  | Multiple media files with different MIME types and bitrates  |
| `vast-broken.xml`           | Invalid XML    | Intentionally broken XML structure                           |
| `vast-wrapper.xml`          | Wrapper, valid | VAST wrapper pointing to another VAST tag                    |
| `vast-no-mediafiles.xml`    | Inline, bad    | No `<MediaFiles>` section inside `<Linear>`                  |
| `vast-no-duration.xml`      | Inline, bad    | `<Duration>` is missing                                      |
| `vast-http-mediafile.xml`   | Inline, mixed  | Media file served over HTTP instead of HTTPS                 |

You can use these VAST tags to verify:

- Basic happy-path behavior (`vast-ok-*.xml`)
- Handling of multiple formats and bitrates
- How the system reacts to malformed VAST or missing fields
- How the system treats non-HTTPS media URLs
- Wrapper VAST handling (if supported by your stack)

---

## Usage with GitHub Pages

1. Create a public GitHub repository, for example: `vast-samples`.
2. Place all `.xml` files in the repository root.
3. Go to **Settings → Pages**:
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/ (root)`
4. After the deployment completes, your files will be available at:

```text
https://<your-username>.github.io/vast-samples/vast-ok-30s.xml
https://<your-username>.github.io/vast-samples/vast-ok-15s.xml
https://<your-username>.github.io/vast-samples/vast-multi-mediafiles.xml
https://<your-username>.github.io/vast-samples/vast-broken.xml
https://<your-username>.github.io/vast-samples/vast-wrapper.xml
https://<your-username>.github.io/vast-samples/vast-no-mediafiles.xml
https://<your-username>.github.io/vast-samples/vast-no-duration.xml
https://<your-username>.github.io/vast-samples/vast-http-mediafile.xml
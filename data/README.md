# RefAmb-1500: data-only reproducibility release

This directory is a **data-only, copyright-respecting release manifest** for
the 1,500-example RefAmb evaluation set. It lets reviewers obtain the exact
underlying records from their official providers without us redistributing
their protected content.

## What this release fixes

`refamb_1500_manifest.jsonl` is the frozen membership list for all **1,500**
RefAmb examples:

| Upstream source | Examples |
|---|---:|
| CRAG-MM | 818 |
| InfoSeek | 176 |
| MC-Search | 300 |
| OVEN | 206 |
| **Total** | **1,500** |

Every manifest row includes the RefAmb ID, source benchmark, official source
record ID, image ID when applicable, source split, task type, and SHA-256
fingerprints of the question, evaluated answer, and canonical RefAmb record.
The fingerprints make it possible to confirm that a locally obtained record is
the intended one without publishing the question text, answer text, images, or
retrieval corpus in this repository.

## How to obtain the 1,500 examples

1. Download each of the four upstream resources only from the official routes
   listed in `UPSTREAM_SOURCES.md` and accept the respective terms.
2. For each row in `refamb_1500_manifest.jsonl`, select the upstream example
   matching `source_dataset`, `source_split`, and `source_record_id`; retrieve
   its image through `source_image_id` where applicable.
3. Use the supplied task metadata and fingerprints to verify that the selected
   upstream records match the frozen RefAmb membership list.

The manifest itself is sufficient to identify all 1,500 records. The
canonical task text, answers, images, web documents, and MC-Search knowledge
base are intentionally not included: they remain subject to the licenses and
terms of their respective upstream providers.

## Included files

- `refamb_1500_manifest.jsonl` — the 1,500-record data manifest.
- `SHA256SUMS` — integrity hash for the manifest.
- `UPSTREAM_SOURCES.md` — official retrieval routes, licensing, and attribution
  requirements.

From the repository root, verify the manifest with:

```bash
sha256sum -c data/SHA256SUMS
```

There is deliberately **no source code** in this release.

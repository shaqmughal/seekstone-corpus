# seekstone-corpus

Pinned source text for the benchmark vaults in [Seekstone](https://github.com/shaqmughal/seekstone), an Obsidian MCP server. The repository holds no code. The files are attached to releases.

## What's here

| Release | Contents |
|---|---|
| [`eb1911-v1`](https://github.com/shaqmughal/seekstone-corpus/releases/tag/eb1911-v1) | 125 volumes of the *Encyclopædia Britannica*, 11th edition (1911), as plain text from Project Gutenberg (`pg<id>.txt`) |

Seekstone's harness generates its committed benchmark vaults (10,000, 1,000 and 5,000 notes) from these volumes.

## Why this mirror exists

Seekstone pins each volume by SHA-256 in [`packages/harness/fixtures/corpus/manifest.json`](https://github.com/shaqmughal/seekstone/blob/main/packages/harness/fixtures/corpus/manifest.json). Project Gutenberg has since re-issued some of those files, so a download from Gutenberg no longer matches every pin. This repository keeps the exact files that were pinned, so anyone can regenerate the vaults byte for byte.

## How it's used

You don't normally download anything from here by hand. In a Seekstone checkout, run:

```bash
npm run harness -- fetch-corpus
```

`fetch-corpus` tries Project Gutenberg first and falls back to this mirror for any volume that doesn't match its pin. Every file is checked against the checksum in `manifest.json`, whichever source it came from.

## Rules

- `manifest.json` in Seekstone is the source of truth. This repository has no copy of the checksums, so there is nothing here to keep in sync.
- Releases are immutable: once published, a release's files and tag can't be changed or deleted.
- A new corpus version goes out as a new release (`eb1911-v2`, and so on). Seekstone's CI checks that the release named in `manifest.json` exists, is immutable, and matches every pin.

Seekstone's [`PROVENANCE.md`](https://github.com/shaqmughal/seekstone/blob/main/packages/harness/fixtures/corpus/PROVENANCE.md) documents how a new version is published.

## License

The 1911 *Encyclopædia Britannica* is in the public domain in the United States. Each file is distributed unmodified, with Project Gutenberg's header and license text intact. Seekstone strips that text at parse time, so only the article text enters the vaults.

## Issues

Issues are turned off here. Report problems on [Seekstone's issue tracker](https://github.com/shaqmughal/seekstone/issues).

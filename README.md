# CG Production Data Assistant

This is a parent repository containing two submodules for constructing an LLM assistant for answering questions on a database of Blender Studio's assets from their short films.

Try out the chatbot here: https://huggingface.co/spaces/cameron-d/cg-production-assistant

## Submodules

- **CG_Production_LLM_Assistant** - LLM-powered assistant
- **CG_Production_Metadata_Extractor** - Asset downloading, metadata extraction, and embedding tools

## Getting started

Run `git submodule update --init --recursive` after cloning to populate the pinned component revisions. See each component's README and `AGENTS.md` for development commands.

The downloader is now ordinary source code in [CG_Production_Metadata_Extractor/asset_downloader](CG_Production_Metadata_Extractor/asset_downloader/README.md). Downloading and extraction remain separate commands. From the extractor repository root:

```powershell
python -m pip install -r asset_downloader/requirements.txt
python asset_downloader/download_assets.py <gallery-url> --dir cg-production-data/shows/<project>
```

Configure `USER_COOKIE` in the extractor-root `.env` without overwriting existing settings, and point scanner `DATA_PATH` at the downloaded assets. See the downloader guide for details and snapshot provenance.

## Existing checkouts

The old downloader repository remains available for historical reference. Before retiring an existing `CG_Production_Asset_Downloader/` checkout, preserve its uncommitted files, `.env`, downloaded assets, and Git metadata. The legacy path is ignored so an existing checkout can remain intact as a local recovery copy; it is no longer an active submodule. Alternatively, keep a recovery copy under ignored `.local-backups/`. Neither is part of fresh clones. Copy needed assets/configuration into the extractor deliberately, without overwriting existing data. Do not delete the old checkout until its local files are accounted for.



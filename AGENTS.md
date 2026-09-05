# Repository Guidelines

## Project Structure & Module Organization

This parent repository coordinates two Git submodules for downloading Blender Studio assets, extracting metadata, and querying it through an LLM assistant:

- `CG_Production_Metadata_Extractor/`: scanner/database code in `src/`, handlers in `src/extractors/`, embeddings in `src/embedders/`, tests in `testing/`, and downloader/unzip tools in `asset_downloader/`.
- `CG_Production_LLM_Assistant/`: Lambda entry point and services in `backend/`, Gradio application in `frontend_gradio/`, and Blender add-on in `frontend_blender/`.

Component READMEs and `docs/` directories describe configuration and deployment. Downloaded assets and generated thumbnails are runtime data, not source code.

The retired downloader checkout may remain at ignored `CG_Production_Asset_Downloader/` or under `.local-backups/`; do not treat recovery copies as active source or delete their local data.

## Build, Test, and Development Commands

Run `git submodule update --init --recursive` from the repository root to populate the pinned component revisions. There is no root-level build or test runner.

Run these commands from the indicated component directory:

- Any directory containing `requirements.txt`: `python -m pip install -r requirements.txt` installs its dependencies; use an isolated virtual environment.
- `CG_Production_Metadata_Extractor/`: `docker compose build` builds the extractor; `docker compose up` starts the configured scanner and services.
- `CG_Production_Metadata_Extractor/`: `python -m unittest discover -s testing -p test_gap_splitting.py` runs sequence-gap regression tests.
- `CG_Production_LLM_Assistant/backend/`: `python testing/test_local.py` checks database connectivity and backend integrations.
- `CG_Production_LLM_Assistant/frontend_gradio/`: `python app.py` launches the web interface.

## Coding Style & Naming Conventions

Follow surrounding Python code: four-space indentation, `snake_case` functions and modules, `PascalCase` classes, and uppercase constants. Preserve existing type hints and document non-obvious behavior. No shared formatter or linter configuration is checked in.

## Testing Guidelines

Existing tests combine `unittest` and standalone Python diagnostic scripts. Name tests `test_*.py` and place them in the affected component's testing directory. Add regression checks for behavioral fixes. No enforced coverage threshold is defined. Integration checks require configured database/AWS access; report prerequisites and any skipped checks.

## Commit & Pull Request Guidelines

History uses short descriptive subjects, such as `Security updates to submodules`; no strict prefix convention is established. Commit component changes in their own repositories, then commit updated submodule references here. Ensure referenced commits are available remotely.

PRs should describe affected components, behavior changes, validation performed, and relevant issues. Include screenshots for interface changes.

## Security & Configuration

Use component `.env.example` files where available. Never commit `.env` files, AWS credentials, database passwords, or Blender Studio cookies. Keep downloaded assets, databases, and model caches out of commits.

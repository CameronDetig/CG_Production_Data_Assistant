# CG Production Data Assistant

This repository serves as a parent repository containing three related CG production tools as Git submodules.

## Submodules

- **CG_Production_Asset_Downloader** - Tool for downloading CG production assets
- **CG_Production_LLM_Assistant** - LLM-powered assistant for CG production workflows
- **CG_Production_Metadata_Extractor** - Metadata extraction tool for CG production files

## Working with Submodules

### Cloning this repository

To clone this repository with all submodules:

```bash
git clone --recursive https://github.com/CameronDetig/[REPO_NAME].git
```

Or if you've already cloned it:

```bash
git submodule update --init --recursive
```

### Making changes to a submodule

Each submodule is its own independent Git repository. To make changes:

1. Navigate into the submodule directory
2. Make your changes and commit them
3. Push to the submodule's remote repository

```bash
cd CG_Production_Asset_Downloader
# Make changes
git add .
git commit -m "Your commit message"
git push origin main
```

### Updating the parent repository

After pushing changes to a submodule, update the parent repository to track the new commit:

```bash
cd ..  # Back to parent repo
git add CG_Production_Asset_Downloader
git commit -m "Update Asset Downloader submodule"
git push origin main
```

### Pulling latest changes from all submodules

```bash
git submodule update --remote --merge
```

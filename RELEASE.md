# Release Procedure

This project uses an automated release pipeline via GitHub Actions.

## How to trigger a release

1.  **Commit and push** all your changes to the `main` branch.
2.  **Create a new tag** using the correct versioning standard (e.g., `v1.1.0.0`). 
    ```bash
    git tag v1.1.0.0
    ```
3.  **Push the tag** to GitHub.
    ```bash
    git push origin v1.1.0.0
    ```

## What the automation does

Once the tag is pushed, the GitHub Action (`.github/workflows/release.yml`) will:

1.  **Build** the plugin DLL with the correct version.
2.  **Package** the DLL into a ZIP file.
3.  **Calculate** the MD5 checksum.
4.  **Update `manifest.json`** with the new version, checksum, and download URL.
5.  **Commit** the updated `manifest.json` back to the `main` branch.
6.  **Create a GitHub Release** and upload the ZIP asset.

## Requirements

- The repository must have **Actions** enabled.
- The **Workflow permissions** must be set to **Read and write permissions** (Settings > Actions > General) so the action can commit the updated manifest.

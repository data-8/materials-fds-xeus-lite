# materials-fds-xeus-lite

[![lite-badge](https://jupyterlite.rtfd.io/en/latest/_static/badge.svg)](https://data-8.github.io/materials-fds-xeus-lite/)

Browser-based Data 8-style environment powered by JupyterLite + Xeus Python.

## What is included

- Full public course materials from [`data-8/materials-fds`](https://github.com/data-8/materials-fds)
- Labs: `lab/`
- Homework: `hw/`
- Projects: `project/`
- Lecture notebooks: `lectures/`
- Local filesystem access via `jupyterlab-filesystem-access` (sidebar folder icon; Chromium-based browsers only)

## Where to start

- Open the deployed site and use the homepage calendar to jump into notebooks.
- In Lab, use the file browser to navigate under `lab/`, `hw/`, `project/`, and `lectures/`.
- For a quick local test notebook, open `demo.ipynb` at the root.

## Run locally

From the repo root:

```bash
jupyter lite build --contents content --output-dir dist
cp landing/index.html dist/index.html
cp landing/data8logo.png dist/data8logo.png
jupyter lite serve --output-dir dist --port 8000
```

Then visit `http://127.0.0.1:8000/`.

## Frontend extensions

Frontend (JupyterLab) extensions are declared in `.github/build-environment.yml`, the conda
environment CI builds the site from. `jupyter lite build` vendors every prebuilt extension it finds
in that environment's `{sys.prefix}/share/jupyter/labextensions` into `dist/extensions/`, so adding
one is a one-line change to that file — no `jupyter-lite.json` and no code required.

Currently included:

- [`jupyterlab-filesystem-access`](https://github.com/jupyterlab-contrib/jupyterlab-filesystem-access)
  — mounts a folder from the user's real hard drive into the Lab file browser using the browser
  File System Access API, so students can open and save notebooks and data files directly instead of
  uploading/downloading. Frontend-only, so it does not affect `environment.yml` (the xeus kernel
  environment). **Chromium-based browsers only** (Chrome, Edge, Brave): on Firefox and Safari the
  sidebar tab still appears but logs `The File System Access API is not supported in this browser.`
  and does nothing.

When building locally, use a clean environment created from `.github/build-environment.yml` rather
than a general-purpose Jupyter environment — otherwise every unrelated labextension installed there
is copied into `dist/` too, and the local site will not match what CI deploys.

## Upstream references

- Source materials: [github.com/data-8/materials-fds](https://github.com/data-8/materials-fds)
- Textbook: [inferentialthinking.com](https://www.inferentialthinking.com/)

## Notes on READMEs

- Root `README.md` (this file) is repo-focused.
- `content/README.md` is student-facing and is what opens inside JupyterLite.

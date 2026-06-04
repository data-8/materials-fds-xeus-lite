# materials-fds-xeus-lite

[![lite-badge](https://jupyterlite.rtfd.io/en/latest/_static/badge.svg)](https://data-8.github.io/materials-fds-xeus-lite/)

Browser-based Data 8-style environment powered by JupyterLite + Xeus Python.

## What is included

- Full public course materials from [`data-8/materials-fds`](https://github.com/data-8/materials-fds)
- Labs: `lab/`
- Homework: `hw/`
- Projects: `project/`
- Lecture notebooks: `lectures/`

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

## Upstream references

- Source materials: [github.com/data-8/materials-fds](https://github.com/data-8/materials-fds)
- Textbook: [inferentialthinking.com](https://www.inferentialthinking.com/)

## Notes on READMEs

- Root `README.md` (this file) is repo-focused.
- `content/README.md` is student-facing and is what opens inside JupyterLite.

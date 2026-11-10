# Science of Rules website

Source code and assets for reproducing the **Science of Rules** website: an ongoing research collaboration with roots in NSF-supported work and the 2026 SNU Grand Quest project *Toward a Science of Rules: Can AI Change the Dynamics of Their Evolution?*

All page content, templates, styles, scripts, portraits, and available research figures required to build the website are included in this repository. The build uses **Python 3.9+ and its standard library**; no additional packages or research datasets are required. Unverified dates or unavailable material are explicitly marked TODO.

## Dashboard

The dashboard is a single HTML file in the `review/` directory of this repository:

```text
Science_of_Rules/                          (repository root)
└── review/
    └── science-of-rules-dashboard.html    (dashboard)
```

Open [`review/science-of-rules-dashboard.html`](review/science-of-rules-dashboard.html) on GitHub and use **Download raw file**, or clone the repository, then open the file in a web browser. It contains the website's six sections, and its images, styles, and scripts are embedded, so viewing it needs no build, server, or internet connection.

## Reproduce the website

```bash
git clone https://github.com/Dawoon-Jeong0523/Science_of_Rules.git
cd Science_of_Rules
python3 scripts/build.py
python3 scripts/validate.py
python3 scripts/serve.py --port 8765
```

Open <http://127.0.0.1:8765> on the computer running the server, or open `dist/index.html` directly.

The six main sections are **Home, Project, Research, People, News, and Data**. Research includes seven publications with figures, summaries, and source links; People presents one shared researcher roster; News lists dated announcements and publications in reverse chronological order. Existing `updates.html` and `outputs.html` URLs also open News, so the build produces eight HTML files. `dist/` is the complete static website.

The private repository requires GitHub access. On Windows, use `py` in place of `python3` if that is your Python launcher.

## Source files

| Path | Contents |
|---|---|
| `content/` | Project, research, unified roster, news events, publications, data catalog, and source metadata |
| `assets/` | CSS, JavaScript, icons, portraits, and original research figures |
| `templates/` | Shared page template |
| `scripts/` | Build, validation, preview, and export tools |
| `ASSET_SOURCES.json` | Image sources, credits, and provenance |
| `docs/MAINTENANCE.md` | Content editing and maintenance instructions |

Edit these source files, then rebuild and validate. Generated `dist/` and `review/` files are recreated from the tracked sources and excluded from Git, except the dashboard `review/science-of-rules-dashboard.html` (see [Dashboard](#dashboard)).

## Create a portable copy

After building, run:

```bash
python3 scripts/package_review.py
```

This writes a ZIP of the website to `review/science-of-rules-local-preview.zip` (not tracked) and the dashboard to `review/science-of-rules-dashboard.html` (tracked; see [Dashboard](#dashboard)). Rerun this step and commit the refreshed dashboard together with any source change so that it matches the sources.

Optional browser checks use `python3 scripts/browser_check.py` and additionally require Playwright and Chromium. The collaboration form prepares an email draft for the visitor to review and send. Hosting and automatic deployment are not configured.

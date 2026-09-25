# TopoS reliability round (09_25) — Streamlit app

Same annotation app as June, with one change: `ANNOTATOR_ID` is read from
Streamlit secrets instead of being hardcoded per branch. One copy of the code
serves all four annotators.

## Drive layout (already set up)
```
TopoS/annotations_09_25/          <- TOPOS_FOLDER_ID
  patch_assignments.csv           220 patches x 4 annotators x 4 features
  annotations/                    app writes annotator_00X_<feature>.csv here
TopoS/patches/                    <- PATCHES_FOLDER_ID (unchanged)
```

## Deploy (4 apps)
1. Push this folder to the repo (e.g. `reliability_09_25/` on `main`, or its own branch).
2. Streamlit Cloud -> New app -> repo `vivianyz/topos-annotation`
   -> branch as pushed -> Main file path `reliability_09_25/app.py`
   -> App URL e.g. `topos-annotation-002-r2`.
3. Settings -> Secrets: paste `secrets_template.toml`, set `ANNOTATOR_ID`.
4. Repeat for 004, 006, 007. Reboot each app once after saving secrets.

## After annotation
Download `annotations_09_25/annotations/*.csv` to
`Topos_claude/reliability_09_25/results/` and run `python kappa.py`.

# Repertizer data

Repertory and materia medica data used by the Repertizer web app and Android app.

## Layout (phase 1)

```
packs/            JSON data packs (exactly what the apps read today)
  kents/          Kent repertory   (meta.json + rubrics-N.json)
  synthesis/      Synthesis        (meta.json + rubrics-N.json)
  murphy/         Murphy           (meta.json + rubrics-N.json)
  boenn/          Boenninghausen   (meta.json + rubrics-N.json)
  hering/         Hering           (meta.json + rubrics-N.json)
  phatak/         Phatak           (meta.json + rubrics-N.json)
  boericke/       Boericke         (meta.json + rubrics-N.json)
  mm/             Materia medica   (rubrics.json)
  nash/           Nash             (data.json)
  counts.json     row counts per book
manifest.json     file list with byte size and SHA-256 for each pack
```

## Compressed copies (phase 2)

Every `packs/**/*.json` also has a gzip copy `*.json.gz`. The phone app and web app read the
`.json.gz` files (about 4-5 times smaller to download) and decompress them on the device.
The plain `.json` files stay for older app versions. `manifest.json` lists both, with SHA-256 of each file.

## Notes

- Files are public. Read them with the raw URL, e.g.
  `https://raw.githubusercontent.com/rrakib150/repertizer-data/main/packs/counts.json`
- Phase 2 (planned): table-form sources (CSV) per book, plus a build script that
  regenerates `packs/` from them. Until then, edit the packs directly and update `manifest.json`.

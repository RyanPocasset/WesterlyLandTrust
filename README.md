# WLT Historic Landscape Map (public version)

Interactive map of Westerly Land Trust properties: historic warm-season grassland, continuous forest since 1939, historic and current conifers, significant boulders, boulder fields and bedrock ledges. Base map is town-wide leaf-off (March 2026) and leaf-on (July 2022) imagery. The 1939, 1951–52 and 1962 aerials and 2022 LiDAR relief are clipped to each property.

**This public build leaves out stone-pile candidates, pile groups and rockshelter settings**, along with their counts. Everything else matches the full map.

## Contents

| Path | What it holds | Files |
|---|---|---|
| `index.html` | The map page (Leaflet 1.9.4, bundled) | 1 |
| `data.js` | All map layers and per-property numbers | 1 |
| `lib/` | Leaflet JS, CSS and license | 3 |
| `base/` | Town-wide leaf-on / leaf-off base map | 30 |
| `hist/` | 1939, 1951–52, 1962 aerials per property | 78 |
| `lidar/` | 2022 LiDAR relief per property | 26 |
| `detail/` | Sharper leaf-on / leaf-off imagery around each property | 52 |
| `.nojekyll` | Tells GitHub Pages to serve files as-is | 1 |

About 38 MB in total. Everything loads by relative path. Nothing calls outside services except Google Fonts, and the page falls back to system fonts without them.

## Put it on GitHub Pages

**With git or GitHub Desktop (simplest):**

1. Copy the `wlt-historic-landscape` folder into a repo, either as a subfolder of an existing Pages repo or as the root of a new one.
2. Commit and push.
3. If Pages isn't on yet: Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)`.
4. Open `https://<user>.github.io/<repo>/wlt-historic-landscape/` (subfolder) or `https://<user>.github.io/<repo>/` (root). The first deploy can take a few minutes.

**In the browser:** GitHub's uploader accepts at most 100 files per commit, so upload in three commits. Drag the folders in so their names are kept.

1. `index.html`, `data.js`, `README.md`, `lib/`, `base/` (36 files)
2. `hist/` (78 files)
3. `lidar/` and `detail/` (78 files)

`.nojekyll` only matters if this folder is the root of the Pages site. It's a hidden file, so show hidden files to drag it in, or create an empty file with that name on GitHub.

## Embed in ArcGIS StoryMaps

1. Add a block → **Embed** → paste the page URL → choose the interactive **Embed** display, not Card.
2. 650–800 px tall works well. In narrow frames the side panel starts closed, and readers open it with **Layers & info**.
3. In sidecars and guided slides, embed the same page several times with different URL parameters so each slide opens on its own view.

## URL parameters

| Parameter | Values | Effect |
|---|---|---|
| `property` | Property name or part of one, any case | Zooms to it and shows its numbers |
| `base` | `leafoff`, `leafon`, `none` | Town-wide base map |
| `hist` | `1939`, `1951`, `1962`, `lidar`, `none` | Imagery shown on the properties |
| `layers` | Comma list of layer keys | Only these layers start on |
| `panel` | `0` closed, `1` open | Side panel state |

Layer keys: `grass` (historic warm-season grassland), `grass2` (other 1939 open land), `intact` (forest since 1939), `hcon` (conifers in historic imagery), `cnow` (conifers today), `succ` (forest history), `cov` (1939 cover), `boulders` (significant boulders), `bfields` (boulder fields), `ledges` (bedrock ledges), `roads` (roads and town line).

Examples, appended to your page URL:

- `?property=Glacier&hist=1939&layers=grass,roads&panel=0` shows 1939 open moraine and grassland sites at Glacier Park.
- `?property=Crandall&hist=1962&layers=hcon,cnow,roads&panel=0` shows conifers at Crandall in 1962 and today.
- `?property=Riverwood&hist=lidar&base=leafoff&layers=boulders,bfields,ledges,roads&panel=0` shows Riverwood's bedrock, erratics and boulder fields.
- `?property=Winnapaug&base=leafon&layers=grass,roads` shows Winnapaug Farm's restoration-ready grassland.

## Sources and credits

- Base imagery: RIGIS orthophotography, March 2026 (leaf-off) and July 2022 (leaf-on).
- Historic aerials: 1939, 1951–52 and 1962 statewide photography, RI Statewide Planning / RIGIS (URI EDC).
- LiDAR: USGS 3DEP, RI_Statewide_D22 (2022).
- Soils: USDA NRCS SSURGO.
- Bedrock geology, glacial deposits, E-911 roads, stone walls, 2020 land use/land cover and Local Conservation Areas: RIGIS.
- Property boundaries: RIGIS Local Conservation Areas (2026) and Westerly Land Trust (2021). Camp Quequatuck (acquired Dec 2025) is not included; no public boundary yet.
- Leaflet 1.9.4, BSD-2-Clause (`lib/LEAFLET-LICENSE`).

All mapped landforms are LiDAR and photo interpretations, not field-verified.

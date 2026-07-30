# Custom KPI Card — Tableau Dashboard Extension

Recreates the "Sales / 2023-12-01 / 1800 / +250 (+16%) vs Previous Month / trend chart"
card style, fully data-driven off a Date field and a KPI field from any worksheet.

## Files
- `manifest.trex` — the extension manifest you add to a dashboard in Tableau.
- `index.html` — the KPI card itself (title, period, value, delta, trend chart).
- `config.html` — the "Configure" dialog (worksheet, Date field, KPI field,
  aggregation, title, prefix/suffix, decimals, comparison period).
- `icon.png` / `icon_b64.txt` — the icon embedded in the manifest.

## ⚠️ Before this will work: host the two HTML files
Tableau Dashboard Extensions load their UI from a URL, not from your local disk
(except in a special developer/debug mode). You need to:

1. Upload `index.html` and `config.html` (they must stay in the same folder,
   since `index.html` looks for `config.html` next to itself) to any HTTPS
   web host you control — e.g. GitHub Pages, an internal web server, S3 +
   CloudFront, Netlify, etc. Both files must be served over **https**.
2. Open `manifest.trex` in a text editor and replace the placeholder URL:
   ```xml
   <source-location>
     <url>https://your-host.example.com/kpi-card/index.html</url>
   </source-location>
   ```
   with the real URL to your hosted `index.html`.

### Testing locally without hosting anything
Tableau Desktop has a developer mode that trusts `http://localhost`:
- Settings → Extensions → enable "Extensions Sandbox"/"Run in developer mode"
  is not needed — instead, run any static file server, e.g.:
  ```
  cd kpi-card-extension
  python3 -m http.server 8765
  ```
  then set the `<url>` in `manifest.trex` to `http://localhost:8765/index.html`
  and enable **Allow unsigned extensions to be added to workbooks** /
  **local extension** setting in Tableau's dialog when adding it.

## Adding it to a dashboard
1. In Tableau Desktop, drag a **Extension** object onto your dashboard.
2. Choose **My Extensions** → browse to `manifest.trex` (or, if hosted in an
   Extension Gallery, select it there).
3. Click through the "run this extension" trust prompt.
4. The card will show **"Configure KPI Card"** the first time — click it and set:
   - **Worksheet** — the sheet the extension should read from.
   - **Date field** / **KPI field** — the two fields it needs.
   - **Aggregation** — Sum / Average / Last value, used both to build the
     current KPI number and to roll values up into each period bucket.
   - **Card title**, **value prefix/suffix** (e.g. `$`, `%`, `units`), **decimals**.
   - **Comparison period** — Previous Month / Quarter / Year. This also
     controls how the trend chart groups points (one point per month,
     quarter, or year).
5. Click **Save**. The card renders the latest period's value, the delta vs.
   the prior period, and a gradient trend chart of all periods found in the data.

## How the numbers are computed
- All rows are bucketed by the Date field into month/quarter/year buckets
  (per your chosen comparison period).
- Each bucket's KPI value = sum, average, or last-value-by-date of the KPI
  field within that bucket (per your chosen aggregation).
- **Current value** = the most recent bucket.
- **Delta** = current bucket − previous bucket; **% change** = delta ÷
  |previous bucket|.
- The **trend chart** plots every bucket found in the data, oldest to newest.

## Customizing look & feel
Colors, font sizes, and the trend chart's smoothing are all in `index.html`
under the `<style>` block (`--accent`, `--green`, `--red`) and the
`renderChart()` function, so you can re-theme it without touching the data logic.

## Notes / limitations
- This extension requires **Full Data** permission (set in the manifest) so
  it can read the underlying summary data for the trend line, not just the
  visible marks.
- Dates need to parse via JavaScript's `Date` constructor; standard Tableau
  date exports (ISO-like strings, native Date objects) work fine.
- Gallery/marketplace distribution requires Tableau's extension signing
  process — this package is unsigned and intended for internal/private use
  unless you sign it.

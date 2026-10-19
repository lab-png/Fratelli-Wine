# Fratelli Wine PWA — GitHub Pages files

This version does **not** use Google Apps Script. The app reads the Google Sheet directly through Google's Visualization endpoint.

## Files
- `index.html` — app interface and spreadsheet search
- `manifest.webmanifest` — PWA metadata
- `sw.js` — basic app-shell caching for installation/offline shell

## Important setup
1. In Google Sheets, click **Share**.
2. For this public, no-login app to read the sheet, set **General access** to **Anyone with the link — Viewer**. This means people who have the link can view the spreadsheet. Do not use this method if the spreadsheet contains confidential information.
3. Open the GitHub repository used for GitHub Pages.
4. Upload all three files to the repository root, replacing the old `index.html` if prompted.
5. Commit the changes and wait for GitHub Pages to publish.
6. Open the GitHub Pages URL and test a tank number.

## Column mapping
- Tank number: `TANK NO`
- Displayed wine name/code: `CODE` (your provided headers did not include a separate `Wine Name` heading)
- Type: `RED/WHITE/ROSE`
- Analysis date: `Date of Analysis`
- Alcohol: `Alc %`
- TA: `T.A`
- pH: `pH`
- Free SO2: `FSO2`
- Total SO2: `TSO2`

If `CODE` is not the wine name/code you want displayed, update the `name` aliases in `index.html` to the correct column heading.

## Refresh
The app refreshes the sheet data every 60 seconds and has a manual **Refresh data** button. Updates can be delayed by Google Sheets publishing/caching. This is periodic refresh, not guaranteed instant push.

## Troubleshooting
- If the app says it cannot load the sheet, confirm the sheet is shared with **Anyone with the link — Viewer**.
- If the error says a heading is missing, confirm the first row of the selected tab contains the exact headings listed above.
- If your sheet uses a different tab ID, change `SHEET_GID` in `index.html`.

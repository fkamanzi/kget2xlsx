# kget to Excel

Turn an Ericsson kget dump into an Excel workbook, in your browser.

**Use it here: https://fkamanzi.github.io/kget2xlsx/**

Open the link in Chrome or Edge, drop your kget file, and click **Download Excel**. Nothing to install.

On a phone, open the link in Chrome or Safari. Browsers inside apps such as LinkedIn often can't pick or save files.

## What the workbook holds

| Sheet | Contents |
|---|---|
| Summary | The MO count checked against the file's own `Total: N MOs` line, and a link to every sheet |
| One sheet per MO class | One row per MO and one column per parameter, with the parent MOs as columns, so relation rows show their source cell. Struct members show as `struct.member`; array elements are joined with ` \| ` |
| Parameters | Every value on its own row, with the line it came from in the kget (optional) |
| Checks | Every line the parser could not place, every struct or array whose entry count does not match what it declares, and every change made to fit Excel |

Nothing is dropped silently: if a line cannot be placed, it is listed on the Checks sheet with its line number.

## Input

- kget text output, as saved from `lt all; kget`, in plain text, `.log`, `.txt` or `.gz`.
- UTF-8 or UTF-16 text. A `.zip` must be unzipped first.

## Privacy

The page reads your file in the browser. The kget is never uploaded and the page makes no network requests. To use it fully offline, save the page or download `index.html` and open it from your disk.

## Excel limits

Classes with more than 1,048,576 MOs and the Parameters sheet split across numbered sheets. Columns beyond Excel's 16,384 and text beyond 32,767 characters per cell are cut, and each cut is listed on the Checks sheet.

## Testing

Checked against an independent reference parser, the published Excel file schema (ISO/IEC 29500), a LibreOffice open-and-save round trip, and end-to-end runs in Chromium, including a 75 MB stress-test file (65,600 MOs). Confirmed on a live-node kget.

Node releases and MO models differ. If your file puts a line on the Checks sheet, open an issue with that line, with node names, addresses and anything else sensitive masked.

Independent tool; not affiliated with or endorsed by Ericsson.

Version 1.1, 6 Oct 2026. Prepared by Frutos

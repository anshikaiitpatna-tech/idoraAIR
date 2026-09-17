> Turn one SVG design template and a spreadsheet into hundreds of press-ready ID cards — zero manual copy-pasting in Canva or Illustrator.
 Preview & Overview

![Bulk ID Studio App Preview](./Screenshot%202026-09-17%20231230.png)

Designing bulk credentials manually in Canva, Figma, or Illustrator is tedious, repetitive, and prone to human error.

IDORA was built for the IIT Patna Alumni & International Relations Cell to automate Alumni ID card generation for 250+ recipients, eliminating hours of repetitive design handoffs.


Live Demo

Check out the live application: [bulk-id-studio.vercel.app]((https://idora-air.vercel.app/))



 What It Does

1. Upload a Template (SVG): Upload an SVG design containing placeholder tokens such as `{{Name}}`, `{{Roll No}}`, `{{Department}}`, and a photo box.
2. Upload Data (CSV / XLSX): Import a spreadsheet with one row per person.
3. Smart Column Mapping: Map each spreadsheet column to a template token. The app auto-suggests matches and highlights missing fields.
4. Live In-Browser Preview: Preview cards live with real data rendered into the actual design before generating anything.
5. Bulk Export: Every row is converted into a finished card and packaged as a downloadable ZIP of PNGs plus a print-ready combined PDF.

Key features

Dynamic token detection — No hardcoded fields. Any {{Token}} present in the uploaded SVG is automatically detected and added to the mapping interface.
Photo matching — Map a spreadsheet column to a photo filename or URL. Unmatched photos are clearly flagged instead of failing silently.
Design-tool agnostic — Works with SVGs exported from Figma, Illustrator, or Canva. Common export quirks are handled automatically:
Canva’s split-<tspan> text export (where tokens are broken across multiple text runs) is merged back into a single readable token.
Placeholder shapes exported as <rect>, <circle>, or <ellipse> (the default in Figma, Illustrator, and Canva) are converted into real <image> elements at render time, because photo swapping only works on <image> tags in SVG.

Live quality checks — Mapped fields, matched photos, and imported rows are calculated live from the uploaded data. Issues are listed specifically (for example, “Lina Joseph — photo filename not found”) rather than shown as a generic error count.
Bulk export — All cards are delivered as a ZIP of individual PNGs, together with a combined print-ready PDF (CR80 card size, multiple cards per page).

Tech stack

React + TypeScript, Tailwind CSS
papaparse / xlsx (SheetJS) for spreadsheet parsing
jszip for archive handling and ZIP export
Native SVG DOM manipulation for token substitution and photo embedding
Canvas-based SVG → PNG rasterization

 Known Limitations

Outlined Text: If SVG text has been converted to outlines/paths during export (e.g., Illustrator's *Create Outlines*), tokens cannot be detected. The source design must be exported with editable text.
Complex Crops: Non-rectangular photo crops require the source file's original `<clipPath>` definitions to be preserved during export.

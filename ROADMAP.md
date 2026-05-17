# Job Quoter — Roadmap

## v0.1 (shipped May 16, 2026)
- Job tab: customer + site + business profile (saved across jobs)
- Photos tab: timestamped photos, camera + library
- Quote tab: materials + labour line items, totals (tax, discount, deposit)
- Saved jobs tab: archive + load + delete
- Generate quote PDF (jsPDF) with photos embedded
- Autosave to localStorage

## v0.2 (shipped May 16, 2026)
- Saved jobs: "Sent to customer" checkbox (like MTO's "Sent to MTO")
- Time on site: auto-calculated from first photo → last photo timestamps,
  shown on Job tab and printed on quote PDF.

## v0.3 (shipped May 17, 2026)
- Photos tab as the default landing tab.
- Labeled photo capture buttons: Before / During / After / Receipt /
  Other. Each opens the rear camera and tags the photo. From-library
  pickup prompts for a label.
- Label badge on each thumbnail (tappable to relabel).
- Quote PDF: photos grouped by label, each with a section header.

## v0.4 (shipped May 17, 2026)
- Voice note button on the Job tab — Web Speech API streams transcription
  into the Job description as you talk. Works in Chrome and Safari/iOS;
  asks mic permission once.
- Photo preview strip on the Quote tab — see exactly which photos will
  land in the PDF while you build the line items. Tap a thumb to jump
  back to Photos.

## v0.5 — receipt OCR + voice → line items (queued, BIG lift)
- When a Receipt photo is taken, OCR it to extract the dollar amount
  and auto-add as a Materials line item. Requires either:
    a) Tesseract.js in-browser (~10 MB lib, works offline once cached,
       lossy on bad lighting / curled receipts).
    b) A cloud OCR API (Google Vision, AWS Textract — paid, needs a
       backend, much more accurate).
- Voice-note → AI parsing — feed transcribed voice into Claude API
  (or similar) to extract structured materials / labour line items from
  natural speech. Same backend question as above.
- Honest note: neither feature works without either a backend or a
  big in-browser library. Pick a direction before building.

## v0.3 (queued)
- Calendar integration. Add a job to macOS Calendar / iCloud (.ics export
  as a first pass — simplest cross-platform option, drops into any
  calendar app). Later: maybe a CalendarKit MCP if one becomes available.
- Excel export. Per-job .xlsx with sheets for:
  - Summary (customer, dates, totals, time on site, sent status)
  - Materials (description, qty, rate, line total)
  - Labour (description, qty, rate, line total)
  - Photos (filename, timestamp, kb)
  Useful for taxes, end-of-year totals, and customer record-keeping.

## v0.4 (queued, possibly)
- Receipts capture (separate tab, photo + amount + category, files into
  the job's archive).
- Customer signature line on the quote PDF (tap to draw, embed in PDF).
- Email-the-quote button (opens default mail client with PDF attached).

## v0.5+
- Multi-user / sync (iCloud Drive or a backend).
- Inventory tracking — preset materials with prices that you reuse across
  jobs.
- Invoice mode (convert an accepted quote into an invoice, separate doc).

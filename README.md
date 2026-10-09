# CBC Report Reader

A single-page tool for reading Credit Bureau Cambodia (CBC) enquiry responses (`ENQUIRYV6` XML).
Lenders often receive these as a `.txt` database export where each row is one whole report squashed
onto a single line, which is unreadable in Notepad. This page turns each report into readable sections.

## What it shows

- K-Score panel laid out like CBC's report: risk grade (AA to EE), score marker on the 100 to 1400 bar and bad rate.
  When CBC gives no score, the SE1 to SE7 code is shown with its meaning, and SE5 to SE7 are flagged in red.
  A "How to read K-Score" guide explains grades, bad rate, scoring factors and SE codes
- Applicant identity, report reference and advisory
- Loan accounts grouped by bank, with:
  - a multi-select bank filter
  - an **All loans / Active only** switch (active = not marked closed)
  - totals for Loan Amount, Installment and Outstanding Balance, per bank and overall (each currency totalled separately)
- Enquiry history with 30-day, 90-day and 12-month counts
- Employment, addresses, other names on file, and a check of the details the lender sent against the bureau record
- The original XML, pretty-printed
- **Export to Excel**: Overview, Loan accounts, Enquiries, Employment and Addresses sheets
- **Edit XML**: change any field value (grouped like the report, with search and a review list of changes).
  **Save as new file** writes a copy that is byte-for-byte identical to the original except the edited values:
  same encoding and byte-order mark, line endings, empty tags and column padding in pipe-table exports.
  Every save creates a new file named `<original>_edited_<YYYYMMDD-HHMMSS>`; the original is never overwritten

## How to use

Open `index.html` in a browser (or turn on GitHub Pages for this repo), then click **Open file**, drag a
`.txt`/`.xml` export onto the page, or paste the XML text.

The page opens with two invented example applicants until you load a file.

## Privacy

Files are read entirely in your browser. Nothing is uploaded and no customer data is stored in this repository.
The page loads fonts from Google Fonts and the Excel library (SheetJS) from cdnjs; everything else is in `index.html`.

## Notes

Some field labels are interpretations of CBC tag names. Tick **Show field codes** to see the original
tag next to each label and check it against CBC's specification.

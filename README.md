# DragonBasic
Scans and OCR of the Dragon Data version of Microsoft Extended Color BASIC for the Motorola 6809.

# Repository Layout
- docs
  - Manuals for the Motorola RASM09 assembler that was likely used (given the listing style)
- listing
  - The final merged file of each source listing after OCR and correction.
  - These are "perfect" reproductions of each file from Duncan's original listing.
- ocr
  - The OCR of each scanned page, split into per source file directories. This is also where OCR correction takes place
-- OriginalScans
  - Dump of all 341 scanned pages of the four listing bundles, split into per source file directories.
  - These were scanned over the Saturday and Sunday of the Dragon Meetup 2022 in Port Talbot, Wales from the original assembler output listing that Duncan printed in 1983 or 1984.
- src
  - A copy of the listing files but with the following removed to reproduce the original source.
    - PAGE heading lines
    - TOTAL-WARNINGS lines
    - TOTAL-ERRORS lines
    - Columns 1 through 27 (generated line/sequence numbers and assembled output)



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
- OriginalScans
  - Dump of all 341 scanned pages of the four listing bundles, split into per source file directories.
  - These were scanned over the Saturday and Sunday of the Dragon Meetup 2022 in Port Talbot, Wales from the original assembler output listing that Duncan printed in 1983 or 1984.
- src
  - A copy of the listing files but with the following removed to reproduce the original source.
    - PAGE heading lines
    - OPT settings for listing (printing) configuration
    - TOTAL-WARNINGS lines
    - TOTAL-ERRORS lines
    - Columns 1 through 27 inclusive (the generated line/sequence numbers and assembled output)
  - The source is not 100% complete as there are a few conditional macros listed as empty IFNE <DEFINE> / ENDC blocks that Dragon Data must not have defined. It is not currently known if these were for Microsoft (or OEM) development use or alternate systems, and more may be discovered as we OCR.
    - FRESW
    - GRPTEK
    - REALIO
    - SPCSW
    - WAITSW

# File Author
Current thinking is that the following are Microsoft files common across Tandy and Dragon Data:
- ECBRAM.SA
- ECBBAS.SA
- ECBBS2.SA
- ECBTAB.SA
- ECBDNL.SA
- ECBPU.SA
- ECBMTH.SA
- ECBEXT.SA
- ECBGRP.SA
  
Given the Microsoft copyright comment blocks (and boot screens!) and METTOY macro blocks, these two files appear to be customized by Microsoft for Dragon Data:
- ECBMOD.SA (Dragon 64 32K ROM)
- ECBM64.SA (Dragon 64 64K ROM)
  
The last two files have no copyright notice and appear to be Dragon Data's BIOS that Duncan wrote:
- ECBOEM.SA (Dragon 64 32K ROM)
- ECBO64.SA (Dragon 64 64K ROM)
  

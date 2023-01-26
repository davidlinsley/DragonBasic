# DragonBasic
Scans and OCR of the Dragon Data version of Microsoft Extended Color BASIC for the Motorola 6809.

# Repository Layout
- docs
  - Manuals for the Motorola RASM09 assembler that was likely used (given the listing style)
- listing
  - The final merged file of each source listing after OCR and correction.
  - These are simply the corrected pages from the associated ocr sub-directory, appended together.
- ocr
  - The OCR of each scanned page, split into per source file directories.
  - Each page is corrected in place to create "perfect" reproductions of each page of Duncan's original listing.
- OriginalScans
  - Dump of all 341 scanned pages of the four listing bundles, split into per source file directories.
  - These were scanned over the Saturday and Sunday of the Dragon Meetup 2022 in Port Talbot, Wales from the original assembler output listing that Duncan printed in 1983 or 1984.
- src
  - A copy of the files from the listing directory but with the following removed to reproduce the original source.
    - PAGE heading lines
    - OPT settings for listing (printing) configuration
      - Though maybe these should be added back in.
    - TOTAL-WARNINGS lines
    - TOTAL-ERRORS lines
    - Columns 1 through 27 inclusive (the generated line/sequence numbers and assembled output)

# Source Fidelity
The source is complete as output by the assembler used at Dragon Data, barring unintentional errors from the manual correction of the OCR. Any spelling mistakes and duplicate words (like "the the") present in the comments are left as is. However, the source is not 100% complete as when shipped by Microsoft:
- We do not yet know the composition of ECBCOM.SA (see Issue ECBCOM.SA #15)
- There are missing macro definitions which the assembler did not list the bytes for, like SKIP2
- Empty IFNE <cconditional> / ENDC blocks that Dragon Data must not have defined as the line numbers do show gaps. It is not currently known if these were for Microsoft (or OEM) development use or alternate systems, and include:
  - CNTRLO
  - FRESW
  - GRPTEK
  - REALIO
  - SPCSW
  - TODCLK
  - WAITSW
  - &0 such as "MONITOR COMMAND - SIMPLE M G R D" page title but no code inside the IFNE &0 block

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
  

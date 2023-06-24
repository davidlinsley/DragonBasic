# Microsoft BASIC for the Dragon 64
This repository contains the source code for the Dragon 64 versions of the Microsoft 16K BASIC Interpreter for the Motorola 6809 (aka BASIC-69 and Extended Color BASIC).

The source was recovered from a paper listing of the Motorola assembler output that was produced in 1983 at Dragon Data's R&D facility near their Kenfig factory in Port Talbot, Wales. The shared and unique source for both the 32K and 64K mode ROMs are present, and despite being boxed in an attic for a majority of the previous 39 years, the listing is very well preserved. It totals 340 pages of fan-fold tractor feed across 4 bundles.

Scanning was hand fed one page at a time (carefully not breaking any of the fan fold or tractor perforations) the weekend of October 22nd-23rd at the 2022 Dragon Meetup. This was also in Port Talbot to mark the 40th Anniversary celebration of the Dragon 32. Over the following months the scans were bulk OCR'ed and manually corrected. Only a handful of poor scans required consulting the original listing.

# Repository Layout
- docs
  - The manual for the Motorola RASM09 assembler that was likely used given the listing format and that it is documented that Dragon Data owned several Motorola EXORset systems.
- listing
  - The individual source files broken out from the complete listing.
  - Each file is simply the corrected pages from the associated ocr sub-directory appended together.
- ocr
  - The OCR of each scanned page split into per source file directories.
  - Each page is corrected in place to create reproductions (including alignment) of each page of the original listing.
  - Some later corrections were only made to the listing and src directory files as the contents of this folder were just an intermediate step.
- scans
  - The scanned pages of the four listing bundles, split into per source file directories.
- src
  - A copy of the files from the listing directory but renamed to the original filenames in the listing page titles.
  - The following items are removed:
    - PAGE heading lines
    - OPT settings for listing (printing) configuration
      - These possibly should be added back in, but they may have been included via ECBCOM.SA.
    - TOTAL-WARNINGS lines
    - TOTAL-ERRORS lines
    - Columns 1 through 27 inclusive which are the generated line/sequence numbers and assembled output.

# Source Fidelity
The source is complete as output by the assembler barring unintentional errors from OCR and manual correction. Pull Requests to fix those are welcome, but original spelling mistakes and other original errors (for example duplicate words like "the the") are intentionally left as is. However, the source is not 100% complete as when shipped by Microsoft:
- We do not yet know the composition of ECBCOM.SA
  - See issue ECBCOM.SA #15.
  - The contents of this file appear to have been the equivalent of #include into the other source files as ECBCOM.SA appears as the filename in the header line of every PAGE 001 of the other files.
- There are missing macro definitions which the assembler did not list the bytes for, such as SKIP2.
  - These were likely defined in ECBCOM.SA.
  - Disassembling the ROMs we can recreate the macros but not any comments. 
- Empty IFNE / ENDC blocks that Dragon Data must not have defined the conditional for as the line numbers do show gaps. We can only speculate if these were for Microsoft or OEM development, alternate systems and  optional features. They include:
  - CNTRLO
  - FRESW
  - GRPTEK
  - REALIO
  - SPCSW
  - TODCLK
  - WAITSW
  - &0 such as the "MONITOR COMMAND - SIMPLE M G R D" page title but no code inside the IFNE &0 block.

# Authors
The following appear to be pure Microsoft files common across licensees:
- ECBRAM.SA
- ECBBAS.SA
- ECBBS2.SA
- ECBTAB.SA
- ECBDNL.SA
- ECBPU.SA
- ECBMTH.SA
- ECBEXT.SA
- ECBGRP.SA

These two files are variants for the 32K and 64K ROMs and contain Microsoft copyrights and the source for commands like CLS, AUDIO, SET and RESET. However, they also contain METTOY (the British toy company who originally formed Dragon Data) macro blocks for the boot screens followed immediately by empty GRPTEK blocks. It is unknown if they were customized by Microsoft for Dragon Data (and similarly for other licensees) or by Dragon Data, but the "mod" name may be a tell to the latter:
- ECBMOD.SA (Dragon 64 32K ROM)
- ECBM64.SA (Dragon 64 64K ROM)

The last two files are the Dragon Data BIOS written by Duncan Smeed:
- ECBOEM.SA (Dragon 64 32K ROM)
- ECBO64.SA (Dragon 64 64K ROM)

# Acknowledgements
## Duncan Smeed
Duncan is the author of the Dragon Data BIOS and coauthor of the seminal book Inside the Dragon. In early 1982 he flew to Seattle from the UK for a single day roundtrip - to the bemusement of immigration at SeaTac Airport - to pick up the BASIC source code disk.

Bookending that adventure, he hand delivered the listing to the Dragon Meetup where he helped scan a majority of pages.

## Richard Harding
## Tony Jewell
Richard and Tony organized the 2022 Dragon Meetup and Richard's A3 scanner was kindly loaned for this project.

They continue to unearth Dragon history which they share on the Facebook Dragon 32/64 Owners/Users group and Twitter.

## Tim Gilberts
Tim helped scan a bulk of the listing, pairing with Duncan and myself. At the start of the weekend he didn't know of this project, but happily sacrificed his time.

## Rich Turner
While at Microsoft Rich led the publishing of the GW-BASIC source code and provided the contacts and guidance for trying to publish the Microsoft code through the same route. He is also a former Dragon 32 owner from the original era.

## Dave Plummer
Dave is a former Microsoft employee who saw my plea for current appropriate contacts and used his network to secure permission for myself to publish the Microsoft source.

## Cecelia, Chiara and Thea Linsley
This project would not have been possible without the support of my amazing wife and kids to attend the 2022 Dragon Meetup. This also fulfilled my childhood dream - since Christmas 1984 - of visiting the former Dragon Data factory.

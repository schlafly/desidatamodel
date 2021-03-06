===
fvc
===

:Summary: Fiber View Camera images for ProtoDESI.
:Naming Convention: ``fvc\.[0-9]{8}(_[0-9]{4}|[0-9]{6})\.fits``
:Regex: ``fvc\.[0-9]{8}(_[0-9]{4}|[0-9]{6})\.fits``


Contents
========

====== ======== ============================== ================================================================
Number EXTNAME  Type                           Contents
====== ======== ============================== ================================================================
HDU0_  PRIMARY  NPIXxNPIX float image          raw image
====== ======== ============================== ================================================================

FITS Header Units
=================

HDU0
----

EXTNAME = PRIMARY

FITS Image: Raw


Required Header Keywords
~~~~~~~~~~~~~~~~~~~~~~~~

======== ========= ==== ========================================
Header   Value     Type Comment
======== ========= ==== ========================================
XTENSION BINTABLE  str  Binary table written by MWRFITS v1.8
BITPIX   8         int  Required value
NAXIS    2         int  Required value
NAXIS1   6132      int  Number of bytes per row
NAXIS2   8176      int  Number of rows
PCOUNT   0         int  Normally 0 (no varying arrays)
GCOUNT   1         int  Required value
TFIELDS            int  Number of columns in table
======== ========= ==== ========================================

Required Columns
~~~~~~~~~~~~~~~~

================= ======== =======
Column            Type     Comment
================= ======== =======
TAI-BEG           float    Timestamp
EXPTIME           float    Exposure Time
IMG-X             int64    Image size -x
IMG-Y             int64    Image size -y
TEMP              float    Temp of camera
TEL-RA            float    Telescope RA
TEL-DEC           float    Tel.DEC
AMASS             float    Airmass
F0-X              float    Fiber 1 X pixel value
F0-Y              float    Fiber 1 Y pixel value
MAG0              float    Mag of Fiber 0
PSF0              float    Size of PSF for Fiber 0
F1-X              float    Fiber 1 X pixel value
F1-Y              float    Fiber 1 Y pixel value
MAG1              float    Mag of Fiber 1
PSF1              float    Size of PSF for Fiber 1
F2-X              float    Fiber 2 X pixel value
F2-Y              float    Fiber 2 Y pixel value
MAG2              float    Mag of Fiber 2
PSF2              float    Size of PSF for Fiber 2
F3-X              float    Fiber 3 X pixel value
F3-Y              float    Fiber 3 Y pixel value
MAG3              float    Mag of Fiber 3
PSF3              float    Size of PSF for Fiber 3
================= ======== =======

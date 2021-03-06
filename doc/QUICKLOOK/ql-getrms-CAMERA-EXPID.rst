===========================
ql-getrms-CAMERA-EXPID.json
===========================

:Summary: This QA for QuickLook includes the calculation of the RMS
        of pixel values in the 2-D pix file after the preprocessing stage. 
:Naming Convention: ``ql-getrms-{ARM}{SPECTROGRAPH}-{EXPID}.json``, where 
        {ARM} is the 1-char arm name (r,b,z), {SPECTROGRAPH} indexes 
        CCDs 0-9 on that arm, and {EXPID} is the 8-digit exposure ID.  
        Together, {ARM}{SPECTROGRAPH} specify a {CAMERA}.
:Regex: ``ql-getrms-[brz][0-9]-[0-9]{8}\.json``
:File Type:  JSON


Inputs
======

Written by qa_quicklook.py, with Get_RMS using:

- preproc image

Contents
========

========== ================ ===========================
KEYNAME    Type             Contents
========== ================ ===========================
GETRMS     Py dictionary    image root-mean-squared
========== ================ ===========================



Dictionary Contents
===================

KEYNAME = GETRMS

Spectral root-mean-squared calculations per image and per CCD amp.

Keyword Description
~~~~~~~~~~~~~~~~~~~

================== ============= ========== ==================================================
KEY                Example Value Type       Comment
================== ============= ========== ==================================================
CAMERA             b4            string     b0-b9, r0-r9, z0-z9
EXPID              00003900      int  	    Exposure ID
FLAVOR             science       string     The type of exposure that can flat, arc or science 
PANAME             PREPROC       string     Name of pipeline algorihm
QATIME             2018-05-27T   float      Timestamp (UTC) of time of QA execution
                   11:31:42.766
NIGHT              20191017      int        The night of observation            
PROGRAM            dark          string     name of the observing program: dark, grey, bright


NOISE              2.009         float      value of RMS across image 
NOISE_AMP          4             float[4]   value of RMS for each amplifier read directly from the header of the preproc image  
NOISE_OVERSCAN_AMP 4             float[4]   value of RMS of the onerscan region per amplifier read directly from the header of the preproc image
BIAS_PATNOISE      4             float[4]   rms of the row by row bias difference divided by the noise of that amp   
NOISE_STATUS       ALARM         string     status of NOISE_AMP 
DATA5SIG           1             float      number of pixels more than 5 sigma below bias in data region of CCD (BOSS)
DIFF1SIG           0.045         float      difference between 1 sigma low and high percentile bounds
DIFF2SIG           0.129         float      difference between 2 sigma low and high percentile bounds
================== ============= ========== ==================================================

Example JSON Output
~~~~~~~~~~~~~~~~~~~

::

    {
    "CAMERA": "b4",
    "EXPID": "00003900",
    "FLAVOR": "science",
    "METRICS": {
        "BIAS_PATNOISE": [
            0.001928452933161584,
            0.0020551932894211223,
            0.013377496003722351,
            0.013273444424777932
        ],
        "DATA5SIG": 1,
        "DIFF1SIG": 0.032,
        "DIFF2SIG": 0.056999999999999995,
        "NOISE": 2.0094836050884783,
        "NOISE_AMP": [
            1.9158278538024538,
            2.013828948358283,
            2.0502913804455387,
            2.1458059208513554
        ],
        "NOISE_OVERSCAN_AMP": [
            1.887512473265009,
            1.996400550363147,
            2.032141125973641,
            2.121880270752116
        ],
        "NOISE_STATUS": "NORMAL"
    },
    "NIGHT": "20191017",
    "PANAME": "Preproc",
    "PARAMS": {
        "NOISE_AMP_REF": [
            1.3184224194929928,
            1.390981338461623,
            2.078279428799927,
            1.6012346133106736
        ],
        "NOISE_NORMAL_RANGE": [
            -1.0,
            1.0
        ],
        "NOISE_WARN_RANGE": [
            -2.0,
            2.0
        ],
        "PERCENTILES": [
            68.2,
            95.4,
            99.7
        ]
    },
    "PROGRAM": "dark",
    "QATIME": "2018-05-27T11:31:43.342882",
     }

=============================
ql-mergedQA-CAMERA-EXPID.json
=============================

:Summary: This QA for QuickLook includes the calculation of the sky
	  continuum level in sky fibers.
:Naming Convention: ``ql-mergedQA-{ARM}{SPECTROGRAPH}-{EXPID}.json``, where 
        {ARM} is the 1-char arm name (r,b,z), {SPECTROGRAPH} indexes 
        CCDs 0-9 on that arm, and {EXPID} is the 8-digit exposure ID.  
        Together, {ARM}{SPECTROGRAPH} specify a {CAMERA}.
:Regex: ``ql-mergedQA-[brz][0-9]-[0-9]{8}\.json``
:File Type:  JSON


Inputs
======

Written by merger.py using:


Contents
========

========== ================ ==============================================
KEYNAME    Type             Contents
========== ================ ==============================================
SKYRESID   Py dictionary    Residuals calculation on sky fibers
========== ================ ==============================================



Dictionary Contents
===================

KEYNAME = mergedQA

SKY residuals calculations over each sky fiber and averaged over sky fibers.


Keyword Description
~~~~~~~~~~~~~~~~~~~

======================= =================  ================ ===================================================
KEY                     Example Value      Type             Comment
======================= =================  ================ ===================================================
CAMERA                  r1                 string           b0-b9, r0-r9, z0-z9
EXPID                   00003577           int  	    Exposure ID
FLAVOR                  science            string           The type of exposure that can flat, arc or science 
NIGHT                   20191001           int              The night of observation
PROGRAM                 dark               string           Name of the observing program: dark, grey, bright 
SEEING                  1.1                float            From the header of the proproc image 
EXPTIME                 1000.0             float            From the header of the proproc image 
AIRMASS                 1.0                float            From the header of the proproc image 
ELG_FIBERID             331                int[ne]          From the fibermap, ne is number of ELGs
LRG_FIBERID             65                 int[nl]          From the fibermap, nl is number of LRGs
QSO_FIBERID             56                 int[nq]          From the fibermap, nq is number of QSOs
SKY_FIBERID             37                 int[nsky]        From the fibermap, nsky is number of SKY fibers
STAR_FIBERID            11                 int[ns]          From the fibermap, nsky is number STARs
IMAGING_MAGS            500, 3             float[500,3]     From the fibermap [DECAM_G, DECAM_R, DECAM_Z]
RA                      500                float[500]       Right ascention of all the 500 targets
DEC                     500                float[500]       Declination of all the 500 targets
B_PEAKS                 3                  float[3]         configured peak sky wavelengths in b band
R_PEAKS                 5                  float[5]         configured peak sky wavelengths in r band
Z_PEAKS                 6                  float[6]         configured peak sky wavelengths in z band
FITS_DESISPEC_VERSION   0.23.1.dev2840     string           version of the desispec software that created the fits
PROC_QuickLook_VERSION  09.18.0            string           version of the Quicklook software that was ran 
PROC_DESISPEC_VERSION   0.23.1.dev2840     string           versopn of the desispec software created the preproc image
QLrun_datime_UTC        2018-09-07         string           date and time of the merger as the last of quicklook step 
======================= =================  ================ ===================================================

======================= =================  ================ ===================================================
CHECK HDUs KEY          Example Value      Type             Comment
======================= =================  ================ ===================================================
EXPNUM_STATUS           NORMAL             string           Reports the result of a match between exposures number in the 
                                                            header and the 
                                                            one given in the argument
CHECKHDUS_STATUS        NORMAL             string           Reports the result of finding the camera in the header 
======================= =================  ================ ===================================================

======================= =================  ================ ===================================================
CHECK CCDs KEY          Example Value      Type             Comment
======================= =================  ================ ===================================================
BIAS_AMP                4                  float[4]         value of bias averaged over each amplifier
BIAS_AMP_STATUS         NORMAL             string           Reports the status of BIAS_AMP
BIAS_PATNOISE           4                  float[4]         rms of the row by row bias difference divided by the noise of 
                                                            that amp
DATA5SIG                1                  int              Number of pixels with counts 5sigma below bias in region of CCD
DIFF1SIG                0.032              float            Diff. between 1 sigma low and high percentile bounds 
DIFF2SIG                0.057              float            Diff. between 2 sigma low and high percentile bounds
LITFRAC_AMP             4                  float[4]         Fraction of the pixels per amp that are above CUTPIX = 5sigmas
LITFRAC_AMP_STATUS      NORMAL             string           Reports the status of LITFRAC_AMP
NOISE_AMP               4                  float[4]         value of RMS per amp read directly from the header of the 
                                                            preproc image
NOISE_OVERSCAN_AMP      4                  float[4]         value of RMS of the onerscan region per amp read directly from 
                                                            the header of the preproc image
NOISE_AMP_STATUS            NORMAL             string       Reports the status pf NOISE_AMP
======================= =================  ================ ===================================================

======================= =================  ================ ===================================================
CHECK FIBERS KEY        Example Value      Type             Comment
======================= =================  ================ ===================================================
XWSIGMA_FIB             2,500              float[500,2]     median of XSIGMAs for all fibers per amp
GOOD_FIBERS             500                boolean          List of boolians for good[1] and bad[0] fibers
NGOODFIB                N                  int              Number of good fibers
NGOODFIB_STATUS         NORMAL             string           Reports the status of NGOODFIB
XWSIGMA                 2                  float[2]         List of median X and W sigmas
XWSIGMA_AMP             4,2                float[4,2]       List of four [X,W]sigmas
XWSIGMA_STATUS          NORMAL             string           Reports the status of XWSIGMA
======================= =================  ================ ===================================================

======================= =================  ================ ===================================================
CHECK SPECTRA KEY       Example Value      Type             Comment
======================= =================  ================ ===================================================
DELTAMAG                500	           float[500]	    List of mag diff b/w the fibermag and the imaging mag from the                                                               fibermap
DELTAMAG_STATUS         NORMAL             string	    Status of DELTAMAG_TGT
DELTAMAG_TGT            [-2.92,...]	   float[N]	    List of the average fiber mag per target types in this camera
FIBER_MAG               [18.22, ...]	   float[500]       Magnitude of the 500 fibers
FIDSNR_STATUS           NORMAL	           string	    Reports the status of FIDSNR_TGT
FIDSNR_TGT              4	           float[4]	    List of fiducial SNR per target type
FITCOEFF_TGT            4,2	           float[4,2]	    List of 4[a,B] Best fit throughput("a") & sky b/g "B" per target
FITCOVAR_TGT            4,2x2	           float[16]	    List of 2x2 covariance matrices [[[c1,c2],[c3,c4]], ...]
MEDIAN_SNR              [1.3,...]	   float[500]       Median SNR per fiber
NSKY_FIB                37                 int              Number of sky fibers 
NUM_NEGATIVE_SNR        0	           int	            Number of targets with negative SNR
PEAKCOUNT               1                  float            Averaged summed counts for sky fibers over specified peak sky wavelengths
PEAKCOUNT_FIB           [91.56,...]        float[500]       summed counts over sky peaks on ALL the 500 fibers
PEAKCOUNT_NOISE         0.072              float            rms of PEAKCOUNT over sky fibers FOR SCIENCE EXPOSURES
PEAKCOUNT_STATUS        NORMAL             string           reports the status of the PEAKCOUNT 
SKYCONT                 210.0	           float	    SKY cont. in all configured continuum areas averaged over all 
                                                            sky fibers
SKYCONT_FIBER           357.238	           float[N]	    SKY continuum per sky fiber averaged over two continuum regions, 
                                                            'N' is number of sky fibers
SKYCONT_STATUS          NORMAL	           string	    Reports the status of the SKYCONT
SNR_MAG_TGT             4	           float[N]	    List of average SNR for target type, N is number of target types
SNR_RESID               436	           float[Nobj]	    List of the SNR values for the targets, Nobj is 500-Nskyfibers
STAR_FIBERID            11	           int[ns]  	    Fiber IDs for standard STARs, ns is number of the STARs
STD_FIBERID             11                 int[n]           Star Fiber IDs 
SKYRBAND                100.	           float            Average value of sky bg in R-band-> to come from ETC (current 
                                                            value is a place holder)
SKYRBAND_STATUS         NORMAL             string           Reports the status of the SKYRBAND 
SKY_RFLUX_DIFF          31.744744          float            Diff b/w flux from sky monitor and the averaged calculated mag from the 
                                                            sky fibers
SKY_FIB_RBAND           [64.109,...]	   float[N]	    Sky fiber mags in camera r [if the camera is not r, this 
                                                            is equal to the value of the SKYRBAND]
WAVELENGTH              5630...7740	   float[NWAVE]     Wavelength (Ang.) in NWAVE bins
XYSHIFTS                []                 float[2]         List of two averaged values (in pixel unit) for the fiber traces in X,Y directions
XYSHIFTS_STATUS         ALARM              string           Reports the status of the XYSHIFTS
======================= =================  ================ ===================================================

Example JSON Output
~~~~~~~~~~~~~~~~~~~
The file has 14667 lines!
    

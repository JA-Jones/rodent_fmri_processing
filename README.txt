Script for preprocessing of rodent fMRI data
Many thanks to P.Zhukovsky & J.Granjean for the implentation of this analysis

Requirements;
MATLAB
SPM8 with SPMmouse toolbox installed
FSL 
AFNI
Structural & functional fmri data 
High resolution structural template

Prior to script;
All functional images must be checked for artifacts/ghosting/phase gradient errors etc.
Initial correspondence of structural & functional images with common template done using 'bulk manual registration tool' in SPMmouse
This must be done for the structural images and also all volumes of the functional image
Voxel size x10 for correspondence between rodent and human imaging (this is imperative for registration later) - for all images (structure/functional/template)

Generation of masks for functional imaging
Structural images (alighed with fMRI data) is run through a 'vbm' type pipeline in SPM
The output (c1/c2/c3) images are combined (either through fslmaths or imcalc in spm) smoothed and binarised
Use this image as a mask to skullstrip the structural image
Check using FSL - may be necessary to manually correct image - fsleyes I have found is the best for this (see below; don't forget to edit in 3D mode)
If using imcalc the first input image will be the output image dimensions 
May be necessary to flirt this mask to the subsequent target image (as not uncommon for FSL to not mask based on incorrect voxel dimensions (check via fslinfo))

High resolution template image is skullstripped using the brain extraction tool in FSL (fslbet)
It may be necessary to adjust parameters of fslbet (e.g. -f & -R) and also to perform this action multiple times
Set colour to render3 and manually edit/remove non-brain voxels if necessary - another option is to use thresholding (fslmaths) for 'clean' template

File set-up
Parent folder with script, skull-stripped template image 
Subject folder as outlined by 'datanames'/scan4 with corresponding functional image and skullstripped structural image
Run script

If you have any questions the please email jaj58@cam.ac.uk








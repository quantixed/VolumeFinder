# VolumeFinder
Volume analysis of 3D point sets in IgorPro

This code is to measure the density of microtubules in a stack of TIFFs. Microtubules are first segmented in Amira and then converted to TIFFs using a FIJI macro. Finally, Igor will work out the volume of the microtubules as a density of the volume in which they are contained. 

1. Segmentation is first done in Amira. Segmented microtubule labels have the value 2.
2. Amira files are thresholded and converted to TIFF in FIJI using the [amThreshTiff.ijm](https://github.com/quantixed/VolumeFinder/blob/master/amThreshTiff.ijm) macro
3. These TIFFs are batch-processed by Igor

To do this call <code>VolumeFinder(2)</code>. 2 specifies the fastest calculation method. Now point Igor at the directory containing the TIFFs.

Caution:
* For best performance /VOL flag is used, only available in Igor 7 Beta 6
* Code will compile in Igor 6.3+ but will use a slower method
* Option 0 is the most straightforward, but is very slow. Benchmarking with <code>tic()</code> <code>toc()</code> timed a complicated data set (768 x 768 x 500, 1.2 x 10^6 points) at ~3 h on a Mac Pro 6 Core. Option 2 speeds this to ~90 s.

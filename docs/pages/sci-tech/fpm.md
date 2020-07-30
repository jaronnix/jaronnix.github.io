# Fourier Ptychographic Microscopy

## Overview
Fourier ptychography microscopy (FPM) is a computational imaging technique that generates a larger numerical aperture (NA) from a set of lower resolution full-field images acquired at various partially-coherent illumination angles, resulting in increased resolution compared to a conventional microscope.[^1]

??? abstract "What is Ptychography?" 
    <!--- Embedded video describing ptychography --->
    <div style="padding:56.25% 0 0 0;position:relative;"><iframe src="https://player.vimeo.com/video/345901457" style="position:absolute;top:0;left:0;width:100%;height:100%;" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe></div><script src="https://player.vimeo.com/api/player.js"></script>
    <p><a href="https://vimeo.com/345901457">Ptychography Explained</a> from <a href="https://vimeo.com/willarmson">Will Armson</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

## Process

### Illumination
In order to generate a set of full-field images, a specimen is illuminated at various angles of incidence via a three-dimensional LED array. Each image is acquired under the illumination of coherent light sources at these various angles of incidence. The different illumination angles correspond to images of different regions of frequency space. The set of acquired images is combined, using an iterative phase retrieval algorithm, into a final high-resolution image (a high space-bandwidth product).

Reassembling these regions into a single frequency domain image means that much higher resolution is obtained over the full field of view (FOV) of the microscope. Furthermore, FPM reconstructs the complex image of the object. As a result, amplitude (or intensity) and quantitative phase information can both be gathered using this technique. However, opposed to interferometric imaging techniques such as holography, FPM is much easier to implement.

Typically, from an array of LEDs, each image is acquired under the illumination of coherent light source at various angles of incidence. The different illumination angles correspond to imaging different regions of frequency space. The set of acquired images is combined, using an iterative phase retrieval algorithm, into a final high-resolution image (a high space-bandwidth product). Reassembling these regions into a single frequency domain image means that much higher resolution is obtained over the full field of view (FOV) of the microscope. Furthermore, FPM reconstructs the complex image of the object. As a result, amplitude (or intensity) and quantitative phase information can both be gathered using this technique. However, opposed to interferometric imaging techniques such as holography, FPM is much easier to implement.

![https://upload.wikimedia.org/wikipedia/en/6/61/Optical_setup_for_Fourier_ptychography.png](https://upload.wikimedia.org/wikipedia/en/6/61/Optical_setup_for_Fourier_ptychography.png)

The general optical configuration for a Fourier ptychography microscope Courtesy of [https://bit.ly/2YThFMA](https://bit.ly/2YThFMA)

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/LEDarray.jpg](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/LEDarray.jpg)

Pathware Inc. prototype LED array

[Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/LEDFPM.mp4](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/LEDFPM.mp4)

Operation of the FPM LED array (Courtesy of [https://bit.ly/2YIwBwW](https://bit.ly/2YIwBwW))

### Image Capture

#### Ptychography

If an object is illuminated with coherent electromagnetic radiation (e.g., visible light), a diffraction pattern is formed in the Fraunhofer far field that is related–via a Fourier transform–to the optical transmission function of the object. The aim of coherent diffractive imaging (CDI), or so-called lensless real-space ptychography is to directly reconstruct the original optical transmission function of the specimen from its measured diffraction pattern. This quantitative phase imaging (QPI) method leverages two important innovations for bypassing the current limitations in the space-bandwidth product of traditional microscopy and ptychography methods for whole slide imaging (WSI) of biopsies. First, lensless ptychography utilizes phase retrieval information for characterizing biological objects present in a biopsy. Phase information characterizes how much light is delayed through propagation and how much is lost during the recording process. The phase retrieval technique is able to recover the lost phase informationby using intensity-only measurements. This is accomplished by using alternating enforcements of the known information of the object in the spatial and Fourier domains. Second, lensless ptychography uses aperture synthesis for bypassing the resolution limit of traditional microscopy techniques. Aperture synthesis combines information from a collection of sources to expand the Fourier passband and improve the achievable resolution. In addition to a unique fusion algorithm, lensless ptychography is able to obtain a super-resolution that is ultimately limited only by the wavelength of the radiation used and not by the quality of optical lenses. In addition, this technique benefits from a large field-of-view and high-resolution, not seen in other biological microscopy techniques.

Spectral multiplexing (SM) produces a two-dimensional image of a polychromatic object separately in several bands of the spectrum. SM is important in biomedical sensing and whole slide imaging because it provides the ability to multiplex information and detect coherent-state decomposition in samples. In this project, Pathware will be using an array of light sources to illuminate the sample from different incident angles and acquire corresponding low-resolution images using a monochromatic camera. In Pathware’s proposed technique, multiple light sources are lit up simultaneously for information multiplexing, and the acquired images thus representing incoherent summations of sample transmission profiles corresponding to different coherent states. Using the state-multiplexed Fourier ptychography (FP) recovery routine, they will decompose the incoherent mixture of the FP acquisitions to recover a high-resolution biopsy image. In addition, color-multiplexed imaging will be performed by simultaneously turning on RGB LEDs for data acquisition and providing a solution for handling the partially coherent effect of light sources used in Fourier ptychographic imaging platforms. A key feature of Pathware’s technique is controlling the photographic illumination of the biopsy sample. Frequency mixing between the object and the structured light shifts the high-frequency object information to the passband of the photographic lens. Therefore, the recorded intensity images contain object information that is beyond the cutoff frequency of the collection optics. Based on multiple images acquired under different structured light patterns, they can use the Fourier ptychographic algorithm to recover the super-resolution WSI and the unknown illumination pattern.

[https://lh5.googleusercontent.com/KPRGiB0M6IhcnBr_kgIN7TFZWRKUFURMP6pNhtUd4yjRpr8MTFbkYLBg0EBt_ypHEuFkayklTn1MXl1KalAbAZeqJQqpW7JbcPMSIPQ8qYDApQ_2R2bMLUBMNN6mlb7wpNr-3jWW](https://lh5.googleusercontent.com/KPRGiB0M6IhcnBr_kgIN7TFZWRKUFURMP6pNhtUd4yjRpr8MTFbkYLBg0EBt_ypHEuFkayklTn1MXl1KalAbAZeqJQqpW7JbcPMSIPQ8qYDApQ_2R2bMLUBMNN6mlb7wpNr-3jWW)

#### Microscopy

!!! success "Resolution Comparison at 4X 0.10NA"
    === "Pathware"
        Maximum Resoltion at 0.39µm/pixel
    === "Standard"
        Maximum Resolution at 2.75µm/pixel

The Bioptic™ unit images no differently than standardized video microscopes: a wide-field objective lens, typically 2X or 4X, projects an image on to a standard CMOS sensor, typically ⅔” or 1.0”. The numerical aperture (NA) of the objective lens is the limiting factor in gathering detail for most microscopy sensors. Optical systems are limited in resolution by diffraction, also known as spatial bandwidth, offering a hard-stop to the resolution that a standard lens and CMOS sensor can achieve. The finest resolution able to be achieved in a given optical system is listed below, where λ is the wavelength of light (nm):

<!-- Final Resolution Equation -->
$$\mathrm{R}_\mathrm{limit} = \frac{\mathrm{λ}}{2\mathrm{NA}_\mathrm{system}}$$

In a standard microscopy system, one with a 4X 0.10NA lens illuminated by full-spectrum light, diffraction causes ‘airy-disks’ that prevents usable spatial data at a limit of 3.5-2.0µm/pixel. In a system of higher numerical aperture, one with a 40X 0.65NA lens and an identical sensor, the resolution limit becomes 538-307 nm/pixel. In order to bypass this spatial bandwidth constraint and obtain wide-field data with sub-micron resolution, an optical system must have low objective magnifications and high numerical apertures, a combination that is unachievable with modern lenses and sensors alone. In order to bypass the spatial resolution constraint, Pathware manipulates the following equation:

<!-- Numerical Aperture Equation -->
$$\mathrm{NA}_\mathrm{system} = \mathrm{NA}_\mathrm{lens} + \mathrm{NA}_\mathrm{illumination}$$

Altering the NA~illumination~ enables us to increase the numerical aperture of the system significantly, therefore increasing the final detail able to be resolved in such a system, simply by increasing the cone of light that makes up the final illumination angle. Pathware does this by sequencing a pattern of LEDs, thus far done in a 17x17 grid, and gathering a set of low-resolution microscopy images, each illuminated from a unique angle. They then take each image into Fourier space and super-resolve a final gigapixel image of the sample, creating a wide-field high-spatial bandwidth whole slide image.

!!! info "What is Whole Slide Imaging?"
    Whole slide imaging is an increasingly common technique to store pathology data. Digitization of tissues through imaging is a space-efficient but computationally heavy task, often requiring petabytes for major institutions and scan-times on the order of hours. Histology data, cut into thin sections and neatly preserved and stained, is a relatively simple and highly-utilized implementation of whole slide imaging. Cytology, with its hugely-variable focal plane and microscopic feature size, provides a greater challenge to implementing this sample-digitization process. New optical techniques are needed to digitize cytology: one that has a large depth-of-field, a wide field-of-view, and able to resolve the ultra-fine details that typical scanning lenses cannot.

[Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/Fourier_Ptychographic_Reconstruction_Simulation.mp4](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/Fourier_Ptychographic_Reconstruction_Simulation.mp4)

Fourier Ptychographic Reconstruction Simulation (Courtesy of [https://bit.ly/2QApnsg](https://bit.ly/2QApnsg))

### Blur Detection

---

Blur detection will act as a troubleshooting measure to be used as an “in-focus” check before stitching. The Laplacian is a 2-D isotropic measure of the second spatial derivative of an image. The Laplacian of an image highlights regions of rapid intensity change and is therefore often used for edge detection. The operator normally takes a single grayscale image as input and produces another grayscale image as output. ([https://goo.gl/fnPecj](https://goo.gl/fnPecj)). Since the input image is represented as a set of discrete pixels, Pathware needs to find a discrete convolution kernel that can approximate the second derivatives in the definition of the Laplacian. Two commonly used small kernels are…

[https://lh5.googleusercontent.com/jUZXXQl5Cak9CiYlynvyC70C-l9z2axwzk1L4iZ28ksryK6HOLT_AEd5XPaNwWxTyKdwErsP_BoHeBTM678j_0YD5e-B0rCWHTMTIpPCwoAGOURcSjzJdCByVZZC-vBCyly-j2AN](https://lh5.googleusercontent.com/jUZXXQl5Cak9CiYlynvyC70C-l9z2axwzk1L4iZ28ksryK6HOLT_AEd5XPaNwWxTyKdwErsP_BoHeBTM678j_0YD5e-B0rCWHTMTIpPCwoAGOURcSjzJdCByVZZC-vBCyly-j2AN)

[https://lh5.googleusercontent.com/eKui5lGOw7CwKQLqDVYrdREYVavYW6hn0myPtPSgBxeVR9nnuqJJr4TPYAqT-c66kuGT1IycCNqrJbPexxaUsxxnEH7PEIhFdp6IfCWFkQOVQZxSc2Vlmg3d6ygDbrpCxLi1lnTa](https://lh5.googleusercontent.com/eKui5lGOw7CwKQLqDVYrdREYVavYW6hn0myPtPSgBxeVR9nnuqJJr4TPYAqT-c66kuGT1IycCNqrJbPexxaUsxxnEH7PEIhFdp6IfCWFkQOVQZxSc2Vlmg3d6ygDbrpCxLi1lnTa)

Two commonly used discrete approximations to the Laplacian filter. (Note, Pathware has defined the Laplacian using a negative peak because this is more common; however, it is equally valid to use the opposite sign convention.) Using one of these kernels, the Laplacian can be calculated using standard convolution methods. The 2-D Laplacian of Gaussian (LoG) operator calculates the second spatial derivative of an image. This means that in areas where the image has a constant intensity (i.e. where the intensity gradient is zero), the LoG response will be zero. In the vicinity of a change in intensity, however, the LoG response will be positive on the darker side, and negative on the lighter side. This means that at a reasonably sharp edge between two regions of uniform but different intensities.

For implementation, You simply take a single channel of an image (presumably grayscale) and convolve it with the first matrix. And then take the variance (i.e. standard deviation squared) of the response. If the variance falls below a predefined threshold, then the image is considered blurry; otherwise, the image is not blurry. The reason that this method works is due to the definition of the Laplacian operator itself, which is used to measure the 2nd derivative of an image. The Laplacian highlights regions of an image containing rapid intensity changes, much like the Sobel and Scharr operators. And, just like these operators, the Laplacian is often used for edge detection. The assumption here is that if an image contains high variance then there is a widespread response, both edge-like and non-edge alike, representative, of a normal, in-focus image. But if there is very low variance, then there is a tiny spread of responses, indicating there are very little edges in the image. As we know, the more an image is blurred, the fewer edges there are.

### Image Stitching

---

To construct our image panoramas, we will utilize computer vision and image processing techniques such as keypoint detection and local invariant descriptors; keypoint matching; RANSAC; and perspective warping. Pathware’s panorama stitching algorithm consists of 5 steps:

Step #1: Detect keypoints (DoG, Harris, etc.) and extract local invariant descriptors (SIFT, SURF, etc.) from the two input images.

Step #2: Match the descriptors between the two images.

Step #3: Use the RANSAC algorithm to estimate a homography matrix using their matched feature vectors. Random sample consensus (RANSAC) is an iterative method to estimate parameters of a mathematical model from a set of observed data that contains outliers when outliers are to be accorded no influence on the values of the estimates. Therefore, it also can be interpreted as an outlier detection method.

Step #4: Apply a warping transformation using the homography matrix obtained from Step #3.

Step #5: Trim the unused pixels from the newly stitched image.

[https://lh6.googleusercontent.com/skAjfq5eR01almtZ8Kc1c57EhDHa8M5aI7vsxvp9rDxsKw0yIWP8MIeUZa2TaYXewSrpyG_FH9A1cdPHQvi5_LC3DM6lYD5y1JkI5QYKL9NAv0Qttkp5YF9rQ7Xpl0TuE7yETTMu](https://lh6.googleusercontent.com/skAjfq5eR01almtZ8Kc1c57EhDHa8M5aI7vsxvp9rDxsKw0yIWP8MIeUZa2TaYXewSrpyG_FH9A1cdPHQvi5_LC3DM6lYD5y1JkI5QYKL9NAv0Qttkp5YF9rQ7Xpl0TuE7yETTMu)

Lowe - Distinctive Image Features from Scale-Invariant Keypoints

The scale-invariant feature transform (SIFT) is an algorithm in computer vision to detect and describe local features in images. Lowe's method for image feature generation transforms an image into a large collection of feature vectors, each of which is invariant to image translation, scaling, and rotation, partially invariant to illumination changes and robust to local geometric distortion. Lowe used a modification of the k-d tree algorithm called the best-bin-first search method that can identify the nearest neighbors with high probability using only a limited amount of computation. Lowe rejected all matches in which the distance ratio is greater than 0.8, which eliminates 90% of the false matches while discarding less than 5% of the correct matches. To further improve the efficiency of the best-bin-first algorithm search was cut off after checking the first 200 nearest neighbor candidates. For a database of 100,000 key points, this provides a speedup over exact nearest neighbor search by about 2 orders of magnitude, yet results in less than a 5% loss in the number of correct matches. Lowe's SIFT-based object recognition gives excellent results except under wide illumination variations and under non-rigid transformations.

## Further Theory
[Advantages of Fourier Ptychography](detail/fpm-advantages.md)

[Engineering Considerations](detail/fpm-in-practice.md)

## Pathware Prototypes

### Resolution

Pathware has been able to employ FPM in the Bioptic prototype to reconstruct images with a resolution down to 0.2 micrometers per pixel (Philips, the current leader in the space is only able to achieve 0.25 micrometers per pixel). We proved this by taking an image of a US Air Force Target as seen in Figure A. The USAF uses these targets to calibrate their laser systems since the individual dashes are of a known thickness in a way similar to that of a ruler. Figure B shows the area in the center of the target that they have enhanced with their technique with the final result shown in Figure C. The smallest lines under region 9 are only 0.55 microns thick.

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/FA.png](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/FA.png)

Figure A

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/FB.png](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/FB.png)

Figure B

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/FC.png](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/FC.png)

Figure C

### Biological Reconstructions

#### Thyroid tissue

We were able to take a series of 2x magnification images and produce a 35x magnification image where cell membranes and nuclei are coming into focus. 

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/AOI1.png](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/AOI1.png)

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/AOI2.png](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/AOI2.png)

#### Cytological Specimens

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/raw_image.jpg](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/raw_image.jpg)

Raw Image

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/intensity_image.jpg](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/intensity_image.jpg)

Intensity Image

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/phase_image.jpg](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/phase_image.jpg)

Phase Image

#### Blood smears

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/raw_image%201.jpg](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/raw_image%201.jpg)

Raw Image

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/intensity_image%201.jpg](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/intensity_image%201.jpg)

Intensity Image

![Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/phase_image%201.jpg](Fourier%20Ptychography%2057d42776d82c495f99e2e413fb4fb2b1/phase_image%201.jpg)

Phase Image

[^1]:	
    Zheng G, Horstmeyer R, Yang C. Wide-field, high-resolution Fourier ptychographic microscopy. Nat Photonics 2013;7:739–45. https://doi.org/10.1038/nphoton.2013.187.

    Eckert R, Phillips ZF, Waller L. Efficient illumination angle self-calibration in Fourier ptychography. Appl Opt 2018;57:5434. https://doi.org/10.1364/AO.57.005434.

    Bian Z, Dong S, Zheng G. Adaptive system correction for robust Fourier ptychographic imaging. Opt Express 2013;21:32400. https://doi.org/10.1364/OE.21.032400.

    Zernike aberration polynomials n.d. URL: https://www.telescope-optics.net/zernike_aberrations.htm (Accessed 11 November 2019).
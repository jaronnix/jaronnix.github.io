# Engineering Considerations

### Pixel Intensity

In image processing, normalization is a process that changes the range of pixel intensity values. Applications include photographs with poor contrast due to glare, for example. Normalization is sometimes called contrast stretching or histogram stretching. In more general fields of data processing, such as digital signal processing, it is referred to as dynamic range expansion.

[IMAGE?]

Left: 40% decrease in gray scale intensity values, Center: Original Image, Right: 40% increase in gray scale intensity values

The purpose of dynamic range expansion in the various applications is usually to bring the image, or other type of signal, into a range that is more familiar or normal to the senses, hence the term normalization. Often, the motivation is to achieve consistency in dynamic range for a set of data, signals, or images to avoid mental distraction or fatigue. For example, a newspaper will strive to make all of the images in an issue share a similar range of grayscale. The linear normalization of a grayscale digital image is performed according to the formula:

$$I_N = (I - Min)\frac{newMax-newMin}{Max-Min}+newMin$$

For example, if the intensity range of the image is 50 to 180 and the desired range is 0 to 255 the process entails subtracting 50 from each of pixel intensity, making the range 0 to 130. Then each pixel intensity is multiplied by 255/130, making the range 0 to 255.

Normalization might also be non linear, this happens when there isn't a linear relationship between ***I*** and I(N)

### LED Positioning (including Defocus)

Small changes in angle become large when they are propagated to large defocus depths, leading to reduced resolution and reconstruction artifacts. For example, using a well-aligned LED array will be unable to reconstruct high-resolution features of a resolution target defocused beyond 30 μm due to angle misalignment. Using the same data set, implementation of a self-calibration algorithm allows for reconstruction of high-resolution features even when there is up to 70 μm off-focus.

[IMAGE?]

Adapted from Waller, et al. Even small calibration errors degrade FPM resolution severely when defocus distances are large. Experimental schematic for a USAF target placed at varying defocus distances.

Because iterative angle estimation (including SC calibration) unfeasibly increases the computational complexity of FPM, only bright field calibration is necessary.

[IMAGES?]

### LED Intensity Fluctuations

One of major systematic noises in FP settings comes from the illumination uncertainty of the
multiple LED elements, a counter problem to the positional uncertainty in conventional
ptychography settings. Specifically, this challenge comes from four aspects: 1) illumination
intensities and incident angles of different LED elements are all different. We need to
calibrate the intensities of different LED elements and measure their angular emission
characteristics. 2) We also need to characterize the angular response of the light-collecting
optics as well as the pixel point-spread-function of the image sensor. 3) In wide field-of-view settings, illumination intensity varies spatially across the entire field-of-view. Such spatial variations are also different for different LED elements. 4) Illumination intensities of different LED elements behave differently over time. In our FP prototype, we observe ~40% intensity drift for certain LED elements, over a time period of several hours. Note that, it is possible to alleviate the illumination uncertainty problem by developing a sophisticated calibration procedure with real-time intensity monitoring setups and associated time-synchronized electronics. However, this may require a substantial amount of maintenance efforts. As a result, adaptive system correction for FPM  involves the evaluation of an image-quality metric at each iteration step, followed by the estimation of an improved system correction. This optimization process is repeated until the image-quality metric is maximized.

[IMAGE?]

The flow chart of the adaptive Fourier ptychographic algorithm for intensity correction.

### Aberration Correction

Generally, the aberrations in an optical system can be decomposed into a set of Zernike polynomials, each with a different coefficient. Introduced by the Dutch scientist Fritz Zernike (Nobel prize laureate for the invention of phase-contrast microscope) in 1934, these polynomials can be applied to describe mathematically 3D wavefront deviation from what can be constructed as a plane - i.e. unit circle - of its zero mean, defined as a surface for which the sum of deviations on either side - opposite in sign one to another - equals zero. Each polynomial describes specific form of surface deviation; their combined sum can produce a large number of more complex surface shapes, that can be fit to specific forms of wavefront deviations (aberrations). In principle, by including sufficient number of Zernike polynomials (commonly referred to as terms), any wavefront deformation can be described to a desired degree of accuracy.

The usual way of applying Zernike terms is to the specific wavefront shape, which is "decomposed" to a needed number of terms in order to determine:

1. The main forms of contributing deviations, and

2. The overall magnitude of deformation

For simple aberration forms, such as pure Siedel aberrations, a single polynomial suffices. Describing more complex aberrations, such as, for instance, seeing error, as well as wavefronts formed by actual (i.e. imperfect) surfaces, requires an expanded set of Zernike polynomials.

Zernike polynomials define deviations from zero mean as a function of the radial point height ρ in the unit-radius circle and its angular circle coordinate θ, which is the setting of a microscope exit pupil, in which the wavefront form is evaluated. In polar and Cartesian coordinates, respectively, the radial component is ρ² = x² + y², with 0 ≤ ρ, x, y ≤ 1. The common convention for the angular coordinate θ varies with the field; in ophthalmology, it is counterclockwise from x+ toward y+ axis (OSA recommended), thus ρ = x/cosθ = y/sinθ. In general optics, it is often different. Malacara's convention is clockwise from y+ to x+ axis, thus ρ = x/sinθ = y/cosθ, and Mahajan's convention (Optical imaging and aberrations) applied here to the conventional aberration functions is counterclockwise from y+ to x-, hence with the same radial-to-angular relations as Malacara's. The polynomials are orthogonal (i.e. their values change independently) over the circle of unit radius. Due to this attribute, these aberration forms are termed orthogonal, or Zernike aberrations.

[ABBERATION CORRECTION IMAGE]

As mentioned, zero mean is defined as a surface for which the sum of wavefront deviations to either side is zero. That is important conceptual difference vs. standard wavefront error, which expresses deviations from a reference sphere (also commonly constructed as a circle). Hence the polynomial, which is a product of its radial variable in `ρ` and angular variable in `θ`, has zero value at the intersection of the wavefront and its zero mean. Zero mean differs from the reference sphere for balanced primary spherical aberration and defocus, while coinciding with it for balanced primary astigmatism. coma and balanced 6th/4th order spherical. As a result, the form of polynomial is different from the classical aberration function for the former three, while identical (except for the normalization factor) for the latter two.

The polynomial normalization factor fulfils the formal requirement that the radial polynomial portion equals 1 for ρ=1. For instance, the deviation from zero mean for primary spherical aberration – whose polynomial only has the radial component – is given by ρ4-ρ2+1/6; thus, its normalization factor is 6, and the corresponding Zernike circle polynomial is 6ρ4-6ρ2+1 (this normalization to unit radius shouldn't be confused with normalization to unit variance, described ahead).

Orthogonality of Zernike polynomials creates the possibility to combine as many different surfaces as needed to approximate the form of wavefront deviation with desired accuracy. It allows expressing separate contributions of various forms of aberrations - including any chosen extent of the higher order forms - and obtaining the combined variance as the sum of individual aberration variances. Also, the polynomials can be - and routinely are - scaled to unit variance over the circle radius for all aberration forms, so that their combined form can be determined directly by adding up their expansion coefficients, which determine the specific magnitude for each aberration form. Wavefront is described as a sum of Zernike aberration terms.

[Zernike Wavefront Figure](Engineering%20Considerations%202fe1edd9c3174398963c77873da67323/Zernike%20Wavefront%20Figure%20ebf578c1f0d745d2ace1f00ed8fb8481.md)

In the nutshell, the normalization factor N is chosen so that a product of the sum of two extreme values of the polynomial (absolute values, determining the relative magnitude of P-V deviation) and normalization factor equals the P-V-to-RMS wavefront error ratio for the aberration. Hence, multiplying this product with the expansion coefficient - which equals the RMS error for given aberration-yields the P-V wavefront error corresponding to the coefficient. For any value of the polynomial for given pupil coordinate ρ, a product with the normalization factor and expansion coefficient yields, as already mentioned, the wavefront deviation from zero mean for that particular pupil coordinate. As with the standard aberrations, the wavefront error, either P-V (as a direct optical path difference) or RMS, is directly related - although not necessarily identical - to the phase error. The absolute value of Zernike expansion coefficient z(nm) is identical to the RMS wavefront error; since the coefficient does express positive and negative deviations, the sum of coefficients for all Zernike terms used to fit particular wavefront gives its overall RMS wavefront error (i.e. standard deviation), and its square equals the wavefront variance.

[Aberration Reconstruction Figure](Engineering%20Considerations%202fe1edd9c3174398963c77873da67323/Aberration%20Reconstruction%20Figure%206ae4ce5d73ae423aa47a543697d175a2.md)
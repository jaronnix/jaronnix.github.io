# Advantages of Fourier Ptychography

### Implementation

FPM can be easily implemented on a conventional optical microscope by replacing the single illumination source with an LED array. Using only bright-field illumination, optical resolution can be improved by a factor of 2. On the other hand, even greater optical resolution can be achieved by including dark-field images in the iterative reconstruction process.

### Enhanced Nyquist Sampling

The Nyquist (Sampling) Theorem is a principle that engineers follow in the digitization of analog signals. For conversion from analogy to digital to result in an accurate reproduction fo the signal, slices (or samples) of the analog waveform must be taken frequently. The number of samples taken per second is called the sampling rate (or sampling frequency).

Any analog signal consists of (wave) components at various frequencies. In the simplest case, a sine wave concentrates all of the signal energy into a single frequency. However, analog signals usually consist of complex waveforms, with (wave) components at several frequencies. The highest frequency component in an analog signal determines the bandwidth of that signal. As a result, the higher the sampling frequency, the greater the bandwidth (holding all other factors constant).

Optical engineers use a concept called space-bandwidth product (SBP) to characterize the total resolvable pixels of an imaging system. By quantifying the combination of resolution and FOV by the SBP, engineers are calculating the number of pixels required to capture the full area at full resolution. In other words, this is just the FOV divided by the pixel size required to achieve Nyquist sampling at the resolution of the image.

### Solution to a Limited Space-Bandwidth Product

In conventional microscopy, the SBPs of most off-the-shelf (OTS) objective lenses are around ~10 megapixels (MP). While 10 MP is reasonable for many applications, this resolution falls short of the gigapixel (GP) resolution needed for many biological applications. Ideally, an engineer could simply create a larger lens to increase the SBP. However, geometrical aberrations associated with the lens also scale up as the size of the lens increases. To solve this issue, one would need to introduce more optical surfaces to increase the degrees of freedom in lens optimization. These measures would complicate lens alignment and would be too costly for use in conventional microscopes.

Furthermore, low magnification objective tend to perform much better than high magnification objectives at transmitting large amounts of information. The SBP scales as NA²/M², and the magnification (M) goes up faster than the NA for high magnification lenses. In other words, most cameras do not have the resolution (pixel size) to capture all of the information passed by the low magnification objectives. So this extra magnification is needed to use the full resolution of a diffraction-limited lens. Second, current cameras do not have the necessary resolution to utilize the full resolution and full FOV of most objectives. To solve this issue, a camera would need to have very small pixels (~1.5-3 MP) and collect data at very high data throughput (~4 GP/s). All of these SBP-related issues can be solved by simply stitching low resolution, large FOV images together in Fourier space.
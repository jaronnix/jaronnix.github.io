# Automated Adequacy Assessment

[AARON NEEDS TO EDIT]

Adequacy of a Fine Needle Aspiration is generally defined as identifying 6 clumps of 10 nucleated cell clusters. Pathware will go about identifying these clusters by combining a series of established Computer Vision techniques to localize cells across the whole slide image.

**Stage 1**: Identify nucleated cells with Fast Radial Symmetry (FRS). FRS is a well established technique in computer vision processing and has been shown to identify upwards of 99.8% of all nucleated cells in histology slides. In Pathware’s limited tests on blood smears, they have been able to identify 100% of nucleated cells present on the slide.

[https://lh5.googleusercontent.com/OH4QJaYoCp7tVWdRrR6ZA9nB-_mRurr-4NFhVbr26a6gV2me0kCoZ1OSR4lwIFl7-_Qo8iqJ2OxuL7ffwDeZOA8l93_0iPjVU7ewUCn596_CKNtWETi0MJl4_qBsQk3r-o1k9Uk4](https://lh5.googleusercontent.com/OH4QJaYoCp7tVWdRrR6ZA9nB-_mRurr-4NFhVbr26a6gV2me0kCoZ1OSR4lwIFl7-_Qo8iqJ2OxuL7ffwDeZOA8l93_0iPjVU7ewUCn596_CKNtWETi0MJl4_qBsQk3r-o1k9Uk4)

**Stage 2**: Identify cell clusters with k-means ++. Pathware first built this algorithm off of randomly generated points to simulate the random nature of the biological sample. Proof of these tests can be found above. They then tested its effectiveness on histology samples with great success as seen in the image below.

[https://lh4.googleusercontent.com/dT27xlFrdK0d2Puo68g6qzioc_pfiPZuPu-DRCb1-h1VCDkS-HBDhjlo07yjNbUlhMbrzueljGt3Nl7DiWdU7XLjMiii9cl3CdWYnR7KIZOMwtu_jn2g4sMfYCles_gNX4VRpogv](https://lh4.googleusercontent.com/dT27xlFrdK0d2Puo68g6qzioc_pfiPZuPu-DRCb1-h1VCDkS-HBDhjlo07yjNbUlhMbrzueljGt3Nl7DiWdU7XLjMiii9cl3CdWYnR7KIZOMwtu_jn2g4sMfYCles_gNX4VRpogv)

**Stage 3**: Rank clusters by cell density and cluster of cluster counts. Pathware is using these metrics when looking for regions of interest to present to the clinician in an interactive graphical user interface. Proof of the algorithm’s functionality is displayed below with the GUI walkthrough incorporated into Appendix K.

[https://lh5.googleusercontent.com/bxJhVVVMYg_B252aPMdyQE5Ic_D0gyUiBtEn4ox5OhL7MwunZqQjEJXNT_nJirhVZ77dx16NzpYEaLnlxgxynvXpyXFYkzYwAzb-PBWK5ekPjti7OnMamQC4z6FXS0QMo6Hu0yl5](https://lh5.googleusercontent.com/bxJhVVVMYg_B252aPMdyQE5Ic_D0gyUiBtEn4ox5OhL7MwunZqQjEJXNT_nJirhVZ77dx16NzpYEaLnlxgxynvXpyXFYkzYwAzb-PBWK5ekPjti7OnMamQC4z6FXS0QMo6Hu0yl5)

## Computer Vision (Current)

### Fast Radial Symmetry Detection With Affine Transform

([https://goo.gl/e2nz6Z](https://goo.gl/e2nz6Z))

The fast radial symmetry (FRS) transform has been very popular for detecting interest points based on local radial symmetry. Although FRS delivers good performance at a relatively low computational cost and is very well suited for a variety of real-time computer vision applications, it is not invariant to perspective distortions. The inclusion of an affine transformation improves the overall accuracy of cell identification. FRS utilizes local radial symmetry to highlight points of interest within a scene. Its low-computational complexity and fast runtimes make this method well-suited for real-time vision applications. The performance of the transform is demonstrated on a wide variety of images and compared with leading techniques from the literature. Both as a facial feature detector and as a generic region of interest detector the new transform is seen to offer equal or superior performance to contemporary techniques at a relatively low computational cost. Previous methods: require the gradient to be quantized into angular bins, the contribution of every orientation is computed in a single pass over the image. Pathware’s new method works well with a general fixed parameter set, however, it can also be tuned to exclusively detect particular kinds of features The approach presented herein determines the contribution each pixel makes to the symmetry of pixels around it, rather than considering the contribution of a local neighborhood to a central pixel.

### K-Means ++ Clustering

---

([https://bit.ly/2st6KeH](https://bit.ly/2st6KeH))

K-means clustering is one of the simplest and popular unsupervised machine learning algorithms. Typically, unsupervised algorithms make inferences from datasets using only input vectors without referring to known, or labeled outcomes. The means in the K-means refers to averaging of the data; that is, finding the centroid within a set of clustered. A cluster refers to a collection of data points aggregated together because of certain similarities. Usually referred to simply as “k-means,” Lloyd’s algorithm begins with k arbitrary “centers,” typically chosen uniformly at random from the data points. Each point is then assigned to the nearest center, and each center is recomputed as the center of mass of all points assigned to it. These last two steps are repeated until the process stabilizes. One can check that φ is monotonically decreasing, which ensures that no configuration is repeated during the course of the algorithm. Since there are only kn possible clusterings, the process will always terminate. K-Means ++ differs from traditional K-Means methods by utilizing a more intuitive selection of initial centroids, leading to improved cluster definition that is O(log k)-competitive with the optimal clustering, as well as considerable increases in speed and accuracy. This improved algorithm achieves greater initialization by using first choosing an initial center c1 uniformly at random from data subset, X. Then, the vector containing the square distances between all points in the dataset is computed. Second, a second center c2 is chosen from an additional subsection of data, X, randomly drawn from the probability distribution. Third, the distance vector is recomputed. Fourth, a successive center c1 is chosen and the distance vector is recomputed. Finally, when exactly k centers have been chosen, the initialization phase is finalized and proceeds with the standard k-means algorithm. If the minimum required value of K ≥ 6 is not met with a total of 10 points within a radial distance of D from the centroid, then the sample will be deemed inadequate.

Below you will find three examples of their functional K-Means algorithm operating on 1,000 data points. The black dots represent randomly generated points comprising 8-10 clusters with each red dot representing an incorrect approximation and each green dot representing the central point of the cluster after 1-2 iterative approximations. This process was completed in less than 0.5 seconds and is easily scalable to meet the needs of assessing a whole slide image.

[https://lh4.googleusercontent.com/gChmJRHTsx9e9HZNgMQgNk_6I2vo0sx1tBwkO8gKdd42K1Gq0HGdkv-VxKT3Fsg4t-OMsz1e_dg5xaMq3n5FqFU-Ah1NN3O90ti_6x4WhdZpoCuX1YJdLRK1hFt52bO-N6bkZFhI](https://lh4.googleusercontent.com/gChmJRHTsx9e9HZNgMQgNk_6I2vo0sx1tBwkO8gKdd42K1Gq0HGdkv-VxKT3Fsg4t-OMsz1e_dg5xaMq3n5FqFU-Ah1NN3O90ti_6x4WhdZpoCuX1YJdLRK1hFt52bO-N6bkZFhI)

[https://lh4.googleusercontent.com/QVPuPiP_eEv6FpWo0Pt0wbV3QU4iEM-xzBF6uz1NgIEPybyyLAPiGQEqk2rudaKdSRam_Pc5Kk6uUlQmzpQsvJknsedCbep9wG_hvIXAwoyJmoJ79-W7vzkO9g8Ptq8hKk6D9Bqa](https://lh4.googleusercontent.com/QVPuPiP_eEv6FpWo0Pt0wbV3QU4iEM-xzBF6uz1NgIEPybyyLAPiGQEqk2rudaKdSRam_Pc5Kk6uUlQmzpQsvJknsedCbep9wG_hvIXAwoyJmoJ79-W7vzkO9g8Ptq8hKk6D9Bqa)

[https://lh6.googleusercontent.com/tjOn43x8KrVeMsPpPc3ej3uYBZMgZLLBRCw5F45A00vuEl2Ty2e-KdMlg-ctLegMX92gQqsEsbHn1u-H4uFc7ov8BBUmH5mFfNiNw012R3Ve90mRZCbHRgR3FFuXbKw7iW0oLk2s](https://lh6.googleusercontent.com/tjOn43x8KrVeMsPpPc3ej3uYBZMgZLLBRCw5F45A00vuEl2Ty2e-KdMlg-ctLegMX92gQqsEsbHn1u-H4uFc7ov8BBUmH5mFfNiNw012R3Ve90mRZCbHRgR3FFuXbKw7iW0oLk2s)

Parameters governing K-Means ++ clustering

1. The number of Data Points (N): Convert the matrix of data points, representing the location of nuclei, into a total number of points. These points are divided into subsections based on the number of clusters pre-defined by the Pham method for calculation of K and iteratively determined subsections using a probability distribution algorithm.

2. Number of Clusters (K): The Pham method for calculation of K uses the value of f(K), the ratio of the real distortion to the estimated distortion. The smaller that f(K) is, the more concentrated is the data distribution. Thus, values of K that yield small f(K) can be regarded as giving well-defined clusters. In addition, f(K) values close to 1 represent a uniform distribution of the data.

3. Convergence: The centroid location is optimized by reducing the in-cluster sum of squares. Convergence is reached when the centroids have stabilized — there is no change in their values because the clustering has been successful, or the defined number of iterations has been achieved.

## Computer Vision (Future)

### Nuclear-Cytoplasmic Ratio

---

The nuclear-cytoplasmic ratio (also variously known as the nucleus:cytoplasm ratio, nucleus-cytoplasm ratio, N:C ratio, or N/C) is a measurement used in cell biology. It is a ratio of the size (i.e., volume) of the nucleus of a cell to the size of the cytoplasm of that cell. The N:C ratio indicates the maturity of a cell, because as a cell matures the size of its nucleus generally decreases. So, for example, "blast" forms of erythrocytes, leukocytes, and megakaryocytes start with an N:C ratio of 4:1 , which decreases as they mature to 2:1 or even 1:1 (with exceptions for mature thrombocytes and erythrocytes, which are anuclear cells, and mature lymphocytes, which only decrease to a 3:1 ratio and often retain the original 4:1 ratio). An increased N:C ratio is commonly associated with precancerous dysplasia as well as with malignant cells. The N:C ratio is a better predictor of malignancy than increased nuclear size.

[https://lh6.googleusercontent.com/cJWg2aD9O6NppE2I83KZyzUi3x2m-InJhgEEUFuoJAu-NP-LtWzEbwx_ObelZLKLT3P-sXawzioePr4mSDb3aushCR0BRIS1PukBmUK39mk6f1uf_YjGcnqgAuZBU96nVGyZ4iba](https://lh6.googleusercontent.com/cJWg2aD9O6NppE2I83KZyzUi3x2m-InJhgEEUFuoJAu-NP-LtWzEbwx_ObelZLKLT3P-sXawzioePr4mSDb3aushCR0BRIS1PukBmUK39mk6f1uf_YjGcnqgAuZBU96nVGyZ4iba)

Nuclear-Cytoplasmic ratio visual

---

[https://lh6.googleusercontent.com/Rrk97HgVK9-YSxGcXawxq2-jvtkNtxCzzM8awdkt1l74xMMnPiQbH1_GLOiCvfBeOJD_ZKrJyubCRQk2ceIbsxerpARU5hdXH2wgm2Q3fhUm4ozfPnoTPNNZbLYe2xc37SEKXNNa](https://lh6.googleusercontent.com/Rrk97HgVK9-YSxGcXawxq2-jvtkNtxCzzM8awdkt1l74xMMnPiQbH1_GLOiCvfBeOJD_ZKrJyubCRQk2ceIbsxerpARU5hdXH2wgm2Q3fhUm4ozfPnoTPNNZbLYe2xc37SEKXNNa)

Red outlined cells (left) have been analyzed for N/C ratio (right)

[https://lh6.googleusercontent.com/cpoPH7kGsnh_-o6tIfT4ewSb6QiZTIqecSfTNQdFl0bb3YNTYwHuYRK4Vqtiz0AujPqDRX5by_XAzqGrQ23UaxuM3qu3HDfz7tiD8GfAJng05dIEZc3iuTCCQFoJ4HD4mSBKXsRz](https://lh6.googleusercontent.com/cpoPH7kGsnh_-o6tIfT4ewSb6QiZTIqecSfTNQdFl0bb3YNTYwHuYRK4Vqtiz0AujPqDRX5by_XAzqGrQ23UaxuM3qu3HDfz7tiD8GfAJng05dIEZc3iuTCCQFoJ4HD4mSBKXsRz)
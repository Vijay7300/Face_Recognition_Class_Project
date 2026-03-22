# Face_Recognition_Class_Project

#  Face Morphing using PCA and Probabilistic Optimization

## 📖 Overview
This project implements **face morphing using Principal Component Analysis (PCA)**, combined with an advanced **probabilistic optimization strategy** to generate smooth and realistic transitions between faces.

The system uses the **ORL (AT&T) Face Dataset** and transforms images into a lower-dimensional latent space using eigenfaces. Morphing is performed in this latent space and reconstructed back to image space.

##  Key Highlights
* PCA-based **Eigenface computation using SVD**
* Face morphing via:
  * Linear interpolation (baseline)
  * Probabilistic interpolation (optimized)
* Automatic **optimal PCA component (k) selection**
* Quantitative comparison using multiple metrics
* GIF generation for visual analysis

# Dataset

* Dataset: **ORL (AT&T) Face Dataset**
* Contains:
  * 40 subjects
  * 10 images per subject
* Images are:
  * Grayscale
  * Resized to 64×64

## Methodology

### 1. Data Preprocessing
* Convert images to grayscale
* Resize to **64×64**
* Flatten into vectors
* Construct data matrix ( X \in \mathbb{R}^{m \times n} )

### 2. PCA using SVD
* Mean-center the dataset
* Compute:
  * Eigenfaces (principal components)
  * Singular values
* Reduce dimensionality using top **k components**

### 3. Face Morphing

#### 🔹 Linear Morphing (Baseline)
* Interpolate between two latent vectors:
  [
  z_t = (1 - t) z_A + t z_B
  ]

#### 🔹 Probabilistic Morphing (Optimized)
* Add structured noise based on covariance:
  * Improves diversity
  * Produces more natural transitions


### 4. Optimization of k
* Grid search over values of k
* Objective balances:
  * Reconstruction Error (MSE)
  * Morph Smoothness

### 5. Evaluation Metrics
* **Reconstruction MSE**
* **Smoothness Variance**
* **Sharpness (Laplacian Energy)**
* **SSIM (Structural Similarity Index)**

##  Results

| Method              | Reconstruction | Smoothness | Sharpness | SSIM   |
| ------------------- | -------------- | ---------- | --------- | ------ |
| Naive PCA Morph     | Good           | Moderate   | Moderate  | High   |
| Probabilistic Morph | Good           | Better     | Better    | Higher |

* Probabilistic method produces **more realistic transitions**
* Statistical validation using **paired t-test**


##  Output Examples

###  Linear Morphing
* Smooth interpolation between two faces
* Deterministic transitions

###  Probabilistic Morphing
* Adds controlled randomness
* More natural and diverse transitions
Generated outputs:
* `morph_linear_example.gif`
* `morph_prob_example.gif`


## Tech Stack
* Python
* NumPy
* OpenCV
* SciPy
* Matplotlib
* ImageIO
* Scikit-image

##  Experimental Analysis
* Multiple face pairs evaluated
* Metrics aggregated across morph sequences
* Statistical significance validated using **paired t-test**


##  Future Improvements
* Use Variational Autoencoders (VAE)
* Integrate GAN-based morphing
* Real-time face morphing application
* Extend to color images

##  How to Run

1. Clone the repository
   
```bash
git clone <repo-link>
cd <repo-name>
```

2. Install dependencies

```bash
pip install numpy scipy matplotlib opencv-python imageio scikit-image
```

3. Run the notebook/script

```bash
python main.py
```


##  Conclusion
This project demonstrates how classical PCA can be extended with **probabilistic modeling and optimization techniques** to achieve high-quality face morphing. It bridges the gap between traditional linear methods and modern generative approaches.


## Acknowledgements
* AT&T ORL Face Dataset
* Scientific Python ecosystem

---

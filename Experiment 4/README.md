# Experiment 4: Image Recognition and Classification with Keras in R

**Author:** Samarth Burkul  
**Roll Number:** 24102c2004  
**Course:** R Programming Lab  
**Topic:** Deep Learning Pipeline Implementation and Version Control  

---

## 🎯 Overview & Objectives

This project establishes an end-to-end deep learning pipeline for binary image classification using R. Leveraging packages like `keras` (with TensorFlow backend) and `EBImage`, it showcases R's capability in computer vision and artificial neural networks. The complete workflow spans from raw image ingestion and tensor preprocessing to multi-layer model architecture design, training, and performance evaluation.

---

## 🔍 Problem Statement

The goal is to design and train an Artificial Neural Network (ANN) capable of distinguishing between two distinct image classes (labeled as **"p"** and **"c"** categories). 

Key technical requirements include:
- Loading raw image files from the filesystem into memory.
- Standardizing image resolutions and flattening multidimensional tensors into feature vectors.
- Splitting the dataset into appropriate training and testing subsets.
- Applying one-hot encoding to target labels.
- Constructing, compiling, and optimizing a Sequential Deep Neural Network in Keras.
- Assessing classification accuracy using confusion matrices and prediction probability analysis.

---

## 📊 Dataset Specifications

- **Total Samples:** 12 images organized in the `images/` directory.
- **Classes:** 2 categories with 6 samples each (`p1.jpg`–`p6.jpg` and `c1.jpg`–`c6.jpg`).
- **Partition:** 10 samples utilized for model training (5 per category) and 2 held-out samples for testing (1 per category).
- **Image Transformation:** Each image is resized to a uniform dimension of **28 × 28 pixels** across 3 RGB color channels, resulting in a flattened feature input vector of 28 × 28 × 3 = 2352 numerical values.

---

## 🛠️ Required Libraries & Tools

| Package / Library | Source | Functionality |
|---|---|---|
| `EBImage` | Bioconductor | Image processing, resizing, and array transformation |
| `keras` / `tensorflow` | CRAN / PyPI | Neural network construction, training, and evaluation |
| `BiocManager` | CRAN | Package manager for Bioconductor dependencies |

---

## ⚙️ Step-by-Step Implementation Workflow

1. **System & Dependency Initialization**  
   Configures Python virtual environments and installs `EBImage`, `keras`, and TensorFlow backend dependencies.
2. **Image Data Ingestion**  
   Iteratively loads the 12 JPG images from the `images/` subfolder into an R list structure using `readImage()`.
3. **Dimensional Scaling & Reshaping**  
   Standardizes all loaded image matrices to 28 × 28 × 3 via `resize()` and `array_reshape()`.
4. **Data Partitioning**  
   Constructs the training matrix `trainx` (10 samples) and evaluation set `testx` (2 samples), accompanied by target labels `trainy` and `testy`.
5. **Categorical Target Encoding**  
   Encodes the binary target arrays into categorical one-hot matrices using `to_categorical()`.
6. **Network Architecture Configuration**  
   Builds a Sequential Neural Network containing:
   - Dense hidden layer (256 units, ReLU activation, input dimension = 2352)
   - Dense hidden layer (128 units, ReLU activation)
   - Dense output layer (2 units, Softmax activation)
7. **Compilation & Optimization**  
   Compiles the model utilizing `categorical_crossentropy` as the loss function, `RMSprop` optimizer, and `accuracy` scoring metric.
8. **Model Fitting**  
   Trains the neural network over 30 epochs with a batch size of 32 and a 20% internal validation split.
9. **Inference & Quantitative Evaluation**  
   Generates class probability distributions and evaluates prediction performance using a cross-tabulated confusion matrix.

---

## 🚀 How to Run

1. **Clone the repository:**
   ```bash
   git clone https://github.com/SamarthBurkul/R-Programming-Lab.git
   cd "Experiment 4"
   ```

2. **Open the Notebook:**
   Launch `RProg_Experiment_4_24102c2004.ipynb` in **Google Colab** (with GPU acceleration enabled) or a local **Jupyter Notebook / RStudio** instance with R kernel support.

3. **Verify Directory Structure:**
   Ensure the `images/` folder containing the dataset is located in the working directory.

4. **Execute Pipeline:**
   Execute all cells sequentially from top to bottom. The setup cell will automatically configure the required packages and TensorFlow runtime.

---

## 📈 Key Findings & Results

- **Model Parameters:** Total trainable parameters: ~635,522 across three dense layers.
- **Convergence:** The network rapidly minimizes cross-entropy loss over 30 epochs.
- **Classification Output:** The model outputs probability vectors for each sample, successfully mapping images to their true class labels.

---

## 📁 Folder Structure

```
Experiment 4/
├── RProg_Experiment_4_24102c2004.ipynb   # Main R notebook containing implementation
├── images/                               # Image dataset (p1-p6, c1-c6)
└── README.md                             # Experiment documentation
```

---

## 👨‍💻 Student Details

- **Name:** Samarth Burkul  
- **Roll Number:** 24102c2004  
- **Repository:** [R-Programming-Lab](https://github.com/SamarthBurkul/R-Programming-Lab)

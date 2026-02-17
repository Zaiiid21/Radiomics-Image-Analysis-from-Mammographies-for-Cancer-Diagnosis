# Mammographic Image Analysis Project

A biomedical image analysis project focused on classifying mammograms as normal or malignant using radiomics-based feature extraction.

## Project Overview

This project applies advanced image analysis techniques to the MIAS (Mammographic Image Analysis Society) MiniMammographic Database for the classification of breast tissue as normal or containing malignant spectra. The analysis leverages PyRadiomics for comprehensive feature extraction from mammographic images.

## Dataset

The project utilizes the **MIAS MiniMammographic Database**, a well-established benchmark dataset in medical imaging research featuring:

- **Resolution**: 1024 × 1024 pixels at 200 micron pixel edge spacing
- **Original Source**: Digitized from the original 50 micron MIAS Database
- **Classification**:
  - **Normal**: 16 normal breast tissue samples
  - **MalignantSpec**: 8 malignant spectra samples

### Image Samples

- **[Normal/](Normal/)** - Normal breast tissue mammograms
- **[MalignantSpec/](MalignantSpec/)** - Malignant specimen mammograms

## Project Structure

```
├── Normal/                          # Normal breast tissue images
├── MalignantSpec/                   # Malignant specimen images
├── EXTRACTION/                      # Processed images and extracted features
│   ├── *_clean.jpg                 # Cleaned/preprocessed images
│   └── *_thr.jpg                   # Thresholded images
├── pyradiomics-master/              # PyRadiomics library for feature extraction
├── Legend.txt                       # MIAS database documentation
├── DataTypes.xlsx                   # Data classification spreadsheet
├── Radiomics PW.pdf                 # Radiomics methodology presentation
└── AIB_FinalProject_Paul_Pau_Alvaro_Zaid.pdf  # Final project report
```

## Features

### Image Preprocessing
- Image cleaning and noise reduction
- Thresholding for region of interest (ROI) segmentation
- Conversion to standardized formats for analysis

### Radiomics Feature Extraction
Utilizing PyRadiomics, the project extracts a comprehensive set of quantitative features including:

- **First-order statistics**: Mean, median, standard deviation, min/max values
- **Shape-based features**: Compactness, sphericity, surface area
- **Texture analysis**: Gray Level Co-occurrence Matrix (GLCM), Gray Level Run Length Matrix (GLRLM)
- **Wavelet-based features**: Multi-scale texture analysis

## Technologies Used

- **Python** - Primary programming language
- **PyRadiomics** - Radiomic feature extraction library
- **Image Processing**: PIL/Pillow for image handling
- **Data Processing**: NumPy, Pandas for numerical computation
- **Machine Learning**: Compatible with scikit-learn for classification

## Dependencies

### Core Requirements
- Python 3.7+
- PyRadiomics
- NumPy
- Pandas
- Pillow (PIL)
- SimpleITK

### Development
See `requirements.txt` in the PyRadiomics folder for complete dependency specifications.

## Installation & Setup

1. **Clone or extract the project**:
   ```bash
   cd "d:\EGBM\3º\2n Trimestre\Análisis Imagen Biomédica\Group project"
   ```

2. **Install PyRadiomics**:
   ```bash
   cd pyradiomics-master
   pip install -e .
   ```

3. **Install additional dependencies**:
   ```bash
   pip install numpy pandas pillow scikit-learn
   ```

## Usage

### Basic Feature Extraction Example

```python
from radiomics import featureextractor
import SimpleITK as sitk

# Initialize feature extractor
extractor = featureextractor.RadiomicsFeatureExtractor()

# Load image and mask
image = sitk.ReadImage('path/to/image.nrrd')
mask = sitk.ReadImage('path/to/mask.nrrd')

# Extract features
result = extractor.execute(image, mask)
```

### Batch Processing

See examples in `pyradiomics-master/examples/` for batch processing workflows:
- `batchprocessing.py` - Single-threaded batch processing
- `batchprocessing_parallel.py` - Parallel processing for multiple images

## Project Objectives

1. Extract radiomics features from mammographic images
2. Compare feature distributions between normal and malignant samples
3. Identify discriminative features for classification
4. Build a classification model to distinguish between tissue types
5. Evaluate model performance and clinical applicability

## Results & Analysis

Feature extraction results are stored in the `EXTRACTION/` folder:
- Processed images show the preprocessing pipeline effectiveness
- Feature vectors enable statistical comparison between classes
- Classification performance metrics documented in the final project report

## References

- Suckling, J., et al. (1994). "The Mammographic Image Analysis Society Digital Mammogram Database." *Exerpta Medica. International Congress Series*, 1069, 375-378.
- Van Griethuysen, J. J., et al. PyRadiomics: Radiomics Package for Python. Retrieved from https://github.com/Radiomics/pyradiomics
- PyRadiomics Documentation: https://pyradiomics.readthedocs.io/

## Team Members

- Paul
- Pau
- Álvaro
- Zaid

## Course

**Análisis de Imagen Biomédica** (Biomedical Image Analysis)  
3º Course, 2nd Term  
School of Biomedical Engineering

## License

The MIAS Database is provided for research purposes. See `Legend.txt` for specific usage terms and conditions.

## Notes

- All original mammogram images are in PGM format (.pgm)
- Processed images in EXTRACTION folder are in JPG format for easier visualization
- Feature extraction configurations can be customized in PyRadiomics settings
- Refer to the final project report for detailed methodology and results

---

*For questions or additional information, please refer to the project documentation and PyRadiomics official resources.*

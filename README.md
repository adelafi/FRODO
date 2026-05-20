FRODO: Functional Relationships and Ordination Data Observer

FRODO is an interactive web application built with Streamlit designed for the analysis and visualization of functional annotations of bacterial genomes (e.g., KO numbers, Pfams, EC codes) in the context of their taxonomy.

---

## INSTALLATION AND SETUP

The application requires Python 3.8 or higher.

### 1. Environment Setup
It is highly recommended to use a virtual environment to manage dependencies and avoid conflicts:

# Create a virtual environment
python -m venv venv

# Activate the environment (Linux/Mac)
source venv/bin/activate

# Activate the environment (Windows)
venv\\Scripts\\activate

### 2. Installing Dependencies
The project includes a 'requirements.txt' file. You can install all necessary libraries (including scientific packages like scikit-bio, scipy, and scikit-learn) by running:

pip install -r requirements.txt

---

## RUNNING THE APPLICATION

Once the libraries are installed, launch the application from the root directory using:

streamlit run app.py

After running this command, the app will be available in your browser at: http://localhost:8501

---

## LIBRARY MANAGEMENT & AUTOMATIC CHECKS

The application is "smart" about dependencies. It includes a built-in check_dependencies() function that runs every time you start the app.

If any of the following libraries are missing:
- Analysis: pandas, numpy, scipy, scikit-learn, scikit-bio, statsmodels
- Visualization: plotly, streamlit

The application will stop and display a clear message in the browser with the exact 'pip install' command needed to fix the issue.

---

## DATA REQUIREMENTS

To perform an analysis, you need two tab-separated (.tsv) files:

1. Functional Annotation File:
   - Must contain columns 'ID' (e.g., GCF/GCA accessions) and 'Functional Annotation'.
   
2. Taxonomy/Metadata File:
   - Must contain an 'ID' column (matching the IDs in the functional file) and any other columns used for grouping (e.g., Genus, Family, Habitat).

The application features an automatic cleaning processor (clean_gcf) that standardizes identifiers to ensure your data merges correctly even if the IDs have slightly different formats between files.

---

## KEY FEATURES

- Ordination: PCA, PCoA, t-SNE, and constrained ordinations (CCA, CAP).
- Clustering: K-means clustering on ordination results with metric calculation.
- Enrichment: Identify functional markers specific to groups using Fisher's Exact Test.
- Statistics: PERMANOVA tests to find significant functional differences between groups.

---

Created for bioinformatic analysis of genomic data.

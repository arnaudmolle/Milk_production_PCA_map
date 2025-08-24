# Milk_production_PCA_map
This study aims to leverage publicly available data on livestock environment to analyze spatial and temporal patterns in milk characteristics across Italy. Principal component analysis is used to reduce data dimensionality and uncover potential regional clustering. Gaps in the data are addressed through multiple imputation by chained equations

Rmd creates the map per month with the quality parameters, performs a MICE where data are missing and plot the first 3 PC as the colors in the RGB system to highlight eventual clustering

📊 Principal Component Analysis Mapping
This R Markdown (Rmd) script performs a Principal Component Analysis (PCA) on a set of milk quality parameters to visualize their geographical distribution across Italy. The analysis is conducted both for each individual month and for the entire dataset combined.

🎯 Project Goal
The primary goal of this script is to analyze and visualize the relationships between various milk quality metrics across different provinces in Italy. By applying PCA, we can reduce the dimensionality of the data and identify the most significant factors (principal components) that explain the variance in milk quality. The script then maps these principal component scores onto an Italian map, revealing underlying geographical patterns.

📂 Data Sources
The script uses multiple CSV files, each containing data for a specific milk quality parameter. The files are expected to be located in the directory specified by setwd(). The following datasets are used:

IBA.csv

DSCC_CM-.csv (Differential Somatic Cell Count)

CM_1100-.csv (Somatic Cell Count - SCS)

CM_1099-.csv (Protein - PROT)

CM_1098-.csv (Fat - FAT)

CM_1015-.csv (A30)

CM_1029-.csv (Total Solids - TS)

CM_1012-.csv (Rennet Coagulation Time - RCT)

CM_1014-.csv (K20)

CM_1007-.csv (Lactose)

CM_1006-.csv (Casein)

CM_1008-.csv (Total Bacterial Count - TBC)

CM_1002-.csv (Inhibitory Substances - IAC)

The script also includes a manually created lookup table (province_lookup_ai) to map Italian province names to their two-letter acronyms (sigla), which is crucial for the geographical mapping.

Concessa in licenza da Google

💻 Script Workflow
Setup and Libraries: Loads essential R libraries for data manipulation (dplyr, tidyr), visualization (ggplot2), interactive plotting (plotly), and spatial mapping.

Data Loading: Reads all specified CSV files into separate data frames.

Data Preprocessing:

Combines all individual datasets into a single data frame.

Cleans and standardizes the data, including handling NA values and ensuring consistent column names.

Averages the data for each month and province to prepare it for PCA.

Uses the missMDA library to impute missing values within the dataset, ensuring the PCA can be performed without errors.

PCA Execution:

Performs PCA on the preprocessed data using R's built-in prcomp() function.

Calculates the explained variance for each principal component to understand their significance.

Visualization:

3D Score Plots: Creates interactive 3D scatter plots of the PCA scores for each month and the full dataset. These plots show how provinces group together in the reduced-dimensional space.

3D Loadings Plots: Generates 3D plots showing the loadings of the original variables on the principal components. This helps interpret what each component represents.

Geographical Maps: Creates a series of maps of Italy, with each province colored according to its score on PC1, PC2, and PC3. This visualizes the spatial distribution of the main sources of variation.

RGB Map: A unique feature where the PC1, PC2, and PC3 scores are mapped to the Red, Green, and Blue channels of a color, providing a composite visualization of the three most important components on a single map.

📈 How to Run
Place all the required CSV data files in the same directory as the Rmd script.

Update the setwd() command in the script to point to the correct directory where the data is located.

Open the Rmd file in RStudio.

Click the "Knit" button to generate the HTML report.

The output will be an interactive HTML document that includes all the generated plots, allowing you to rotate and zoom in on the 3D visualizations.

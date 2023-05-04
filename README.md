# Machine-Learning-Assisted-Raman-Spectroscopy
Maryam Ghaffari

# Introduction
**RamanTech** is a leading biomedical company that produces Raman spectroscopy equipment used for molecular analysis in various fields, including healthcare, pharmaceuticals, and materials science. RamanTech aims to address the challenges associated with the interpretation and analysis of large quantities of spectral data generated by Raman spectroscopy. To achieve this goal, RamanTech is seeking to develop automated data analysis methods based on machine learning that can significantly improve the efficiency and accuracy of Raman spectroscopy data analysis.

The current methods for Raman spectroscopy data analysis require specialized knowledge and expertise, making it challenging for non-expert users to analyze and interpret the data accurately. Additionally, the analysis process is time-consuming, leading to delays in decision-making and increasing costs. By developing automated data analysis methods based on machine learning, RamanTech aims to make Raman spectroscopy more accessible to non-expert users and facilitate faster and more precise data analysis.

The development of machine learning-based data analysis methods has the potential to revolutionize the Raman spectroscopy industry. By leveraging machine learning algorithms, RamanTech can analyze large datasets and identify patterns and trends that would otherwise be difficult to detect using traditional analysis methods. This capability can provide significant advantages in terms of identifying specific molecules, improving the accuracy of data interpretation, and reducing analysis time.

The automated data analysis methods based on machine learning that RamanTech aims to develop can have a significant impact on various fields, including healthcare, materials science, and pharmaceuticals. In healthcare, these methods can facilitate the development of more accurate and efficient diagnostic tools and therapies for a wide range of diseases. Pharmaceuticals can enable faster and more efficient drug discovery and development processes. In materials science, they can help in the development of new materials with specific properties, accelerating the innovation cycle.

Overall, RamanTech`s efforts to develop automated data analysis methods based on machine learning can provide significant value to its customers and contribute to advancing the field of molecular analysis.

# Problem Statement & Mission
Developing automated Raman spectroscopy data analysis faces several challenges such as data preprocessing, feature selection, model selection, interpretation, and generalization. In Biological samples, there are additional challenges added to the aforementioned challenges. Biological samples are typically weak Raman scatterers, and the signals generated are often low in intensity. This makes it difficult to obtain high-quality spectra and increases the risk of interference from background noise. Furthermore, biological samples are often complex mixtures of different components, including proteins, nucleic acids, lipids, and carbohydrates. This complexity can lead to overlapping peaks in Raman spectra, making it challenging to identify and quantify individual components accurately. Biological samples are inherently variable, and small changes in sample preparation, handling, or measurement conditions can result in significant variations in Raman spectra. This variability can make it difficult to obtain reproducible results. This project's mission is to develop an automated data analysis method based on machine learning algorithms for Raman spectroscopy in biological samples. I aim to tackle the challenges of large quantities of spectral data, complex spectra with overlapping peaks and noise, and the need for specialized knowledge for analysis and interpretation. By leveraging the power of machine learning, I will develop user-friendly software tools to make Raman spectroscopy more accessible to non-expert users and facilitate faster and more precise data analysis. The goal is to enable faster and more accurate data interpretation, and ultimately, to maximize the clinical translation potential of Raman spectroscopy in the biomedical industry.

# Methodology
Methodology in a data science project refers to the structured approach or process used to carry out the project from start to finish.The general research strategy in this project is to use the OSEMiN pipline on the availabe dataset to structure their workflow and make it more organized and efficient The OSEMiN pipeline consists of the following five steps: **Obtain, Scrub, Explore, Model, and iNterpret**.

## Obtain
Parlatan et al. [1] in a recent stuy classified nano-sized extracellular vehicles (EVs) based on their cellular origins, which is important for the development of diagnostic tools and therapies targeting specific cell types. Their study investigated the potential of using machine learning-assisted surface-enhanced Raman spectroscopy (SERS) as a label-free method for differentiating cancer cell-derived exosomes from those of healthy cells. The raw data of this study are openly available in zenodo at https://doi.org/10.5281/zenodo.7011380. Raman spectra of Evs from five types of cells were stored in a CSV file.

## Scrub

After obtaining the data the first step is to clean and preprocess the raw data to remove any errors, inconsistencies, or missing values. The spectra also need to normalize or scale the data to make it more suitable for machine learning algorithms. This step may include techniques such as outlier removal, imputation, and feature scaling. The beginning of data cleaning is to print a concise summary of a DataFrame with `.info()` method and view a small sample of the DataFrame object with `.head()` method. Through the `.info()` method we access valuable information about missing values and datatype. `.isnull()` is a method that helps us determine the missing value and based on the percentage of them or necessity of them, decided on delete them with .dropna() method. Raman spectroscopy data preprocessing is an essential step for machine learning analysis. Some common preprocessing steps are **baseline correction, normalization, smoothing, peak detection, feature extraction, and data augmentation**. The preprocessing steps for Raman spectroscopy data depend on the specific application and the quality of the raw data. 

![image](https://user-images.githubusercontent.com/101681195/230388987-2f6e296b-ac60-4771-a083-c85f64473c52.png)
### Baseline correction and Normalization
Removing the baseline from Raman spectra can help to enhance the spectral features and make them easier to interpret. Additionally, baseline removal can help to reduce the noise in the spectrum and improve the accuracy of any subsequent quantitative analysis. There are various methods to remove the baseline, and the choice of method depends on the nature of the baseline and the characteristics of the spectrum. 
**Interpolation-based baseline correction** is a method used in spectroscopy to remove the baseline drift or baseline offset from a signal. The baseline is defined as the low-frequency variations in the signal that are unrelated to the analyte's spectral features. Baseline drift can be caused by various factors, such as instrument noise, changes in temperature, and variations in the intensity of the light source.
For Raman spectroscopy data, **L2 normalization** is often used, as it scales the Raman spectra to have a unit length while preserving the relative intensity of the spectral features. This can be achieved by dividing each spectrum by its L2 norm, which is calculated as the square root of the sum of the squares of the spectrum values.



# Machine-Learning-Assisted-Raman-Spectroscopy
Maryam Ghaffari

# Introduction
**RamanTech** is a leading biomedical company that produces Raman spectroscopy equipment used for molecular analysis in various fields, including healthcare, pharmaceuticals, and materials science. RamanTech aims to address the challenges associated with the interpretation and analysis of large quantities of spectral data generated by Raman spectroscopy. To achieve this goal, RamanTech is seeking to develop **automated data analysis** methods based on machine learning that can significantly improve the efficiency and accuracy of Raman spectroscopy data analysis.

The current methods for Raman spectroscopy data analysis require specialized knowledge and expertise, making it challenging for non-expert users to analyze and interpret the data accurately. Additionally, the analysis process is time-consuming, leading to delays in decision-making and increasing costs. By developing automated data analysis methods based on machine learning, RamanTech aims to make Raman spectroscopy more accessible to non-expert users and facilitate faster and more precise data analysis.

The development of machine learning-based data analysis methods has the potential to revolutionize the Raman spectroscopy industry. By leveraging machine learning algorithms, RamanTech can analyze large datasets and identify patterns and trends that would otherwise be difficult to detect using traditional analysis methods. This capability can provide significant advantages in terms of **identifying specific molecules, improving the accuracy of data interpretation, and reducing analysis time.**
The automated data analysis methods based on machine learning that RamanTech aims to develop can have a significant impact on various fields, including healthcare, materials science, and pharmaceuticals. In healthcare, these methods can facilitate the development of more accurate and efficient diagnostic tools and therapies for a wide range of diseases. Pharmaceuticals can enable faster and more efficient drug discovery and development processes. In materials science, they can help in the development of new materials with specific properties, accelerating the innovation cycle.
Overall, RamanTech`s efforts to develop automated data analysis methods based on machine learning can provide significant value to its customers and contribute to advancing the field of molecular analysis.

# Problem Statement & Mission
Developing automated Raman spectroscopy data analysis faces several challenges such as data preprocessing, feature selection, model selection, interpretation, and generalization. In Biological samples, there are additional challenges added to the aforementioned challenges. **Biological samples are typically weak Raman scatterers**, and the signals generated are often low in intensity. This makes it difficult to obtain high-quality spectra and increases the risk of interference from background noise. Furthermore, biological samples are often complex mixtures of different components, including proteins, nucleic acids, lipids, and carbohydrates. This complexity can lead to overlapping peaks in Raman spectra, making it challenging to identify and quantify individual components accurately. Biological samples are inherently variable, and small changes in sample preparation, handling, or measurement conditions can result in significant variations in Raman spectra. This variability can make it difficult to obtain reproducible results. This project's mission is to develop an automated data analysis method based on machine learning algorithms for Raman spectroscopy in biological samples. I aim to tackle the challenges of **large quantities of spectral data, complex spectra with overlapping peaks and noise, and the need for specialized knowledge for analysis and interpretation**. By leveraging the power of machine learning, I will develop user-friendly software tools to make **Raman spectroscopy more accessible to non-expert users and facilitate faster and more precise data analysis**. The goal is to enable faster and more accurate data interpretation, and ultimately, to maximize the clinical translation potential of Raman spectroscopy in the biomedical industry.

# Evaluation Metrics
Among the cell lines I tried to classify, **Hela cells** are generally considered to be **highly malignant**. They were originally derived from a cervical cancer patient and have been extensively studied for their ability to proliferate rapidly and form tumors in vivo. **HT1080 cells** are also considered to be **highly malignant** and have been used extensively as a model for studying the biology of fibrosarcoma. Hec and Mef are not as well characterized as Hela and HT1080 cells, but they have been reported to have malignant properties in certain studies. Thp1 cells are a human monocytic leukemia cell line and are generally considered to be less malignant than the other cell lines.The model will be a **multi-classification**, meaning that there are five potential classes (**Ht1080, Hec, Mef, Hela, Thp-1**) that can be placed. While Hec, Mef, Thp-1 cells can affect the health of the petients, Hela and HT1080 cells are generally considered more serious and require more aggressive treatment, as they have ability to invade surrounding tissues, and potential to metastasize to distant sites in the body. If the designed model incorrectly predicts Hec, Mef, and Thp-1 cells, some patients with a higher risk of life-threatening would be neglected. Therefore, for the purposes of this work, a **low false-negative** rate has more value than a low false-positive rate. When a low false-negative rate has more value than a low false-positive rate, the metric evaluation of **sensitivity or recall** is more important than specificity or precision. Sensitivity or recall measures the proportion of actual positives that are correctly identified as such by a classification model, while specificity or precision measures the proportion of actual negatives that are correctly identified as such. A low false-negative rate means that the model is identifying most of the positive cases correctly, which is particularly important in situations where missing a positive case can have serious consequences. In contrast, a low false-positive rate is more important when the cost of false positives is high, such as in medical testing where false positives can lead to unnecessary treatments and anxiety for patients. The optimum recall for the selected model considerd to be equal or higher than 0.9. The Recall is defined as:

$$ \text{Recall} = \frac{\text{Number of True Positives}}{\text{Number of True Positives + Number of False Negative}} $$ 

$$ \text{Recall} => 0.9 $$ 

The other important aspect of this project is how a **prediction need time**. The time module in Python can be useful for measuring the time elapsed during model training and prediction. It evaluate the efficiency of the model and identify any bottlenecks or areas for optimization.The time module will be use to measure the time taken for each inference or for a batch of inferences. This can help to optimize the performance of the model, especially with large datasets or real-time applications where speed is important. The optimum elapsed time for predicting a new spectrum is equal or less than 60 seconds.

$$\text{Elapsed Time} =< 60\text { Seconds} $$

# Methodology
Methodology in a data science project refers to the structured approach or process used to carry out the project from start to finish.The general research strategy in this project is to use the OSEMiN pipline on the availabe dataset to structure their workflow and make it more organized and efficient The OSEMiN pipeline consists of the following five steps: **Obtain, Scrub, Explore, Model, and iNterpret**.

## Obtain
Parlatan et al. [1] in a recent stuy classified nano-sized extracellular vehicles (EVs) based on their cellular origins, which is important for the development of diagnostic tools and therapies targeting specific cell types. Their study investigated the potential of using machine learning-assisted surface-enhanced Raman spectroscopy (SERS) as a label-free method for differentiating cancer cell-derived exosomes from those of healthy cells. The raw data of this study are openly available in zenodo at https://doi.org/10.5281/zenodo.7011380. Raman spectra of Evs from five types of cells were stored in a **CSV file**.

## Scrub

After obtaining the data the first step is to clean and preprocess the raw data to remove any errors, inconsistencies, or missing values. The spectra also need to normalize or scale the data to make it more suitable for machine learning algorithms. This step may include techniques such as outlier removal, imputation, and feature scaling. The beginning of data cleaning is to print a concise summary of a DataFrame with `.info()` method and view a small sample of the DataFrame object with `.head()` method. Through the `.info()` method we access valuable information about missing values and datatype. `.isnull()` is a method that helps us determine the missing value and based on the percentage of them or necessity of them, decided on delete them with `.dropna()` method. Raman spectroscopy data preprocessing is an essential step for machine learning analysis. Some common preprocessing steps are **baseline correction, normalization, smoothing, peak detection, feature extraction, and data augmentation**. The preprocessing steps for Raman spectroscopy data depend on the specific application and the quality of the raw data. 

![image](https://user-images.githubusercontent.com/101681195/236503549-47372c6a-2de0-492e-9300-f8e9ed0a20d7.png)

### Baseline Correction and Normalization
Removing the baseline from Raman spectra can help to enhance the spectral features and make them easier to interpret. Additionally, baseline removal can help to reduce the noise in the spectrum and improve the accuracy of any subsequent quantitative analysis. There are various methods to remove the baseline, and the choice of method depends on the nature of the baseline and the characteristics of the spectrum. 
**Interpolation-based baseline correction** is a method used in spectroscopy to remove the baseline drift or baseline offset from a signal. The baseline is defined as the low-frequency variations in the signal that are unrelated to the analyte's spectral features. Baseline drift can be caused by various factors, such as instrument noise, changes in temperature, and variations in the intensity of the light source.
For Raman spectroscopy data, **L2 normalization** is often used, as it scales the Raman spectra to have a unit length while preserving the relative intensity of the spectral features. This can be achieved by dividing each spectrum by its L2 norm, which is calculated as the square root of the sum of the squares of the spectrum values.

![image](https://user-images.githubusercontent.com/101681195/236215624-9161c506-91cd-4c51-80f9-2b2b07ae79bf.png)

## Machine Learning Models
I trained 5 different machine learning classification models to classifiy the spectra.The models I used were the following:
- Logistic Regression
- Dession Tree
- Convolutional Neural Network (CNN)
- Fully connected neural network (FCNN)
- Residual Network (ResNet)

Based on the results, the Logistic Regression and Fully connected neural network (FCNN) models with preprocessing on data achieved the highest accuracy of 0.985 and 0.988, respectively, followed by the Decision Tree model with preprocessing on data achieving an accuracy of 0.961. The Decision Tree model with feature extraction achieved a slightly lower accuracy of 0.919, indicating that the feature extraction may not have been effective for this dataset.
On the other hand, the Convolutional Neural Network (CNN) and Residual Network (RestNet) models, both with and without preprocessing on data, performed poorly, with accuracies of only 0.231 and 0.149, respectively. This suggests that the CNN and RestNet models may not be suitable for this particular dataset.
It is also important to note the elapsed time for each model, with the Logistic Regression and FCNN models with preprocessing on data achieving the fastest elapsed time of only 3.54 and 57.04 seconds, respectively, while the RestNet model with and without regularization had the longest elapsed time of 754.91 seconds.
Overall, the results suggest that the Logistic Regression and FCNN models with preprocessing on data are the most effective for this particular Raman spectroscopy dataset. However, it is important to consider the specific goals of this project that is **less false negatives in  HT1080 and Hela cells and elapse time less than 60 seconds**. Based on the results **FCNN** is my selected model for practical use.




![image](https://user-images.githubusercontent.com/101681195/236521346-349b0dd5-9f36-4658-9cc6-0162f159ae1c.png)








![image](https://user-images.githubusercontent.com/101681195/236524249-444a32bb-178f-426b-aca6-7bf9a3a276ea.png)

## Feature Importance
In the context of Raman spectroscopy data analysis, feature importance can be a valuable tool for understanding and interpreting the data. Here are some reasons why feature importance is important:

1. Identification of Relevant Spectral Features: Raman spectroscopy generates a large amount of spectral data, often consisting of hundreds or thousands of variables (wavelengths/intensities). Feature importance analysis can help identify the specific spectral features that contribute the most to the classification or regression task at hand. By focusing on the most important features, you can gain insights into the molecular or compositional characteristics of the samples being analyzed.

2. Dimensionality Reduction: Raman spectroscopy datasets are typically high-dimensional, which can make analysis and interpretation challenging. Feature importance analysis can aid in dimensionality reduction by identifying the most informative features. By selecting a subset of important features, you can reduce the complexity of the data and improve the efficiency and effectiveness of subsequent analysis steps.

3. Identifying Spectral Artefacts or Noise: In some cases, certain spectral features may not contribute meaningfully to the classification or regression task and might be noise or artefacts. Feature importance analysis can help identify such features, allowing for data cleaning and improving the overall quality of the analysis results.

In this project the `permutation_importance` method from scikit-learn's `inspection` module was used. This method calculates feature importance by permuting the values of each feature and measuring the impact on the model's performance.

<p align="center">
<img width="460" height="300" src="https://github.com/MarGhaf/Machine-Learning-Assisted-Raman-Spectroscopy/assets/101681195/5d19a6f0-70c4-4efe-816c-d2bfebc12692">
</p>


The exact interpretation of Raman peaks depends on factors such as molecular structure, chemical environment, and experimental conditions. According to the top 10 important features peaks around 700, 850, and 1050 cm^-1  have a significant role in predicting the type of vesicles secreted from different cancerous cell types. Aromatic amino acids, including phenylalanine, tyrosine, and tryptophan, can contribute to Raman peaks in this region in the context of biological samples. This finding helps scientists to identify specific molecules and study their role in cell behaviors would be valuable in cardiology studies. 


# Conclusion 
In conclusion, this project aimed to develop automated data analysis methods based on machine learning algorithms for Raman spectroscopy in biological samples. The objective was to address the challenges associated with large quantities of spectral data, complex spectra with overlapping peaks and noise, and the need for specialized knowledge for analysis and interpretation.
By leveraging the power of machine learning, the project successfully developed a user-friendly software tool that makes Raman spectroscopy more accessible to non-expert users and facilitates faster and more precise data analysis. The chosen model, the Fully connected neural network (FCNN), achieved high accuracy in classifying the spectra and demonstrated low false-negative rates for the more malignant cell types. The evaluation metrics focused on sensitivity (recall) and elapsed time for prediction. The FCNN model achieved an accuracy of 0.988 and demonstrated a recall above 0.9, ensuring the low false-negative rate required to identify high-risk cell types accurately. Additionally, the prediction elapsed time of less than 60 seconds met the desired efficiency for practical use. Feature importance analysis using permutation importance helped identify the most relevant spectral features for classification.
Overall, the developed machine learning-assisted Raman spectroscopy method holds great potential in the field of molecular analysis. It can contribute to advancements in healthcare, materials science, and pharmaceuticals by enabling faster and more accurate diagnostics, efficient drug discovery, and the development of new materials. By overcoming the challenges associated with Raman spectroscopy data analysis, this project has paved the way for enhanced understanding and utilization of Raman spectroscopy in various industries.

# Recommendations & Future Works
Based on the business understanding and the results of machine learning, the following recommendations and future works can be suggested:

- Deploy the model: It is recommended to deploy the model that has shown good performance on the Raman spectroscopy dataset. Fully connected neural network with preprocessing has shown good results, and it can be used for further analysis.

- Increase dataset size: To improve the model's performance, increasing the dataset size can be useful. Collecting more samples from different sources can help in better model generalization.

- Fine-tune the models: Fine-tuning the models can help in improving their performance. The hyperparameters of the models can be adjusted and optimized to improve their performance.

- Develop user-friendly interface: As mentioned in the business understanding, the current methods for Raman spectroscopy data analysis require specialized knowledge and expertise. Therefore, developing a user-friendly interface that can make the Raman spectroscopy more accessible to non-expert users can be useful.

- Develop ensemble models: Combining multiple models can lead to better performance. Therefore, developing ensemble models that can combine the predictions of different models can be useful.

- Investigate feature extraction methods: Investigating feature extraction methods can help in improving the performance of the models. Different feature extraction methods can be compared to find the most effective ones for Raman spectroscopy data analysis.

- Further validation: It is recommended to further validate the performance of the models on external datasets to ensure that they are generalizable and can be used in different settings.

- Collaborate with industry partners: Collaborating with industry partners can help in better understanding the needs and challenges of the industry and developing solutions that can address these challenges.
- 
 ## Repository Structure
```

├── Code : final_student.ipynb includ modeling
├── Data : Data used for modeling, includes train and test image files
├── Images : Images used in Phase 5 Project Presentation.pdf and README
├── Phase 5 Project Presentation.pdf : Presentation for stakeholders
└── README.md : Project information and repository structure

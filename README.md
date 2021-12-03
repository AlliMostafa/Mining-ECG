# Mining  Ecg database

# 1. PTB-XL dataset
Electrocardiography (ECG) is a key diagnostic tool to assess the cardiac condition of a patient. Automatic ECG interpretation algorithms as diagnosis support systems promise large reliefs for the medical personnel - only on the basis of the number of ECGs that are routinely taken. However, the development of such algorithms requires large training datasets and clear benchmark procedures. In our opinion, both aspects are not covered satisfactorily by existing freely accessible ECG datasets.

The PTB-XL ECG dataset is a large dataset of 21837 clinical 12-lead ECGs from 18885 patients of 10 second length. The raw waveform data was annotated by up to two cardiologists, who assigned potentially multiple ECG statements to each record. The in total 71 different ECG statements conform to the SCP-ECG standard and cover diagnostic, form, and rhythm statements. To ensure comparability of machine learning algorithms trained on the dataset, we provide recommended splits into training and test sets. In combination with the extensive annotation, this turns the dataset into a rich resource for the training and the evaluation of automatic ECG interpretation algorithms. The dataset is complemented by extensive metadata on demographics, infarction characteristics, likelihoods for diagnostic ECG statements as well as annotated signal properties.

All relevant metadata is stored in ptbxl_database.csv with one row per record identified by ecg_id. It contains 28 columns that can be categorized into:

1. Identifiers: Each record is identified by a unique ecg_id. The corresponding patient is encoded via patient_id. The paths to the original record (500 Hz) and a downsampled version of the record (100 Hz) are stored in filename_hr and filename_lr.
2. General Metadata: demographic and recording metadata such as age, sex, height, weight, nurse, site, device and recording_date
3. ECG statements: core components are scp_codes (SCP-ECG statements as a dictionary with entries of the form statement: likelihood, where likelihood is set to 0 if unknown) and report (report string). Additional fields are heart_axis, infarction_stadium1, infarction_stadium2, validated_by, second_opinion, initial_autogenerated_report and validated_by_human.
4. Signal Metadata: signal quality such as noise (static_noise and burst_noise), baseline drifts (baseline_drift) and other artifacts such as electrodes_problems. We also provide extra_beats for counting extra systoles and pacemaker for signal patterns indicating an active pacemaker.
5. Cross-validation Folds: recommended 10-fold train-test splits (strat_fold) obtained via stratified sampling while respecting patient assignments, i.e. all records of a particular patient were assigned to the same fold. Records in fold 9 and 10 underwent at least one human evaluation and are therefore of a particularly high label quality. We therefore propose to use folds 1-8 as training set, fold 9 as validation set and fold 10 as test set.

Data set can be accessed from [kaggle](https://www.kaggle.com/khyeh0719/ptb-xl-dataset/version/1) or [physionet](https://physionet.org/static/published-projects/ptb-xl/ptb-xl-a-large-publicly-available-electrocardiography-dataset-1.0.1.zip).

Origginal authors:

Wagner, P., Strodthoff, N., Bousseljot, R.-D., Kreiseler, D., Lunze, F.I., Samek, W., Schaeffter, T. (2020), PTB-XL: A Large Publicly Available ECG Dataset. Scientific Data. https://doi.org/10.1038/s41597-020-0495-6


# 2. Analysing heartbeat signals using heartpy

Heartpy is a python toolkit to analyze heartbeats. Using Anaconda can be simply installed  by :

pip install heartpy

a full manual can be found at [here](https://python-heart-rate-analysis-toolkit.readthedocs.io/en/latest/heartpy.heartpy.html#main-functions)

# 3. 

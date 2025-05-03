# ESE527 Medical Prediction LLM Based on MIMIC-III Database Capstone
Title: Large Language Model for Medical Forecasting using MIMIC-III Data

Background
With the advancements in digitalization within the medical and healthcare system, unstructured text has become an essential component of Electronic Health Records (EHRs; Jackson et al., 2018). Natural Language Processing (NLP) models have already been widely applied to free-text data in EHRs and trained on real-world hospital datasets, yielding promising results.
However, unlike traditional NLP models, there are limited experiments or recorded studies applying and evaluating the latest generation of Large Language Models (LLMs), such as GPT-4 or Gemini, in this domain. Most research focuses on physical tests or medical quizzes to validate these models, but their performance in analyzing complex clinical data for decision-making should not be overlooked.
Target
Fine-tuning large language models using MIMIC-III clinical notes to enhance its ability to accurately predict and interpret medical conditions, improving clinical decision support in ICU settings.
Decisions to be Impacted
Devisions to be impacted by this project are clinical decision-making in ICU settings:
1.	Diagnosis Support Decisions:
•	The model may help clinicians interpret past unstructured clinical notes to better identify or confirm diagnoses.
2.	Prognostic Forecasting and Risk Prediction:
•	Predicting patient outcomes, e.g. risk of mortality, diseases, complications, etc.
•	Supporting resource allocation by identifying high-risk patients early.
3.	Operational and Workflow Decisions:
•	Reducing cognitive load on medical staff.
•	Supporting decisions on whether and how to integreate LLM-powered tools into clinical workflows.
•	Policies on AI-assisted decision-making in sensitive healthcare environments.
Business Value
•	Hospital: Optimized ICU resource allocation
•	Patient: Improved patient outcomes since early intervension strategies are informed
•	Clinicians: assisted with early and informed decisions about their patients
•	Insurance companies: Better risk predictions
Data assets
•	MIMIC-III: accessible through the link https://physionet.org/content/mimiciii/1.4/.
Data Description:
•	40k+ patients data in critical care units
•	2M+ clinical notes
•	diverse & large population of ICU patients
•	Time range: 2001 to 2012
Data compositions (25 .csv files):
•	Demographics
•	Vital Signs
•	Laboratory Tests
•	Medications
•	Diagnoses & Procedures
•	Clinical Notes
•	Prescriptions
•	Survival Outcomes
Out of the 25 csv files, noteevents.csv, patients.csv, and admissions.csv are used for analysis. Patients and admissions provide supplementary information and note events provide the clinical notes that are the foundation for the project. The next section introduces each files and the information extracted from each file.
•	Reason for Choosing Clinical notes:
	Physician’s high-level summary of patients’ entire medical information
	Added interpretation and reasoning, most relevant details

Current Progress:
We collected clinical notes along with their corresponding documentation IDs and grouped them using unique patient identifiers. To extract structured medical concepts, we applied MedCAT, a clinical NLP toolkit, to perform named entity recognition and linking (NER+L), mapping terms to SNOMED CUIs for medications, symptoms, disorders, and procedures. This replacement process helps mitigate human-recorded biases in raw text.
We used charttime to timestamp each visit and organized all notes chronologically per patient. Rare concepts (appearing only once across the dataset) were filtered as outliers. To capture longitudinal patient journeys, we implemented a temporal bucketing strategy (e.g., <1 Day>, <1 Month>) and built a structured clinical timeline for each patient. The final dataset enables downstream modeling tasks such as patient trajectory prediction, temporal concept clustering, and bias-aware medical analysis.
In the next step, we will begin process the tokenization and applied them into the LLaMA v2-7B and Mistral v0.1-7B model for prediction.

Test on 1000 patients: https://colab.research.google.com/drive/1rhPykIPRRTDICNTMeI3d0xvV5uypN4be?usp=sharing


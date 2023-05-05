# MLFinalProject
Final Project work for INFO-251 Spring 2023


For folders containing conversation transcripts, utterance transcripts, and the base conversations dataframe (Outcomes_NoTranscripts.csv), see our shared [Google Drive here](https://colab.research.google.com/drive/1NrvHUrMtmp9z0uby6j_zXXz5as4gNy4s?usp=share_link). Note that you must access with an @berkeley.edu email address. 


## Base Files

**MartinQuinnScores.csv**
Contains information on the median Martin-Quinn Score for each Supreme Court term. The range for scores is -8 to 4 with 4 being the most conservative justice in the Supreme Court’s history and -8 being the most liberal. Dates from 1937 to 2021. 

**SCDB_2022_01_caseCentered_Docket.csv**
Contains 60 variables for each case including the outcome, whether the petitioner won, lower court decision, legal issue area, and so on, for the full history of the court 1791 - present

**Cornell Established Data -- Self Compiled**
Dataset created via DataPreProcessing.ipynb below using Cornell University's [convokit package](https://convokit.cornell.edu/documentation/supreme.html). Approximately 1,700,000 utterances and over 8,000 oral arguments transcripts from 7,700 cases scraped from the [Oyez website](https://www.oyez.org). Years 1955 - 2019. 

## Notebooks 

**DataPreProcessing**
This script ingests the MartinQuinnScores and SCDB base files and pulls in the convokit package. The output is a pair of dataframes of Conversations (argument text) data and Utterances (speaker text) data. Two folders containing the actual transcript text for later ingestion are also created. 

**SimpleModels**
Runs various logistic regression, decision tree, and random forest models on our Conversations dataframe.

**BertTrial**
Runs our base trial with semi-tuned hyperparameters. Requires access to base files -- hardcoded paths must be updated in the script. 

**BigBirdTrial** 
Runs initial passes using the BigBird model. Likely requires access to cloud computing services. We run using Google Colab standard GPU accelerator. 

**DeBERTa_model**
Runs final DeBERTa model on conversation text. With default sequence parameters (mean 3000 tokens, std dev 250) and 3000 conversations, cloud computing services required. Ongoing updates to this model include embedding MartinQuinn data and wrapping speaker information per utterance to garner more variability among transcripts and avoid overfitting. We recommend running larger portions of data using Google Colab premium GPUs if available. 

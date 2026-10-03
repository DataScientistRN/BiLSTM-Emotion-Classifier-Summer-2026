# CSCIE-89B Introduction to Natural Language Processing

Booky: A Bidirectional LSTM Approach to Real-Time Emotion Classification in Narrative Text

Cristina Kennedy, BSN, RN

August 2026

## Overview

Reading can be a deeply emotional endeavor, and it is such a great feeling to be able to share it with someone. However, often reading is an isolated experience for the reader, not a social one. That led me to imagine the next best thing: having a live emotion classifier that can validate your emotions in real time, wrapped in a product I named Booky.

Booky is a Bidirectional Long Short-Term Memory (BiLSTM) classifier built with Keras TextVectorization and Embedding layers and is trained from scratch on a subset of the GoEmotions dataset. Rather than using all 28 emotions from the dataset, some of them being too sparse regardless, this project trains its own lightweight model on nine emotions that plausibly occur in narrative fiction: joy, sadness, fear, anger, surprise, love, disgust, embarrassment, and curiosity.

A BiLSTM was strategically chosen for this task for its unique ability to process data both forward and backward, a crucial step in getting good context from the data. Keras TextVectorization was chosen over a manual NLTK pipeline mainly because TextVectorization saves and loads the preprocessing into the model itself, so raw strings can be fed in directly and ensures the same transformation for all train/val/test data.

Two models with the same architecture but different inputs were trained and evaluated head-to-head. Model A is a single-label classifier (softmax output, trained only on rows carrying exactly one of the nine emotions), and Model B is a multi-label classifier (sigmoid output, trained on a larger set that also keeps rows carrying more than one of the nine emotions at once). Both are evaluated on the exact same single-label test set never seen by either model. Model B with an overall accuracy of 69% was ultimately chosen for the demonstration. 

Model B was then applied to “The Wizard of Oz”, a narrative text never seen by the model, where it classified and assigned each page a label, confidence score, and a probability vector. The emotion labels predicted here will display on the e-reader at the bottom of the page as you are reading through the book.


# PFAM-amino-acid-domain-classification
## 1. Problem Description
### 1.1 Description
Source: https://www.kaggle.com/googleai/pfam-seed-random-split Data : PFAM seed random split . Download random_split.zip . Which contains train dev and test data files.

Problem Statement : The task is , given the amino acid sequence of the protein domain, predict which family it belongs to.
### 1.2 Source/Useful links
https://www.biorxiv.org/content/10.1101/626507v3.full
https://arxiv.org/pdf/1606.01781.pdf?
https://www.appliedaicourse.com/lecture/11/applied-machine-learning-online-course/3439/code-example-imdb-sentiment-classification/8/module-8-neural-networks-computer-vision-and-deep-learning
### 1.3 Real world objectives and constraints
No low latency requirement.
Interpretability is not important.
Only sequence data is input data
## 2. Deep Learning Problem Formulation
### 2.1 Data
This directory contains data to train a model to predict the function of protein domains, based on the PFam dataset.

Domains are functional sub-parts of proteins; much like images in ImageNet are pre segmented to contain exactly one object class, this data is presegmented to contain exactly and only one domain.

The purpose of the dataset is to repose the PFam seed dataset as a multiclass classification machine learning task.

#### 2.1.1 Data split and layout :
The approach used to partition the data into training/dev/testing folds is a random split.

Training data should be used to train your models.
Dev (development) data should be used in a close validation loop (maybe for hyperparameter tuning or model validation).
Test data should be reserved for much less frequent evaluations - this helps avoid overfitting on your test data, as it should only be used infrequently.
#### 2.1.2 File Content
Each fold (train, dev, test) has a number of files in it. Each of those files contains csv on each line, which has the following fields:

sequence: HWLQMRDSMNTYNNMVNRCFATCIRSFQEKKVNAEEMDCTKRCVTKFVGYSQRVALRFAE family_accession: PF02953.15 sequence_name: C5K6N5_PERM5/28-87 aligned_sequence: ....HWLQMRDSMNTYNNMVNRCFATCI...........RS.F....QEKKVNAEE.....MDCT....KRCVTKFVGYSQRVALRFAE family_id: zf-Tim10_DDP

Description of fields: Sequence: These are usually the input features to your model. Amino acid sequence for this domain. There are 20 very common amino acids (frequency > 1,000,000), and 4 amino acids that are quite uncommon: X, U, B, O, Z.
family_accession: These are usually the labels for your model. Accession number in form PFxxxxx.y (Pfam), where xxxxx is the family accession, and y is the version number. Some values of y are greater than ten, and so 'y' has two digits.
family_id: One word name for family.
sequence_name: Sequence name, in the form "𝑢𝑛𝑖𝑝𝑟𝑜𝑡𝑎𝑐𝑐𝑒𝑠𝑠𝑖𝑜𝑛𝑖𝑑/start_index-$end_index".
aligned_sequence: Contains a single sequence from the multiple sequence alignment (with the rest of the members of the family in seed, with gaps retained.

Generally, the family_accession field is the label, and the sequence (or aligned sequence) is the training feature.

This sequence corresponds to a domain, not a full protein.

### 2.2 Mapping the real world problem to Deep Learning problem
Since there are 18,000 output classes , so this is a multiclass classification problem

Performance Metric : We ll be using accuracy as our performance metric.
### 2.3 Deep learning constraints and objectives
Objective : The objective is to predict the family of the given domain of a amino acid using the sequence data posing a multi class classification problem.

Constraints :

No low latency requirement.
Get a decent accuracy.
Use only sequence data as input.

Team Members:

Aksh Minesh Patel (G01418113: apatel66@gmu.edu)

Sreeja Venkatakrishnan (G01438914: svenka7@gmu.edu)

# Implementation of "[GPT-who: An Information Density-based Machine-Generated Text Detector](https://arxiv.org/abs/2310.06202)"


This repository provides code to calculate the 4 UID-based features and UID minimum and maximum span features described in the paper for efficient and accurate machine text detection.

![image](https://github.com/saranya-venkatraman/gpt-who/assets/8631382/eee122f4-8578-4f88-b2ca-d01b597a1bde)

## Installation

Use the package manager [pip](https://pypi.org/project/pip/) to install all requirements.

```bash
$ pip install -r requirements.txt
```

## The notebook contains 2 scripts:
1. get_uid_features.py This scripts loads texts and author labels from a csv file/any data source, calculates all UID features needed for GPT-who and writes them to a new csv file. This new generated csv file is the input to gpt-who.py

#### Arguments
```
--input_path: Path to the CSV file or data source containing text and corresponding labels (default: None).
--cache_path: Path to the cache directory for the GPT-2 XL model (default: "./.cache/models/gpt2-xl").
--output_path: Path to the CSV file where UID features will be saved (default: "./scores/uid_features.csv").
```

#### Example Usage 
```
python gptwho_uid_features.py --input_path ./data/text_labels.csv --cache_path ./model_cache/gpt2-xl --output_path ./scores/uid_features.csv
```

2. gpt-who.py: This script takes as input two .csv files with UID features corresponding to the train and test split of the dataset, calculates the UID span features to concatenate with the other 4 (uid_var, uid_diff, uid_diff2, and mean), runs logistic regression, predicts labels, and reports machine text detection performance.

#### Arguments
```
--train_file: Path to the CSV file containing UID features for the training split (default: "./scores/train_uid_scores.csv").
--test_file: Path to the CSV file containing UID features for the test split (default: "./scores/test_uid_scores.csv").
```


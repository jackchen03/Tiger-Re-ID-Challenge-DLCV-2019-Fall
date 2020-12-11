# DLCV 2019 Fall, Final Project Challenge#1
## Tiger ReId

![illustration](https://cvwc2019.github.io/imgs/det_1.jpg)

## Introduction
Tiger re-identification aims to find all image in the database containing the same tiger as the query one.

The original challenge website is provided [here](https://cvwc2019.github.io/challenge.html).

## Methods
Overall Architecture:
![alt text](./overall_architecture.PNG?raw=true)

Methods Used:
1. Produced **semantic masks** based on pose labels, later served as pseudo ground truth labels for training on semantic segmentation.
2. Train **semantic segmentation** model to identify and extract local features from specific body parts. 
3. Integrating the training paths of **re-id and segmentation**, enabled **end-to-end training** and considered both **global and local features**.

For the detail of our model, please refer to 'final_poster.pdf'

## Dataset 
One can download the dataset [here](https://drive.google.com/file/d/1QmvUBz07IphyIi-80iz5B5ZWMEC0IrSq/view?usp=sharing).

The dataset arrangment is listed as follow: 
* **imgs/** : All tiger images (* .jpg).
* **train.csv** : Image names and corresponding ids for training.
* **query.csv** : Image names and corresponding ids of query images.
* **gallery.csv** : Image names and corresponding ids of gallery images.

All the csv files are in the format:

| id | img_name |
|:----------:|:-----:|
| 2 | XXXXX.jpg |
| 3 | YYYYY.jpg |
| 1 | ZZZZZ.jpg |
| 2 | WWWWW.jpg |


> Note that you are **not allowed to** use query.csv and gallery.csv to train your model. Those can only be used to calculate Rank1 to evaluate your performance. 

### Evaluation & Grading 
We use Rank1 to evaluate the model performance. We provide the script to evaluate the performance of your algorithm (`evaluate.py`). One can use the following command to calculate Rank1:
```
python3 evaluate.py --query $1 --gallery $2 --pred $3
```
* `$1` : the path to query.csv (e.g. `query.csv/`).
* `$2` : the path to gallery.csv (e.g. `gallery.csv`).
* `$3` : the path to the predicted csv file. (e.g. `results.csv`)
The baseline score is 60%.


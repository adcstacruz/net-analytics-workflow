# Workflow for iterative network analysis and modeling

ML workflow focused on feature-engineering network/graph data for organized and more collaborative analysis and modeling.

## Problem statement

**TL;DR**: Feature engineering is messy, and might be messier when analyzing network data. This work proposes a simple ML workflow which utilizes scikit-learn's [`Pipeline`](https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html) module and `Custom Transformers` to reduce human errors, enable collaboration, and ease code iterations during the feature engineering process. 

**Context:**
Collaborating with other people when buildng ML-solutions might be complicated, especially during the preprocessing and feature-engineering stage. Rudimentary feature-engineering workflows might be prone to error, time consuming, and difficult to deal with in a collaborative manner.

**Example:** Below is a code (rudimentary base workflow) where we have numerical features in `X_train`, then PCA is performed and the results were used as input for the model.

```python
# transform the data
pca = PCA(n_components=3)
pca.fit(X_train) 
X_train_pca = pca_transform.transform(X_train)

# fit the  model
model = RandomForestClassifier(100)
model.fit(X_train_pca, y_test)

# perform transformation then predict
X_test_pca = pca.transform(X_test)
y_test_pred = model.predict(X_test_pca)

```

- What if:
    - you have decided to perform normalization to specific columns? 
    - you want to include new categorical feature which you need to encode? 
    - you want to explore other models? (some might require different preprocessing strats) 
    - you want to tune the `n_components` hyper-param? 
- Imagine: 
    - the code changes in order to perform these.
    - having hundreds of features requiring different transformations. 
    - having more complex features. 
- Issues:
    - This will be a really messy code (been there). 
    - Difficult to collaborate this with other people.
    - Hard to keep track of the series and parallel transformations done to the raw data.
    - Difficult to deploy and iterate models.
    - Tedious feature engineering process.
- What we need? **Structure** 

**Proposed Solution:** To reduce these issues/complexities, this work proposes an initial workflow where different collaborators can just add different data transformation techniques in model building. In addition, this work will extend on model evaluation and feature analysis.

## Main packages used
* `networkx`:      feature extraction from network/graph data
* `scikit-learn`:  custom transformers, modeling, and etc.
* `shap`:          feature importance

## How to use?

#### 1. Install [Anaconda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/)

#### 2. Create an environment 

```
$ conda create -f environment.yml
```
#### 3. Activate the environment

```
$ conda activate net_analytics_p36
```

#### 4. Add kernel to the notebook

In order to use the environment that was just created, 
```
$ python -m ipykernel install --user --name=net_analytics_p36
```


#### 5. Deactivate environment. Then, open the jupyter notebook under the repo's `notebook` directory. Use the kernel name that was set earlier. 

```
$ conda deactivate
$ jupyter notebook
```


## Current Workflow Components and Development Status

- [x] Initial feature engineering
    - [x] basic transformer for edges
    - [x] basic transformer for community based
- [x] Initial model evaluation
- [x] Model performance analysis
- [ ] Instance analysis
- [ ] Feature importance analysis

Next steps:
- Integration with GIS data
- Include EDA and model analysis based on a use case
- Tailor-fit to my own use case
- Make this Google Colab compatible

## Notes:
- Motivation behind this: I might collaborate with some data scientists to solve a network/gis-based problem
- This work is not intended to build a pipeline/workflow that can do everything. This is more of establishing a structure where people can extend the feature engineering, modeling, analysis, and eval strategies. 

- Current notebook only considered one use case which was adopted from an assignment in [Applied Social Network Analysis in Python](https://www.coursera.org/programs/department-of-science-and-technology-philippines-on-coursera-n6fc2?collectionId=&currentTab=MY_COURSES&productId=ZIVvfx00EeagBBLYvz0q6w&productType=course&showMiniModal=true)

- The structure of the workflow is in a single notebook for now; however, if I see the need to improve the repo structure, this will be changed.
- I focused more on the feature engineering side, I think I need to further establish my use case to determine the EDA and model analysis that needs to be done. 
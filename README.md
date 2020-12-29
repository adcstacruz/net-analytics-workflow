# Pi-graph

### **Workflow for iterative graph analysis and modeling**: 

ML workflow focused on feature-engineering graph/network data for organized, iteration-friendly, and more collaborative network data analysis and modeling.

# Problem statement

**TL;DR**: Feature engineering is messy. Feature engineering network data might be messier. This work proposes an ML workflow which utilizes scikit-learn's [`Pipeline`](https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html) module and `Custom Transformers` to reduce human errors, enable collaboration, and ease code iterations during the feature engineering process. 

**Context:**
Collaborating with other people when buildng ML-solutions might be complicated, especially during the preprocessing and feature-engineering process. Rudimentary pipelines might be prone to error, time consuming, and difficult to deal with in a collaborate manner.

**Example:** Below is a code where we have 3 numerical features in `X_train`, where PCA is performed and the results were used as input for the model.

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

**Issues:** What if you have decided to perform normalization to specific columns? What if you want to acquired new categorical feature which you need to enode? What if I want to use SVM? Imagine the code changes in order to perform these. Imagine having have hundreds of data. Imagine having more complex data. This will be really messy code (been there). Lastly, how can you collaborate this with other people, if even you are having trouble modifying your code during the feature-engineering process. We need stucture. 

**Proposed Solution:** To reduce these issues/complexities, this work proposes an initial workflow where different collaborators can just add different data transformation techniques in model building. In addition, this work will extend on model evaluation and feature analysis.

# Main packages used
* `networkx`:      feature extraction from network/graph data
* `scikit-learn`:  custom transformers, modeling, and etc.
* `shap`:          feature importance

# How to use?

1. Install Anaconda
2. Create an environment 
3. Add kernel to the notebook
4. Open the jupyter notebook under the `notebook` directory

* Create the environent - some graph-based feature extactors used have some issues in the new version of networkx


# Current Workflow Components and Development Status

- [ ] Feature engineering
    - [x] basic column transformer for edges
    - [x] basic column transformer for community based
- [x] Basic model evaluation
- [x] Model performance analysis
- [ ] Instance analysis
- [ ] Feature importance analysis

Next steps:
- Integration with GIS data
- Include EDA and model analysis based on a use case

# Notes:
- This is not intended to be a general workflow. 
    - I am considering only a sample use case because it is quite similar to the problem that I will be solving where I'll follow this the proposed workflow/pipeline of this work.
    - Current use case was based on an assignment in [Applied Social Network Analysis in Python](https://www.coursera.org/programs/department-of-science-and-technology-philippines-on-coursera-n6fc2?collectionId=&currentTab=MY_COURSES&productId=ZIVvfx00EeagBBLYvz0q6w&productType=course&showMiniModal=true)
- The structure of the workflow in a single notebook for now, however, if I can see the need to improve the repo structure, this will be changed.
- I focused more on the feature engineering side, I think I need to further establish my use case to determine the EDA and model analysis that needs to be done. 
# The Data Science Pipline

- The terms and the pipeline itself will most likely vary slightly, depending on where everything was learned, but at its core, it should be the same.

---

## Step One: Planning

- Pretty self explanatory, but there are certain things that should be defined by this phase.

    - The goal

    -  Any deliverables

    - A rough 'How to get there'

### The Goal

- Again, obvious. This is meant to define what your actual goal is, as well as your actual measure(s) of success. Also included are any plans on how to achieve this.

### The Deliverable(s)

- This will be the documentation of the goal, measure of success, and the plan to get there. If you don't define what success looks like to you, you won't know when you're there.

### How to get There

- This will be answered by asking questions about the final product and identifying any inital hypothesis to move forward with.

- Common questions will be something like:

    - What will the end product look like?

    - What format will it be in?

    - Who is it for?

    - What is my MVP (Minimal Viable Product)

- Formulating hypothesis will look something like this:

    - Is attribute 1 (from the actual data) related to attribute 2?

    - How does attribute 3 relate to the target variable?

    - Is the mean of the target variable for subset A significantly different from subset B?

---

## Step Two: Acquisition

- The goal (for this step)

- The deliverable

- How to get there

### The Goal

- You create a path from the original data source to the environment in which you're to be working with the data. In my case, I will acquire my data in such a way that I can work with it in Jupyter Labs.

### The Deliverable

- A file, the acquire.py (or alternatively encapsulated in a wrangle.py), that contans the functions needed to reproduce the acquisition of the data.

### How to get There

- There are any number of ways to get data, however one very common method is pulling the data from a SQL database. If this is used, some amount of refinement of the SQL query is probably necessary before reading the data into the python environment.

-  Another method would be to use Pandas to read the information directly from a csv, or json, txt, xlsx file (among others).

- Web scraping using BeautifulSoup or even Selenium may be used to acquire this data.

---

## Step Three: Preparation

- The goal

- The deliverable

- How to get there

### The Goal

- By the end of exploration you want to have your data split into 2 or 3 subsets (usually 3, but if cross-validation is being used later, then a train/test is optimal). This is done in order to have one sample of the data to use to test our final model, one that wasn't used in the exploration or development of the model, so that we can understand and see how our model works on 'future' unseen data, and determine generality and usefulness from there.

- Before that, the data must be cleaned in a way that we can easily interpret.

- With acquisition, preparation is absolutely one of the most time consuming parts of this process.

### The Deliverable

- As with the acquisition of the data, the deliverable here is a prepare.py file (or encapsulated within the wrangle.py mentioned above) with all of the functions used to clean the data so that the work is reproducible.

- The resulting dataframes from this should be 2 or 3 samples

- If the data is split 3 ways, there will be a train set, made for training the algorithms, a validate to...validate the models developed using the train, and a test set, made to test the data further on completely unseen data, in order to ensure the data can perform on new data and is not overfit. In this case the data splits should be somewhere around 50-60%for the train set, 20-30% for the validate, and around 20% for the test set

- If the data is split in two ways, there will be a train and test set. In this case the train should be roughly 80% and the test 20%. If split in this way there should be another method used to help overcome not having a validate, like cross validation

### How to Get There

- Using various Python libraries to change the data, handle null values, outliers, normalize any text data, changing any data types into something more useful, or any binning required.

- Using matplotlib or seaborn to plot distributions of numeric attributes and target (individually, do NOT compare features to eachother in this way until there is a split of the data to avoid bias)

- Use Scikit-learn to split the data as mentioned above

---

## Step Four: Exploration (and Pre-processing)

- The goal

- The deliverable

- How to get there

### The Goal

- The goal here is to uncover the features that have the largest impact on the target variable, such as something that will drive the target in one direction or another

### The Deliverable

- The first will be a explore.py file that contains any functions needed to reproduce the pre-processing and exploration of the data

- The dataframe resulting from this file should be ready to be used for modeling

- This means that;

    - attributes will be reduced to features

    - features are in a numeric form

    - there are no missing values

    - continuous or categorical values are scaled to be unitless

### How to Get There

- Use python libaries to perform statistical tests to:
    - understand correlations 
    
    - significant differences in variables 
    
    - variable interdependencies
    
    - ect.
    
- Create visualizations that demonstrate relationships across and within attributes and the target variable

- Use domain knowledge and/or information gained through exploration to engineer any useful features

- Remove features that are noisy, provide no actual value, or are redundant

- Use Scikit-learn's preprocessing algorithms (and pd.dummies) like below to turn attributes into features:

    - feature selection
    
    - feature engineering
    
    - dummy variables
    
    - clustering
    
    - scale all data
    
    - create x/y subsets of each dataframe, with x being all of the data except the target variable column and the y being the target variable column
   
---   

## Step Five: Modeling

- The goal

- The deliverable

- How to get there

### The goal

- Create a robust and generalized model that is a mapping between features and the target outcome

### The Deliverable

- A model.py file that contains the functions created for training the model (fitting), predicting the target on new data, and evaluating the results

### How to Get There

- Identify the algorithms most appropriate, such as: 

     - classification 
     
     - regression 
     
     - time-series 
     
     - and others
     
- Build the model:

    - create the model object
    
    - fit the model to the training (or in-sample) observations
    
    - Predict the target value on your train observations
    
    - Evaluate the results on the in-sample predictions
    
    - Repeat as necessary with other algorithms or by tuning hyperparameters
    
    - Use best performing model to predict on the test subset (the out-of-sample observations)
    
    - Evaluate the results on the out-of-sample observations
    
---

## Delivery

- The Goal

- The Deliverable

- How to get there

### The Goal

- Enable others to use what you've created and developed through all previous stages

### The Deliverable (some or all of the below)

- a pipeline.py file that takes new observations from acquisition to prediction using the previously build functions

- A fully deployed model

- A reproducible report and/or presentation with recommendations of actions to take based on the original project goals

- Predictions based upon a specific set of observations

- A dashboard for observing/monitoring the key drtivers (features) of the target variable

### How to Get There

- Tableau for creating a report, presentation, story, or dashboard

- Jupyter Notebook (or similar) for creating the report or a framework to reprocude the research

---


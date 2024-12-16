# ML related

## ML techniques

---

| Aspect |  Overfitting | Underfitting |
| --- |  --- | --- |
| Training Error |  Low |  High|
| Test Error |  High |  High |
| Model Complexity |  Too high |  Too low |
| Generalization |  Poor (memorizes noise) |  Poor (fails to capture patterns) |
| Decision Boundary |  Overly complex |  Overly simplistic |
| Hyperparameter Tuning | Reduce model size, learning rate, or epochs | Increase model size, learning rate, or epochs |
| Regularization | Increase regularization strength |  Reduce regularization or increase model capacity |
| Learning Curves | training and validation losses diverge significantly | both training and validation losses are high |

---

* Over fittied model correction
  * regularization
    * Add a regularization penalty to the loss function to prevent overly complex models
    * L1 Regularization
      * L1 regularization adds a penalty term proportional to the absolute values of the model’s weights to the loss function
      * L1 regularization adds a penalty term proportional to the absolute values of the model’s weights to the loss function
      * You suspect many features are irrelevant or redundant.
      * You want a sparse model with fewer non-zero weights for interpretability and efficiency.

    * L2 Regularization
      * L2 regularization adds a penalty proportional to the squared values of the weights:
      * L2 regularization does not drive weights to zero but instead shrinks them toward smaller values
      * You expect most features to have some contribution to the prediction.
      * You want to reduce overfitting without completely eliminating any features.

    * Dropout
      * Randomly disable a fraction of neurons during training to prevent co-dependencies

    * Early Stopping
  * Improve data Quality
    * Data Augmentation
      * Artificially expand your dataset with transformations (e.g., rotations, flips, cropping).

    * Add more training data
    * Data pre processing
  * Reduce model complexity
  * USer better training
    * Batch normalization
    * Optimize learning rate
  * Evaluate training process
    * Analyze learning curve
    * Increase validation set
  * Perform Cross-Validation
    * Use k-fold cross-validation to train and evaluate your model on different subsets of data, ensuring it generalizes well

* Under fitted model correction
  * Improve Model complexity
    * more complex by using more nueral network layers, or random forests etc
    * increase params
  * Add Interaction or Nonlinear Terms
  * Refine Feature Engineering
    * Remove irrelevant or noisy features
    * Scale or normalize features
  * Tune Hyperparameters
    * Increase the depth, number of estimators, or learning rate for ensemble models like XGBoost or LightGBM.
    * Adjust regularization parameters (e.g., alpha, lambda) to reduce bias in linear or ridge regression models.
  * Collect or Use More Data

## MT training

* Feature selection
  * remove highly corelated features
  * Use Random Forest or Gradient Boosting techniq
  * Recursive Feature Elimination (RFE)
* Dimensionality Reduction
  * faster training , less noice and no overfitting
* Model Optimization
  * small model or smaller nueral netwroks
  * Add L1 or L2 regularization to discourage reliance on less useful features.
  * Batch Size: Increase the batch size to speed up training at the cost of higher memory usage

* Feature Engineering
  * Domain Knowledge: Use insights about the payment system to engineer meaningful features, e.g., payment frequency, transaction patterns, or outlier indicators

* Distributed or Accelerated Training
  * Hardware Acceleration: Use GPUs or TPUs to speed up training

## Custom vs Auto ML

* Benefits of Custom training
  * hyperparameter tuning
  * customize
  * flexible
  * advanced use cases
    > Complex models, specific requirements.

* Benefits of AutoML training
  * ease of use
  * build n deploy without hyperparameters tuning
    > Quick deployment of standard models.

## Misc

* Zip code is `categorical` feature as numeric values has no significance (like greater than or smaller then etc)

* if more "no" than "yes", then `recall` ( true positive rate ) (denom as FP)
  * TP / ( TP + FN )
  * recall improves when false negatives decrease
  * Use when false negatives are more expensive than false positives (FP are easy to handle)
    * search engines
    * fraud detection (to prevent loss by letting in fraud) (most frauds are caught)
    * decease/tumor detection (Medical Diagnosis )
    * Security applications, such as identifying potential threats
    * spam email (to catch all spams) (some good mails into spam)

* if nore "yes" than "no", then `precision` (denom as FN)
  * TP / ( TP + FP )
  * Precision improves as false positives decrease
  * Use when it's very important for positive predictions to be accurate
    * spam email (to avoid false positives) (some spam into Inbox)
    * fraud detection (avoid normal trans being flagged)
    * Medical diagnostics
    * defective apple selection from farms

|  Aspect |  Recall |  Precision|  
|  --- |   --- |  --- |  
| Measures |  how well the model identifies all relevant instances (true positives) | ow many of the model's positive predictions are actually correct |
|  |  TP / ( TP + FN )  |   TP / ( TP + FP ) |
|  Focus | Catching all true positives (minimizing false negatives) | Avoiding false positives |  
| Interpretation | Of all the actual positive cases, how many did the model correctly identify? | Of all the predicted positive cases, how many were truly positive? |
|  When to Prioritize? | When missing positives is costly (eg, detecting diseases) | When false positives are costly (eg, fraud detection) |  
|  What It Measures | Coverage of actual positives | Accuracy of positive predictions |  
|  Effect of Threshold | Recall increases as threshold decreases (more positives predicted) |  Precision decreases as threshold decreases (more false positives)
| when to use  | medical dignosis, spam, seach and rescue | fraud detection, hiring systems, reco system |

* F1 Score: If both precision and recall are important and you need a balance, use the F1 score,
  * F1 Score = 2 * (Precision+Recall) / (Precision⋅Recall)

<https://developers.google.com/machine-learning/crash-course/classification/accuracy-precision-recall>

*

## PL best practises

### ML Dev

* Prepare training data.
  * Store structured and semi-structured data in BigQuery.
  * Store image, video, audio and unstructured data on Cloud Storage.
  * Use Vertex AI Feature Store with structured data.
  * Use Vertex AI TensorBoard and Vertex AI Experiments for analyzing experiments.
  * Train a model within a Vertex AI Workbench instance for small datasets.
  * Maximize your model's predictive accuracy with hyperparameter tuning.
  * Use a Vertex AI Workbench instance to understand your models.
  * Use feature attributions to gain insights into model predictions.

* Data Preparation
  * Use BigQuery to process tabular data.
  * Use Dataflow to process data.
  * Use Dataproc for serverless Spark data processing.
  * Use managed datasets with Vertex ML Metadata.

* ML training
  * Run your code in a managed service.
  * Operationalize job execution with training pipelines.
  * Use training checkpoints to save the current state of your experiment.
  * Prepare model artifacts for serving in Cloud Storage.
  * Regularly compute new feature values.

* Model Serving and deployment
  * Specify the number and types of machines you need.
  * Plan inputs to the model.
  * Turn on automatic scaling.
  * Monitor models by using BigQuery ML.

* ML Wrokflow Orchestration
  * Use Vertex AI Pipelines to orchestrate the ML workflow.
  * Use Kubeflow Pipelines for flexible pipeline construction.
  * Use Ray on Vertex AI for distributed ML workflows.

* Artifact Organization
  * Organize your ML model artifacts.
  * Use a source control repository for pipeline definitions and training code.

* Model Monitoring
  * Use skew and drift detection.
  * Fine tune alert thresholds.
  * Use feature attributions to detect data drift or skew.
  * Use BigQuery to support model monitoring.

​

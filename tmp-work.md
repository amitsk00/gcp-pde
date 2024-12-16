# will/should be moved sooner


## DataProc

* primary workers are non-preemptible, secondary are preemptible 
'''shell
gcloud dataproc clusters update with the --num-secondary-workers parameter
'''

* FetchFailedException exception - while scaling down when shuffle data maybe lost



## Data Catalog - new one to study

* can automatically extract metadata from sources including Cloud Storage, BigQuery, Cloud Bigtable, Cloud Pub/Sub, and Google Sheets
* service designed for **data discovery** and metadata management



## Custom ML

* custom training allows for tuning hyperparameters
* AutoML training tunes hyperparameters for you (on its own)


## Data Studio

* Extracted data sources are snapshots and can provide better performance than live data
* There is no imported data source


## FireStore

* Indexes: 
    * auto create - `Atomic values, ascending` and `Atomic values, descending`
    * There isn't a hash index type in Cloud Firestore
    * Composite index needs to be created manually - always with mult columns



## ML

### Precision


### Recall


### L1/L2 regularization



## Redis vs Memcached



## Generic

* BigQuery BI Engine is an in-memory analytics engine

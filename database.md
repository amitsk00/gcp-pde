# Database options

## DataSTore

* mongoDB like document DB
* it has `kind > entity > property`
  * kind as table
  * entity as row
  * Property as column
  * Key as primary key

## FireStore

* Indexes
  * auto create - `Atomic values, ascending` and `Atomic values, descending`
  * There isn't a hash index type in Cloud Firestore
  * Composite index needs to be created manually - always with mult columns

* index is mandatory as *no scan posisble* otherwise
  * single (atomic / built in on all fields) or composite (needs to be created manually)

## Spanner

* avoid hot spotting
  * dont use auto incr number or timestamp as key
  * use `V4 UUID` as key
  * use shard and ur own value as custom prim key (for sequential data)

## BigTable

### Access controls

* using access control at the project level:
  * Allow a user to read from, but not write to, any table within the project.
  * Allow a user to read from and write to any table within the project, but not manage instances.
  * Allow a user to read from and write to any table within the project, and manage instances

* using access control at the instance level include the following:
  * Allow a user to read from any table in only one instance in a project that has multiple instances.
  * Allow a user to manage only one instance in a project that has multiple instances

* access control at the table level include the following:
  * Allow a user to write to a table but not read from the table.
  * Allow a user to read from a table but not write to the table

* access control at the authorized view level include the following:
  * Let a user read an authorized view but not modify it.
  * Let a user view data from only one of multiple authorized views of a table

### Roles

* Bigtable Administrator (roles/bigtable.admin)
* Bigtable Reader (roles/bigtable.reader)
  * read-only access to the data stored within Bigtable tables.
  * Intended for data scientists, dashboard generators, and other data-analysis scenarios
* Bigtable User (roles/bigtable.user)
  * read-write access to the data stored within Bigtable tables.
  * Intended for application developers or service accounts.
* Bigtable Viewer (roles/bigtable.viewer)
  * no data, onlu list/get

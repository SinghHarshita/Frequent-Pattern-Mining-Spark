# Frequent-Pattern-Mining-Spark
PCY Algorithm for Frequent Pattern Mining using Pyspark

## About Dataset
The dataset is downloaded from kaggle.
It has 38765 rows of the purchase orders of people from the grocery stores. 
These orders can be analysed and association rules can be generated.

## Details on Implementation
PCY algorithm is an improvement of the Apriori algorithm. We have also added the Multihash optimization in the implementation. PCY finds frequent itemsets by making several passes over a dataset.
1. In the first pass, It keeps track of the occurrences of each singleton (It counts how many each individual item appears in the dataset). Additionally, it hashes pairs that appear in the dataset to 2 different HashTables.
2. After the 1st pass, We filter our singletons (We keep only the frequent items of our dataset). To decide if an item is frequent, we define a threshold (support) for each time. If an item appears in the dataset more than the threshold, then it's considered frequent. We also filter HashTables by converting them to bitmaps.
In the second pass, we count the candidate pairs. An pair {i, j} I is counted if the following conditions are met:
    * Both i and j are frequent items.
    * {i, j} is hashed in a frequent bucket in both hashtables.
3. In that way, we reduce the number of counters we have to count, so we dramatically reduce the memory used in our program.

### Implementation Using Apache Spark
1. For preprocessing Spark dataframe is used.
2. In implementation of the PCY algorithm, Spark RDD is used.

##Scalable Machine Learning

######Lecture 4 Spark Essentials######
1. Iterative algorithms/jobs involve lots of disk I/O for each repetition. Spark keeps data in memory. 
2. A spark program runs on two programs, _a driver program_ and _a workers program_.
3. **SparkContext**
    1. ipython and program must use a constructor to create a new **SparkContext**
    2. Use SparkContext to create RDDs
    3. The **master** parameter for a SparkContext determines which type and size of cluster to use
4. **Resilient Distributed Datasets**(RDD)
    1. primary abstraction in spark
        * Immutable once constructed
        * track lineage information to recompute the lost data efficiently
        * enable operations on collections of elements in parallel
    2. how to construct RDDs
        * construct from existing python collections(list)
        * transforming from an existing RDD
        * read from HDFS or other storage system
5. RDDs
    1. Transformation
    
    2. Actions

######Functions
1. Higher Order Functions
    1. The function name is a variable pointing to the function iteself.
    2. passing functions as arguments to other functions
    3. **[First-class Function](https://en.wikipedia.org/wiki/First-class_function)**: treat functions as first-class citizens. 
        1. pass functions as arguments to other functions
        2. return functions as values from other functions
        3. assign functions as variables and store them into data structure

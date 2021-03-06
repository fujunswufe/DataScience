##Scalable Machine Learning

######Lecture 4 Spark Essentials######
1. Iterative algorithms/jobs involve lots of disk I/O for each repetition. Spark keeps data in memory. 
2. A spark program runs on two programs, _a driver program_ and _a workers program_.

3. **SparkContext**
    1. ipython and program must use a constructor to create a new **SparkContext**
    2. Use SparkContext to create RDDs
    3. The **master** parameter for a SparkContext determines which type and size of cluster to use
    4. **sc.parallelize()**: 
        * first argument: create a new set of input data based on data that is passed in.
        * second argument: tells Spark how many partitions to break the data into when it stores the data in memory.

4. **Resilient Distributed Datasets**(RDD)
    1. primary abstraction in spark
        * Immutable once constructed
        * track lineage information to recompute the lost data efficiently
        * enable operations on collections of elements in parallel
    2. how to construct RDDs
        * construct from existing python collections(list)
        * transforming from an existing RDD
        * read from HDFS or other storage system

5. RDDs: we can cache RDDs for later use
    1. **Transformation**: lazy evaluation which means that transformations are only executed when actions are called
        1. Key-Value Transformation
            * reduceByKey(func): gathers together pairs that have the same key and applies a function to two associated values at a time. Combine output with common keys before shuffling data across nodes.
            * sortByKey()
            * groupByKey():  Only use groupByKey() if the operation would not benefit from reducing the data before the shuffle occurs.
            * combineByKey()
            * foldByKey() 
        2. map(func)
        3. flatMap(func)
        4. filter(func)
        5. distinct([numTasks]))
        6. mapValues(func)
        7. mapPartitions()
        8. mapPartitionsWithIndex()
        
    2. **Actions**: get results out of spark
        * first(): returns the first element of an RDD
        * take(n): return the first n elements of the RDD
        * takeSample()
        * takeOrdered(n, key = func) : returns the first n elements of the RDD, using either their natural order or a custom comparator. (returns the list sorted in ascending order and results is deterministic)
        * top(): similar to takeOrdered() except that it returns the list in descending order
        * collect()
        * count()
        * countByValue()
        * reduce(func): take two parameters and return a single value
        * takeSample(): returns an array with a random sample of elements from the dataset. (_takes in a **withReplacement** argument_)
        * Note that for the first() and take() actions, the elements that are returned depend on how the RDD is partitioned.
        * 
    3. **Cache**: cache RDD in memory for future reuse
        * cache()
        * unpersist(): inform Spark that you no longer need the RDD in memory
        * id()
        * setName()
    4. spark also support **Key-Value pair** RDDs
    
6. Shared Variables
    1. Broadcast Variables: read-only, sent to each worker once and cached on workers. Actions: each task’s update to accumulator is applied only once	
    2. Accumulators: write-only, only the driver can read accumulator's value.

######Functions
1. Higher Order Functions
    1. The function name is a variable pointing to the function iteself.
    2. passing functions as arguments to other functions
    3. **[First-class Function](https://en.wikipedia.org/wiki/First-class_function)**: treat functions as first-class citizens. 
        1. pass functions as arguments to other functions
        2. return functions as values from other functions
        3. assign functions as variables and store them into data structure
2. An [anonymous function](https://en.wikipedia.org/wiki/Closure_(computer_programming)#Anonymous_functions) is a function literal without a name, while a closure is an instance of a function, a value, whose non-local variables have been bound either to values or to storage locations 
######Closure
3. **[Closure](https://en.wikipedia.org/wiki/Closure_(computer_programming)#First-class_functions)**: Operationally, a closure is a record storing a function together with an environment: a mapping associating each free variable of the function (variables that are used locally, but defined in an enclosing scope) with the value or storage location to which the name was bound when the closure was created

###04/13/2016 
####[A Deeper Understanding of Spark Internals](https://spark-summit.org/2014/talk/a-deeper-understanding-of-spark-internals)
1. Acutally, spark is the optimization of data stream. 
2. The performance is about (computing time + shuffle time + dispatch time) / \# of Parallelism
3. Execution model:
    * Create **DAG of RDDs** to represent computation, which is Spark _transformations_ and _actions_.
    * **Create logical execution plan for DAG**. Pipeline as much as possible and Split into "stages" based on need to reorganize data
    * Schedule and execute individual tasks. _Execute all tasks within a stage before moving on_
4. Notice:
    * Enough partitions for concurrency
    * **Minimize memory consumptions**, for example avoiding use groupByKey() and sortByKey(). A single key-value pair may not fit into memory.
    * Minimize data shuffle
    * Know the standard library
5. **Dive into Spark data stream flow**.

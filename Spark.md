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
5. RDDs: we can cache RDDs for later use
    1. Transformation: lazy evaluation which means that transformations are only executed when actions are called
        1. Key-Value Transformation
            * reduceByKey(func)
            * sortByKey()
            * groupByKey()
        2. map(func)
        3. filter(func)
        4. flatMap(func)
        5. distinct([numTasks]))
        6. mapValues(func)
    2. Actions: get results out of spark
        1. reduce(func)	
        2. take(n)	
        3. collect()
        4. takeOrdered(n,key=func)	
    3. spark also support **Key-Value pair** RDDs
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
3. 
4. Notice:
    * Enough partitions for concurrency
    * **Minimize memory consumptions**, for example avoiding use groupByKey() and sortByKey(). A single key-value pair may not fit into memory.
    * Minimize data shuffle
    * Know the standard library

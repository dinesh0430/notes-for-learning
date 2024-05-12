# Spark

Apache Spark™ is a multi-language engine for executing data engineering, data science, and machine learning on single-node machines or clusters.

**Structured Data**: This includes data with a well-defined schema, like tables in a relational database. Spark supports common data formats like CSV, JSON, Parquet, ORC, and Avro. It can also interact with data warehouses through JDBC/ODBC connections.

**Unstructured Data**: Spark can handle text files, log files, sensor data, and even images and audio (though these would require specialized libraries).


### Spark vs Hadoop (Map Reduce) (from Reddit)

Spark vs Hadoop, is indeed unfair comparison. Historically Hadoop consisted of two layers: storage (mostly HDFS) and processing (for simplicity MapReduce). That said it would make sense to compare Spark with MapReduce, as those two are processing frameworks capable of processing data stored on some kind of storage (most likely but not limited to HDFS).

The main difference between MR and Spark is that latter is memory centric (remember that disk splits is a thing) through it resilient distributed dataset (RDD) data structure, and by that is more suitable for multistage and/or iterative workloads. One could (and people did) write a book at differences between MR and Spark, but in a nut shell - MR has to write output of each job to storage (HDFS), and in next stage read it in again and so on, this part (serialisation/write/read/deserialisation) is very expensive. While Spark will try to keep data in memory and reuse/recompute if necessary thus making the data available for processing much much faster.



### Apache Spark vs Hadoop (Map Reduce) (from Gemini AI)

**Spark**

Pros:

Speed: Spark is significantly faster than MapReduce due to in-memory processing. It can store intermediate data in memory, reducing disk I/O operations.
Versatility: Spark is not limited to batch processing like MapReduce. It can handle real-time data processing with Spark Streaming and supports various functionalities like machine learning through MLlib.
Ease of Use: Spark offers APIs in Python, Scala, and Java, making development easier compared to the Java-centric approach of MapReduce. Spark also provides an interactive shell for development and exploration.

Cons:

Resource Intensive: Due to its in-memory processing, Spark requires more RAM and computational resources compared to MapReduce.
Security: While improving, Spark's security features are still considered less robust than MapReduce's established security protocols.

**MapReduce**

Pros:

Scalability: MapReduce excels at handling extremely large datasets that may not fit in memory entirely. It efficiently distributes tasks across clusters of machines.
Maturity: MapReduce is a more mature technology with a longer track record and established security features.
Cost-effective: Since it relies less on memory, MapReduce can be more cost-effective for processing massive datasets on commodity hardware.

Cons:

Speed: MapReduce's reliance on disk storage makes it slower than Spark, especially for iterative tasks involving multiple passes over the data.
Limited Functionality: MapReduce is primarily focused on batch processing large datasets. It's less versatile for other big data tasks like real-time analytics or machine learning.
Development Complexity: Programming MapReduce jobs involves writing Java code for the Map and Reduce phases, which can be more complex than using Spark's APIs.
Choosing Between Spark and MapReduce:

For speed, in-memory processing, and versatility across various data processing needs, Spark is the preferred choice.
For processing massive datasets that may not fit in memory entirely, where cost-effectiveness and established security are priorities, MapReduce remains a good option.
In many cases, Spark can be integrated with Hadoop, the ecosystem where MapReduce originated, allowing you to leverage Spark's strengths while still utilizing Hadoop's distributed storage capabilities


### Spark Architecture
![image](https://github.com/dinesh0430/notes-for-learning/assets/32917000/0db19a99-e644-4053-9677-cde17635b4e6)

The architecture of Spark is based on two main abstraction layers, which are given below.

Resilient Distributed Dataset (RDD) and Directed Acyclic Graph (DAG)
 
Let us discuss these two layers before starting to learn about Spark architecture.

**Resilient Distributed Dataset (RDD)**

RDD is an essential building block of Spark. It is a key data computation tool and an interface for immutable data. It is a data structure that is useful to recompute data in case of failure. RDD includes all sorts of Python, Scala, or Java objects for users to use

Each dataset in RDD is divided into logical partitions. These partitions are stored and processed on various machines of a cluster.

The concept of RDD in Spark is to achieve a fast and more efficient MapReduce operation.
Using RDDs, one can perform two types of operations:

1.Transformations: These are the set of operations that are applied to create a new RDD from the existing RDDs. It takes one RDD as an input and produces one or more RDD as an output.

2.Actions: Actions are the operations that trigger a Spark job to perform computations on the dataset. After the computations are done, the result is sent to the Spark driver program.

**Directed Acyclic Graph (DAG)**

In Spark, DAG is the logical flow of plans that need to be applied to data to achieve the desired outcome. The DAG can be broken down as follows:

**Directed**: It means a direct connection from one node to another. 
 
**Acyclic**: It means that there are no cycles or loops present. Whenever a transformation occurs, it cannot return to its earlier state.
 
**Graph**: A graph is a combination of vertices and edges. Here vertices represent the RDDs, and the edges, represent the operation to be applied to the RDDs.
 
DAG helps Spark to optimize executions, achieve parallelism, and provide fault tolerance.

---

**Master Node**: The master node contains the driver program which executes our apps. When the driver program executes, it calls the original program of the app and generates a Spark Context. Spark Context includes all the basic functions. You can assume Spark Context as a gateway to all Spark's functionality. Every task that you perform on Spark always goes through the Spark Context. 

**Cluster Manager**: The cluster manager works with the Spark Context and manages the execution of various jobs inside the cluster. The cluster manager is the resource manager of Spark apps. Its task is to allocate resources and schedule tasks across all the worker nodes. It can be Spark's standalone cluster manager or some other third-party cluster manager such as Apache Mesos or Hadoop Yarn.

Now, the job gets broken down into smaller jobs and distributed to all the worker nodes. These worker nodes can also process the RDDs created in the Spark Context, and results can also be cached.

**Worker Node**: The worker nodes act as a slave and execute various tasks assigned to them by the master node. The Spark Context breaks a job into multiple tasks and distributes them to the worker node. The tasks then work on the partitioned RDD, and after collecting the results of various operations, they are returned to the main Spark Context. The executor’s job is to run all the tasks and store the data during execution. All the cache is stored in the Spark executor’s memory


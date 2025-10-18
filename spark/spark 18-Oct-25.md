# Spark Heirarchy

The information comes from the youtube video: Apache Spark Core—Deep Dive—Proper Optimization Daniel Tomes Databricks [https://www.youtube.com/watch?v=daXEp4HmS-E]
<img width="1193" height="804" alt="image" src="https://github.com/user-attachments/assets/9cf6f7f1-5214-4d63-a5b9-fa6842adf6be" />

Apache Spark was designed to overcome the limitations of Hadoop MapReduce, which writes intermediate data to disk after each map/reduce step.

Spark, on the other hand, keeps intermediate data in memory (RAM) as much as possible. But it would still need disk storage if a spill (data doesn't fit in the memory) happens or when a shuffle is required.

<img width="1609" height="758" alt="image" src="https://github.com/user-attachments/assets/1e091f01-9f7d-4fa9-b64e-6931b287d1ea" />

Action triggers a Job
→ Job is divided into Stages (based on shuffles)
→ Each Stage runs multiple Tasks (one per partition)

Difference between HIVE partitions and Spark Partitions, why they are not the same.

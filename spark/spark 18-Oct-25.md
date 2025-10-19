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

<img width="1155" height="796" alt="image" src="https://github.com/user-attachments/assets/3f61020c-b31c-4ed5-8e13-a5aad8a9e172" />

<img width="1596" height="788" alt="image" src="https://github.com/user-attachments/assets/c648c99b-a023-4a9b-a245-7cc6b3151fa9" />

<img width="1700" height="876" alt="image" src="https://github.com/user-attachments/assets/3ff1b9c1-97da-4e6d-a09b-efd767b565f9" />


Try to avoid NOT IN instead always prefer NOT EXISTS or left anti joins — they’re much more efficient and behave better with NULLs. Using NOT IN might result in Spark using Broadcasted Nested Loop Join which is not preferred. Look at the time taken below 7.1 min vs 16 sec.

1️⃣ <> → Standard “not equal” operator

This is the ANSI SQL–style not equal operator.

It returns NULL if either operand is NULL, because NULL means “unknown.”

Example:
SELECT 1 <> 2;   -- true
SELECT 2 <> 2;   -- false
SELECT NULL <> 2;   -- NULL
SELECT 2 <> NULL;   -- NULL
SELECT NULL <> NULL;   -- NULL


So in expressions, if one side is NULL, the result is NULL (unknown) —
not true or false.

2️⃣ <=> → NULL-safe equal operator

<=> is Spark’s “null-safe equal” operator.

It returns true if both sides are NULL, and false only if the values are actually different.

You can think of it as a safe version of = that treats NULL = NULL as TRUE.

Example:
SELECT 1 <=> 1;     -- true
SELECT 1 <=> 2;     -- false
SELECT NULL <=> 2;  -- false
SELECT 2 <=> NULL;  -- false
SELECT NULL <=> NULL;  -- true ✅


So unlike =, it won’t return NULL when comparing NULLs — it returns a boolean.

<img width="1153" height="645" alt="image" src="https://github.com/user-attachments/assets/a5bf5821-6490-4072-be06-c388e41d3b16" />


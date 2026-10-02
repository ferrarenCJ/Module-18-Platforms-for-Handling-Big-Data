# Self-Study Discussion 18.1: Thinking Like a Data Scientist - Platforms for Handling Big Data

One resource that I found particularly helpful during this module was the Hadoop tutorial provided by Guru99:

https://www.guru99.com/create-your-first-hadoop-program.html

This resource provides a step-by-step walkthrough of setting up Hadoop, understanding HDFS, creating Java MapReduce programs, compiling source code, creating JAR files, and executing MapReduce jobs. The examples are beginner-friendly and include screenshots, commands, and explanations that make it easier to understand how data moves through the Hadoop ecosystem.

Another resource I found useful was the Apache Hadoop documentation:

https://hadoop.apache.org/docs/stable/

The official documentation contains detailed information about Hadoop architecture, HDFS, YARN, MapReduce, and ecosystem components. I frequently used it to better understand the relationship between NameNodes, DataNodes, resource management, and distributed processing.

One tip that helped me complete the coding activities and final assignment was to verify HDFS operations at each stage rather than waiting until the end. Commands such as:

```bash
hdfs dfs -ls /
hdfs dfs -ls /inputMapReduce
hdfs dfs -head filename
hdfs dfs -tail filename
```

made it much easier to identify issues before running a MapReduce job. I also found that reviewing Hadoop job output statistics, such as Map Input Records, Reduce Output Records, and job completion messages, helped confirm that processing completed successfully.

These resources helped me better understand Hadoop architecture, HDFS storage, Java-based MapReduce processing, and the practical steps required to deploy and execute Hadoop applications within Docker containers. I have bookmarked both resources and plan to continue using them throughout future data engineering projects involving distributed computing and big data analytics.
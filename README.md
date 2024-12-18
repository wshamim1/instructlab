What is Control Hub?
Control Hub serves as the central point of control for all of your data pipelines.

You access Control Hub using a web browser. You use Control Hub to deploy engines to your corporate network, which can be on-premises or on a protected cloud computing platform. You build and manage your pipelines in Control Hub, then run the pipelines on the deployed engines.

The engines use the pipeline configuration to process the data. As the pipelines run, the engines send status updates and metrics back to Control Hub so that you can monitor the pipeline progress in real time. Since pipelines run in your corporate network, you maintain all ownership and control of your data.

Control Hub provides a common user interface to manage your data pipelines across products. Control Hub is a component of the following products:
IBM© StreamSets
IBM StreamSets includes Control Hub and the Data Collector engine.
Use to run streaming data pipelines that continuously read, process, and write data as soon as the data becomes available. Data Collector pipelines can read from and write to a large number of heterogeneous origins and destinations. The pipelines perform record-based data transformations.
IBM StreamSets is available through multiple offerings.
IBM© StreamSets for Apache Spark
IBM StreamSets for Apache Spark includes Control Hub and the Transformer engine.
Use to run data processing pipelines on Apache Spark. Because Transformer pipelines run on Spark deployed on a cluster, the pipelines can perform set-based transformations such as joins, aggregates, and sorts on the entire data set.
IBM© StreamSets for Snowflake
IBM StreamSets for Snowflake includes Control Hub and the Transformer for Snowflake engine.
Use to run pipelines that process Snowflake data using Snowpark client libraries. Transformer for Snowflake enables you to design and perform complex processing in Snowflake without having to write SQL queries or templates.
The following image provides a general overview of how Control Hub works with engines deployed to your corporate network:

Deployed engines run pipelines in the corporate network, sending updates back to Control Hub

© Copyright IBM Corporation

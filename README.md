Connection is developed by W Shamim From AAAAAAA.
We can create connections for S3, AS3, AAS3.
OverviewA connection defines the information required to connect to an external system.
Getting Started with Connections
Expressions in Connection PropertiesSome connection properties allow you to specify an expression using the IBM StreamSets expression language.
Securing ConnectionsConnections require sensitive information, such as user names or passwords, to access data in external systems.
Connection TagsA connection tag identifies similar connections. Use connection tags to easily search and filter connections when viewing them in the Connections view. For example, you might want to group connections by the origin system or by the test or production environment.
Using Connections in Pipeline FragmentsYou can use connections in pipeline fragments to design pipeline fragments as your data sources. When you use connections in fragments, you reduce the possibility of user errors when defining connection information and you standardize the processing logic for the data sources.
Managing Connections
Overview
A connection defines the information required to connect to an external system.

Note: Connections are recommended for Data Collector and Transformer pipelines and for Transformer for Snowflake pipelines that run on a deployed engine. They are not applicable for Transformer for Snowflake pipelines that run on the IBM StreamSets hosted engine.
Pipelines communicate with external systems to read and write data. Most of these external systems require sensitive information, such as user names or passwords, to access the data. When you configure pipelines and pipeline fragments, you can enter the details needed to connect to the external system, or you can select an existing connection that contains the details.

Using connections provides the following benefits:
Increased security
When you use connections, you can limit the number of users that need to know the security credentials for external systems.
For example, you want to ensure that only the DevOps team knows the security credentials required to access external systems. A DevOps engineer logs into Control Hub to create all connections to the external systems, and then shares the connections with data engineers who design pipelines, granting them the ability to use the connections. Data engineers select the appropriate connection name for a pipeline stage, but cannot view the connection details.
Reusability
You can create a connection once and then reuse that connection in multiple pipelines. Reusing connections reduces the possibility of user errors and simplifies updates to connection values.
For example, you might create a single connection to your source data stored in Amazon S3. You name the connection SourceData. You develop multiple pipelines to process this source data. Each time you add an Amazon S3 origin to a pipeline, you simply select the existing SourceData connection. You do not need to re-enter the AWS authentication details for each Amazon S3 origin. When you need to update the authentication details, you make a single update to the connection. All Amazon S3 origins using that connection reflect the updated values in subsequent pipeline runs.
For more information on the supported connection types, see Connection Types Overview.

Understanding Standard and Engineless Connections
When you create a connection, you can create a standard or engineless connection:

Standard connections
A standard connection is associated with an authoring Data Collector in your organization. The Data Collector version and the stage libraries installed on the engine determine the connection types that you can create and the properties available in the connection.
Create a standard connection when you want full control of available connection types and properties.
For example, suppose you have an authoring Data Collector version 5.5.0 that includes the Snowflake stage library. You can create a Snowflake connection with this authoring Data Collector and use the connection in Snowflake stages in your Data Collector pipelines.
When you edit a standard connection, you can change the authoring Data Collector associated with the connection. You cannot change a standard connection to an engineless connection at this time.
In the previous example, if you want the Snowflake connection associated with an authoring Data Collector version 5.5.0 to use OAuth authentication, you need to upgrade the connection to use an authoring Data Collector version 5.6.0 or later because OAuth authentication was added to the Snowflake connection with Data Collector 5.6.0.
When you configure a standard connection, you can test to see if it connects to the specified system as expected.
For more information about version requirements for different connection types and functionality, see Connection Requirements.
Engineless connections
An engineless connection is not associated with a Data Collector engine in your organization. When you create an engineless connection, the connection uses the stage libraries available in the latest Data Collector version.
Create an engineless connection when you want easy access to the latest Data Collector stage libraries. Engineless connections can be especially useful when you want to create Transformer or Transformer for Snowflake pipelines and you do not have the necessary Data Collector engine version.
An engineless connection uses the Data Collector version that it was created with by default. When needed, you can configure the connection to use an available authoring Data Collector in your organization, changing the engineless connection to a standard connection.
For example, suppose you create an engineless Amazon connection that uses Data Collector 6.0.0, and the next Data Collector release includes support for a new Amazon authentication-related property. If you want to configure the new property, you can edit the connection and select an appropriate authoring Data Collector in your organization, converting the connection to a standard connection. Otherwise, the connection continues to use Data Collector 6.0.0 stage libraries and functionality.
Note: You cannot test an engineless connection during connection configuration. To test if an engineless connection works as expected, you can configure a pipeline to use the connection, then perform a draft run or create and run a job.
Connection Requirements
Before you configure a connection, note the following requirements:

Use an appropriate Data Collector version to create connections
When you create a standard connection, you must select an available authoring Data Collector version 4.0.0 or later.
The Data Collector version and the stage libraries installed on the engine determine the connection types, such as Amazon S3 or JDBC, that you can create and the properties available in the connections.
For example, to use a MongoDB Atlas connection, you must use an authoring Data Collector version 5.2.0 or later, and have the MongoDB Atlas stage library installed on the engine. Similarly, to use Azure Managed Identity authentication in an Azure connection, you must use an authoring Data Collector version 5.5.0 or later and have the Azure stage library installed.
When you create an engineless connection, the connection uses the latest Data Collector version. When you update an engineless connection, the connection automatically upgrades to the latest Data Collector version unless you select an authoring Data Collector in your organization.
For a list of new connection types and properties supported with each Data Collector version, see Data Collector Versions.
Pipelines with the appropriate engine version can use connections
After creating connections, you can use those connections in pipelines.
For Data Collector and Transformer pipelines, the engine version that runs the pipeline must support the selected the connection type, and have the required stage library installed.
For example, say you create an Amazon S3 connection, using Data Collector version 4.0.0 with the Amazon Web Services stage library installed. You can use this connection in a Transformer pipeline, as long as you design and run the pipeline using Transformer version 4.0.0 or later with the Amazon Web Services stage library installed.
For Transformer for Snowflake, the engine version that runs the pipeline must support the selected connection version. For details, see Transformer for Snowflake Versions.
Using connections in pipelines requires the following minimum engine versions:

Data Collector version 4.0.0 or later
Transformer version 4.0.0 or later
Transformer for Snowflake version 5.0.0 or later
Later versions introduce support for additional connection types, as listed below:
Data Collector Versions
Transformer Versions
Transformer for Snowflake Versions

Data Collector Versions
The Data Collector version associated with a connection determines the connection types that you can create and the properties available in each connection.

Connection support was initially introduced with Data Collector 4.0.0. Later versions introduce support for additional connection types and properties.

The following table lists the new connection types and properties supported with each Data Collector version. Later Data Collector versions support all previously introduced connections and connection properties, unless stated otherwise:
Engine Version	New Connection Types or Properties
Data Collector 5.11.0	
Web Client
Data Collector 5.10.0

Snowflake support for optionally defining the warehouse, database, and schema.
Data Collector 5.9.0

Teradata
Data Collector 5.8.0

Couchbase
Data Collector 5.6.0

Aerospike
Snowflake support for the following features:
Private key file authentication
Private key content authentication
OAuth authentication
Private link URL
Orchestrator
Data Collector 5.5.0	
Azure Data Lake Storage Gen2 support for Azure Managed Identity authentication
Data Collector 5.4.0

CONNX
Data Collector 5.2.0

MongoDB Atlas
Data Collector 5.1.0	
Kafka support for custom authentication
Data Collector 5.0.0

Hive
MQTT
OPC UA Client
Data Collector 4.4.0

Amazon S3 support for custom endpoints
CoAP Client
Influx DB
Influx DB 2.x
Pulsar
Data Collector 4.2.0

Cassandra
SFTP/FTP/FTPS support for using a proxy to connect to the remote server
Data Collector 4.1.0

Amazon Redshift
MongoDB
RabbitMQ
Redis
Data Collector 4.0.0

Amazon Kinesis Firehose
Amazon Kinesis Streams
Amazon S3
Amazon SQS
Azure Data Lake Storage Gen2
Azure Synapse - Requires the Azure Synapse Enterprise stage library version 1.2.0 or later.
Databricks Delta Lake - Requires the Databricks Enterprise stage library version 1.2.0 or later.
Elasticsearch
Google BigQuery
Google Cloud Storage
Google Pub/Sub
JDBC
JMS
Kafka
Kudu
MySQL
Oracle
PostgreSQL
Salesforce
SFTP/FTP/FTPS
Snowflake - Requires the Snowflake Enterprise stage library version 1.7.0 or later.
Snowpipe - Requires the Snowflake Enterprise stage library version 1.7.0 or later.
SQL Server
Transformer Versions
The Transformer version determines the connection types that you can use in Transformer pipelines and the properties available in each connection.

Using a connection with Transformer pipelines requires creating a standard connection with an authoring Data Collector of an appropriate version or creating an engineless connection.

Connection support was initially introduced with Transformer 4.0.0. Later versions introduce support for additional connection types and properties.

The following table lists the connection types and properties supported with each Transformer version. Later Transformer versions support all previously introduced connections and connection properties, unless stated otherwise:
Engine Version	Connection Types or Properties
Transformer 6.0.0

Elasticsearch support removed with the removal of the Elasticsearch destination.
Transformer 5.8.0

Snowflake support for optionally defining the warehouse, database, and schema.
Using this feature requires Data Collector version 5.10.0 or later.

Transformer 5.7.0

Amazon EMR Cluster Manager support for using AWS Service Catalog to provision a cluster.
Using this feature requires Data Collector version 5.10.0 or later.

Transformer 5.4.0

Amazon EMR Cluster Manager support for specifying a cluster by name and tags.
Amazon EMR Serverless support for specifying an application by name and tags.
Using these features requires Data Collector version 5.4.0 or later.

Transformer 5.3.0

Amazon EMR Serverless - Creating this connection type requires Data Collector version 5.3.0 or later.
Transformer 4.0.0

Amazon EMR Cluster Manager
Amazon Redshift - Creating this connection type requires Data Collector version 4.1.0 or later.
Amazon S3
Elasticsearch
JDBC
Kafka
Kudu
MySQL
Oracle
PostgreSQL
Snowflake - Requires the Snowflake Enterprise stage library version 1.7.0 or later.
SQL Server
Transformer for Snowflake Versions
When your organization uses Transformer for Snowflake deployed engines, you use Snowflake connections to provide connection information for the pipelines.

Using a connection with Transformer for Snowflake pipelines requires creating a standard connection using an authoring Data Collector of an appropriate version or creating an engineless connection.

The Transformer for Snowflake version determines the connection versions that you can use in the pipelines, and the properties available in each connection. Connection support was initially introduced with Transformer for Snowflake 5.0.0. Later versions introduce support for additional functionality.

The following table lists the connection version and properties supported with each Transformer for Snowflake version. Later Transformer for Snowflake versions support all previously introduced functionality, unless stated otherwise:

Engine Version	Connection Type or Properties
Transformer for Snowflake 5.6.0

Snowflake connection support for OAuth authentication
Transformer for Snowflake 5.0.0

Snowflake connection
Using this connection requires Data Collector version 5.10.0 or later.

Working with Connections
The Connections view lists all connections that you have access to.

You can complete the following tasks in the Connections view:
Create connections.
Assign tags to connections.
Test that configured connection values are valid.
View connection details, including the connection type, assigned tags, and the list of pipelines and pipeline fragments that use the connection.
Edit connection details.
Duplicate connections.
Share connections with other users and groups.
Delete connections.
The following image shows a list of connections in the Connections view. Each connection is listed with its name, type, tags, and creator.
Tip: To resize, hide, or reorder the columns, see Customizing Table Columns.


Note the following icons that display for connections when you select a connection. You'll use these icons frequently as you manage connections:

Icon	Name	Description
	Add	Add a connection.
	Refresh	Refresh the list of connections.
	Toggle Filter Column	Toggle the display of the Filter column, where you can filter connections by connection type or tag. You can also search for connections by name or description.
	Share	Share connections with other users and groups, as described in Permissions.
	Delete	Delete the connection.


 Securing Connections
Connections require sensitive information, such as user names or passwords, to access data in external systems.

To ensure that this sensitive information is not compromised, use roles and permissions to secure connection objects and use credential stores or runtime resources to secure connection values.

Secure Connection Objects
To secure connection objects, use roles and permissions as follows:
Grant a small set of DevOps engineers the Connection Editor role and Write permission on connections. With this access, a user has full access to connection objects. The user can create and edit connections in the Connections view.
Grant data engineers who design pipelines the Connection User role and Read permission on connections. With this access, a user can select the connection name when configuring a pipeline or fragment, but cannot view the connection values.
For more information, see Roles and Permissions.

Secure Connection Values
To secure connection values, use one of the following methods when you define connection properties:
Credential stores
To use credential stores, you add the sensitive values as secrets in an external credential store system, such as AWS Secrets Manager or Azure Key Vault. Then you use credential functions in connection properties to retrieve those values.
You must enable all registered engines that access the connection to use the external credential store system. For example, you must enable the authoring Data Collector to use the credential store so that you can test a connection or preview a pipeline that uses credential functions. Similarly, you must enable the execution Data Collector to use the credential store so that you can run a pipeline that uses credential functions.
For more information, see credential stores for Data Collector or credential stores for Transformer.
Runtime resources
To use runtime resources, you define runtime resources in a file that is locally stored on Data Collector or Transformer, and then you call the resources from connection properties.
You must locally store the runtime resource file on all registered Data Collectors or Transformers that use the connection. For example, you must locally store the file on the authoring Data Collector so that you can test a connection or preview a pipeline that calls a resource from the file. Similarly, you must store the file on the execution Data Collector so that you can run a pipeline that calls a resource from the file.
Using runtime resources also allows you to change connection values by simply changing the values in the runtime resource files. For example, you might store the same resource file on two execution Data Collectors, but define a different resource value in each file. That way, a pipeline using the same connection can run on both execution Data Collectors, but the connection uses different values.
For more information, see runtime resources for Data Collector or runtime resources for Transformer.
Tip: To more securely define sensitive values, use credential stores.

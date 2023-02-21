# Module 06 - Using the Gremlin API for a Graph Data Model

[< Previous Module](../modules/module05.md) - **[Home](../README.md)** - [Next Module >](../modules/module07.md)

## :loudspeaker: Introduction

Azure Cosmos DB for Apache Gremlin is a graph database service that can be used to store massive graphs with billions of vertices and edges. You can query the graphs with millisecond latency and evolve the graph structure easily. The API for Gremlin is built based on Apache [TinkerPop](https://tinkerpop.apache.org/), a graph computing framework that uses the Gremlin query language.

The API for Gremlin combines the power of graph database algorithms with highly scalable, managed infrastructure. This approach provides a unique and flexible solution to common data problems associated with inflexible or relational constraints.

Here are some scenarios where graph support of Azure Cosmos DB can be useful:

**Social networks/Customer 365:** By combining data about your customers and their interactions with other people, you can develop personalized experiences, predict customer behavior, or connect people with others with similar interests. Azure Cosmos DB can be used to manage social networks and track customer preferences and data.

**Recommendation engines:** This scenario is commonly used in the retail industry. By combining information about products, users, and user interactions, like purchasing, browsing, or rating an item, you can build customized recommendations. The low latency, elastic scale, and native graph support of Azure Cosmos DB is ideal for these scenarios.

**Geospatial:** Many applications in telecommunications, logistics, and travel planning need to find a location of interest within an area or locate the shortest/optimal route between two locations. Azure Cosmos DB is a natural fit for these problems.

**Internet of Things:** With the network and connections between IoT devices modeled as a graph, you can build a better understanding of the state of your devices and assets. You also can learn how changes in one part of the network can potentially affect another part.


## Add a graph
https://learn.microsoft.com/en-us/azure/cosmos-db/gremlin/quickstart-dotnet?tabs=windows#add-a-graph

## Query using Gremlin
https://learn.microsoft.com/en-us/azure/cosmos-db/gremlin/tutorial-query

> :bulb: **Did you know?**
>The following options are not available if you select Serverless as the Capacity mode:

        Apply Free Tier Discount
        Geo-redundancy
        Multi-region Writes


## :mortar_board: Knowledge Check

Which of the following is a type of data model supported by Azure Cosmos DB using the Gremlin API?

        A) Relational data model
        B) Document data model
        C) Graph data model
        D) None of the above

What is the purpose of vertices in a graph data model?

        A) To represent entities in the data model
        B) To represent relationships between entities in the data model
        C) To define the schema of the graph data model
        D) None of the above

Which of the following is a query language used with the Gremlin API for graph data models?

        A) SQL
        B) Cypher
        C) Gremlin
        D) None of the above

Which of the following is a traversal step in Gremlin that is used to filter vertices based on their properties?

        A) out()
        B) in()
        C) has()
        D) None of the above


<div align="right"><a href="#module-06---lineage">↥ back to top</a></div>

## :tada: Summary

This module provided an overview of graph databases in Cosmos DB using the Gremlin API.

[Continue >](https://github.com/PrabhakerP/CosmosDBHOL)

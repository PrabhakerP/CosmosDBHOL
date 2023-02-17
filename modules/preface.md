
# Azure Cosmos DB

Azure Cosmos DB is a fully managed NoSQL and relational database for modern app development. Azure Cosmos DB offers single-digit millisecond response times, automatic and instant scalability, along with guarantee speed at any scale. Business continuity is assured with SLA-backed availability and enterprise-grade security.

When implementing Microsoft Purview, it's recommend not introducing too much change and complexity quickly. The technical metadata is recommended to be the foundation. You'll need to gather and organize this before you can make sense of it. After this, start with the basics: business terms, lists of authoritative data sources and databases, schema information, data ownership and stewardship, and security. Slowly scale by involving more domain owners and data stewards. Also scale by adding more classifications and sensitivity labels. This improves the search experience and allows for better data access management. For your custom metadata attributes, such as list of domains and application metadata, you could consider creating extra type definitions in Microsoft Purview using Purview's REST APIs.

When you envision a domain-oriented or more decentralized architecture, it's recommended to align your Microsoft Purview Collections and Glossaries with your data domains. Collections in Microsoft Purview are used to organize assets and sources. You can use a Collection as a boundary for your assets and sources and align this with a particular domain. You can do the same for your Glossary: create hierarchy structures within your glossary and align these with your domains. Ask your domains to take ownership for creating relationships between your glossary terms and collection attributes. This creates transparency over data ownership and improves your data semantics.

## [Key Benefits](https://learn.microsoft.com/en-us/azure/cosmos-db/introduction#key-benefits)

* Guaranteed speed at any scale
* Simplified application development
* Mission-critical ready
* Fully managed and cost-effective
* Azure Synapse Link for Azure Cosmos DB

   ![](../images/preface/metadata.png)

## APIs in Azure Cosmos DB

Azure Cosmos DB offers multiple database APIs, which include NoSQL, MongoDB, PostgreSQL Cassandra, Gremlin, and Table. By using these APIs, you can model real world data using documents, key-value, graph, and column-family data models. These APIs allow your applications to treat Azure Cosmos DB as if it were various other databases technologies, without the overhead of management, and scaling approaches. Azure Cosmos DB helps you to use the ecosystems, tools, and skills you already have for data modeling and querying with its various APIs.

All the APIs offer automatic scaling of storage and throughput, flexibility, and performance guarantees. There's no one best API, and you may choose any one of the APIs to build your application.

## Solutions that benefit from Azure Cosmos DB

Web, mobile, gaming, and IoT application that handle massive amounts of data, reads, and writes at a global scale with near-real response times for various data will benefit from Azure Cosmos DB. Azure Cosmos DB's guaranteed high availability, high throughput, low latency, and tunable consistency are huge advantages when building these types of applications. Learn about how Azure Cosmos DB can be used to build IoT and telematics, retail and marketing, gaming and web and mobile applications.

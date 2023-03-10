# Module 05 - Writing client applications for Cosmos DB

[< Previous Module](../modules/module04.md) - **[Home](../README.md)** - [Next Module >](../modules/module05.md)

## :loudspeaker: Introduction


We'll learn how to use the .NET SDK to build client applications for Cosmos DB and the SQL API. Cosmos DB is designed to support web‑scale applications, and like almost every service on Azure, it uses HTTP and REST as its native client protocol. Any Cosmos DB operation can be performed by any HTTP client, so long as the request URL points to a valid Cosmos DB resource, and the HTTP headers contain the proper authentication.

[Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)

## :thinking: Prerequisites

* An [Azure account](https://azure.microsoft.com/free/) with an active subscription.
* .NET SDK is version 6.0 or later. Open command window, run dotnet --version to check the version.
* VS code


## :bookmark_tabs: Table of Contents

| #  | Section  
| --- | ---  
| 1 | [Create a console application to read docs](#1-Create-a-console-application-to-read-docs)  
| 2 | [Create a console application to create database, contrainer and docs](#2-Create-a-console-application-to-create-database-contrainer-and-docs)  

<div align="right"><a href="#module-04---glossary">↥ back to top</a></div>

## 1. Create a console application to read docs

1. Create 2 local folders C:\CosmosLabs\ReadDocs and C:\CosmosLabs\CreateCosmosDB
2. Open the terminal from VS code and run these commands. It'll create program.cs with 
   Console.WriteLine("Hello, World!");

        dotnet new console

3. When the project folder is first opened in VS Code:

        A "Required assets to build and debug are missing. Add them?" notification appears at the bottom right of the window.
        Select Yes.
        
        If you miss it use Command Palette (View > Command Palette Ctrl+Shift+P) by typing '.NET', and running .NET: Generate Assets for Build and Debug.
                
4. Run the app by entering the following command in the command shell make sure the environment is good. It should display "Hello, World!"         

        dotnet run

5. Run these commands from the terminal 

        dotnet add package Microsoft.Azure.Cosmos
        dotnet restore
        
6. Replace this code in Program.cs file:

                using Microsoft.Azure.Cosmos;
                using System;
                using System.Threading.Tasks;

                namespace DotNetSdkDemo
                {
                        class Program
                        {
                                async static Task Main(string[] args)
                                {
                                        await QueryForDocument();
                                }

                                private async static Task QueryForDocument()
                                {
                            var cosmosUrl = "####";
                            var cosmoskey = "####";

                                        using (var client = new CosmosClient(cosmosUrl, cosmoskey))
                                        {
                                                var container = client.GetContainer("Families", "Families");
                                                var sql = "SELECT * FROM c WHERE ARRAY_LENGTH(c.children) > 1";
                                                var iterator = container.GetItemQueryIterator<dynamic>(sql);
                                                var page = await iterator.ReadNextAsync();

                                                foreach (var doc in page)
                                                {
                                                        Console.WriteLine($"Family {doc.id} has {doc.children.Count} children");
                                                }
                                                Console.ReadLine();
                                        }
                                }

                        }
                }

7. Find values for cosmosUrl and cosmosKey from Cosmos DB account and replace #### with the actual values.

8. Press Ctrl+F5 to run the code.

9. Replace the code with the below to list all the documents.

            using System;
            using System.Collections.Generic;
            using Microsoft.Azure.Cosmos;

            namespace CosmosDBSample
            {
                class Program
                {
                    static async Task Main(string[] args)
                    {
                        // Get your Cosmos DB account endpoint and key from the Azure portal
                        string endpointUrl = "######";
                        string primaryKey = "####";

                        // Create a new Cosmos DB client instance
                        CosmosClient cosmosClient = new CosmosClient(endpointUrl, primaryKey);

                        // Set the database and container names
                        string databaseName = "Families";
                        string containerName = "Families";

                        // Create a new instance of the container
                        Container container = cosmosClient.GetContainer(databaseName, containerName);

                        // Define a query to retrieve all documents from the container
                        string sqlQuery = "SELECT * FROM c";

                        // Set the query options
                        //QueryRequestOptions queryOptions = new QueryRequestOptions
                        //{
                        //    PartitionKey = new PartitionKey("yourPartitionKey")
                        //};

                        // Execute the query
                        FeedIterator<dynamic> feedIterator = container.GetItemQueryIterator<dynamic>(sqlQuery); 
                        //, requestOptions: queryOptions);

                        // Read the results
                        List<dynamic> items = new List<dynamic>();

                        while (feedIterator.HasMoreResults)
                        {
                            FeedResponse<dynamic> response = await feedIterator.ReadNextAsync();
                            items.AddRange(response);
                        }

                        // Output the results
                        foreach (dynamic item in items)
                        {
                            Console.WriteLine(item.ToString());
                        }

                        // Cleanup resources
                        cosmosClient.Dispose();
                    }
                }
            }

10. Find values for endpointUrl and primaryKey from Cosmos DB account and replace them with ####

11. Press Ctrl+F5 to run the code.

## 2. Create a console application to create database, contrainer and docs

1. Open a New Folder in VS.

2. Open the terminal from VS code and run these commands. 
3. 
        dotnet new console
        dotnet add package Microsoft.Azure.Cosmos
        dotnet restore

3. Replace this code in Program.cs file:

         using Microsoft.Azure.Cosmos;
         using System;
         using System.Threading.Tasks;

         namespace DotNetSdkDemo
         {
                 class Program
                 {
                         async static Task Main(string[] args)
                         {
                                 await CreateCosmosDBDoc();
                         }

                         private async static Task CreateCosmosDBDoc()
                         {
                          
                            var cosmosUrl = "####";
                            var cosmoskey = "####";
                            
                            CosmosClient client = new CosmosClient(cosmosUrl, cosmoskey);
                            
                            Database database = await client.CreateDatabaseIfNotExistsAsync("MyCosmosDB");
                            Container container = await database.CreateContainerIfNotExistsAsync(
                                "MyContainerName",
                                "/partitionKeyPath",
                                400);

                            // Create an item
                            dynamic testItem = new { id = Guid.NewGuid().ToString(), partitionKeyPath = "MyTestPkValue", details = "it's working", status = "done" };
                            await container.CreateItemAsync(testItem);

                            // Query for an item
                            using (var iterator1 = container.GetItemQueryIterator<dynamic>(
                                "select * from T where T.status = 'done'"))
                            {
                                while (iterator1.HasMoreResults)
                                {
                                    var documents1 = await iterator1.ReadNextAsync();
                                    var cnt = 0;
                                    foreach (var item in documents1)
                                    {
                                        //Console.WriteLine(item);
                                        Console.WriteLine($" ({++cnt}) Id: {item.id}; Details: {item.details}; Status: {item.status}");
                                    }
                                }
                            }
                                }

                 }
         }
         
         
4. Check the CosmosDB and verify the database MyCosmosDB, MyContainerName and Docs created.



## :mortar_board: Knowledge Check

1.	Which of the following programming languages can be used to develop client applications for Cosmos DB with the SQL API?

        A) C# 
        B) Java 
        C) Python 
        D) All of the above

2.	What is the purpose of the Cosmos DB SDK for .NET? 

        A) To provide an object-oriented interface for interacting with Cosmos DB from .NET applications 
        B) To provide a set of pre-built functions for common Cosmos DB operations, such as querying and document management 
        C) To provide a set of tools for monitoring and managing Cosmos DB performance and usage 
        D) None of the above

3.	Which of the following options is used to configure the connection to a Cosmos DB account using the .NET SDK? 

        A) Account endpoint 
        B) Account key 
        C) Connection string 
        D) All of the above

4.	Which of the following is true regarding querying data with the .NET SDK for Cosmos DB? 

        A) Queries can be constructed using LINQ or SQL syntax 
        B) Queries can only return a maximum of 100 documents at a time 
        C) Queries can only be executed on the primary replica of the Cosmos DB account 
        D) None of the above


<div align="right"><a href="#module-04---glossary">↥ back to top</a></div>

## :tada: Summary

This module provided an overview of how to create, export, and import terms into the Microsoft Purview glossary.

[Continue >](../modules/module06.md)

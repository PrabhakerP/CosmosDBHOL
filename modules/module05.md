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

1. Open the terminal from VS code and run these commands.

        dotnet new console
        dotnet add package Microsoft.Azure.Cosmos
        dotnet restore

2. Replace this code in Program.cs file:

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

3. Find values for cosmosUrl and cosmosKey from Cosmos DB account and replace them with ####

4. Press Ctrl+F5 to run the code.

## 2. Create a console application to create database, contrainer and docs

1. Open a New Folder in VS.

2. Open the terminal from VS code and run these commands. 
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

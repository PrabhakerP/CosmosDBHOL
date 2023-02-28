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
| 2 | [Query Operators and Built-in Functions](#2-Query-Operators-and-Built-in-Functions)  

<div align="right"><a href="#module-04---glossary">↥ back to top</a></div>

## 1. Create a console application to read docs

1. Open the terminal from VS code and run these commands.
    dotnet new console
    dotnet add package Microsoft.Azure.Cosmos
    dotnet restore

## 2. Create a console application to create database, contrainer and docs


## :mortar_board: Knowledge Check

[https://aka.ms/purviewlab/q04](https://aka.ms/purviewlab/q04)

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

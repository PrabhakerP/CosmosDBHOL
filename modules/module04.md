# Module 04 - Programming with .NET SDK

[< Previous Module](../modules/module03.md) - **[Home](../README.md)** - [Next Module >](../modules/module05.md)

## :loudspeaker: Introduction


We'll learn how to use the .NET SDK to build client applications for Cosmos DB and the SQL API. Cosmos DB is designed to support web‑scale applications, and like almost every service on Azure, it uses HTTP and REST as its native client protocol. Any Cosmos DB operation can be performed by any HTTP client, so long as the request URL points to a valid Cosmos DB resource, and the HTTP headers contain the proper authentication.

[Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)

## :thinking: Prerequisites

* An [Azure account](https://azure.microsoft.com/free/) with an active subscription.
* .NET SDK is version 6.0 or later. Open command window, run dotnet --version to check the version.

## :dart: Objectives

* Create a Term in the Glossary using the System Default Term Template.
* Create a Term in the Glossary using a Custom Term Template.
* Bulk Import Terms into the Glossary via a CSV file.
* Bulk Export Terms from the Glossary into a CSV file.
* Assign a Term to an Asset in the Data Catalog.
* Update an existing Term with Related Terms and Contacts.

## :bookmark_tabs: Table of Contents

| #  | Section | Role |
| --- | --- | --- |
| 1 | [Create a Term (System Default Term Template)](#1-create-a-term-system-default-term-template) | Data Curator |
| 2 | [Create a Term (Custom Term Template)](#2-create-a-term-custom-term-template) | Data Curator |
| 3 | [Bulk Import Terms](#3-bulk-import-terms) | Data Curator |
| 4 | [Bulk Export Terms](#4-bulk-export-terms) | Data Reader |
| 5 | [Assign a Term to an Asset](#5-assign-a-term-to-an-asset) | Data Curator |
| 6 | [Update an Existing Term](#6-update-an-existing-term) | Data Curator |

<div align="right"><a href="#module-04---glossary">↥ back to top</a></div>

## 1. Create a Term (System Default Term Template)

1. Open the **Microsoft Purview Governance Portal** and from the **Data catalog**, click **Glossary**.

    ![ALT](../images/module04/04.00-manage-glossary.png)



## :mortar_board: Knowledge Check

[https://aka.ms/purviewlab/q04](https://aka.ms/purviewlab/q04)

1. Glossary terms with the same name but different descriptions can exist under the same parent term?

    A ) True  
    B ) False 

2. Glossary terms can be related to other terms in the glossary. Which of the following is **not** a valid glossary term relationship type?

    A ) Synonyms  
    B ) Antonyms  
    C ) Related terms  

3. Glossary terms created using different term templates can be exported together using the the Microsoft Purview Governance Portal (UI) glossary "Export terms" functionality?

    A ) True  
    B ) False  

<div align="right"><a href="#module-04---glossary">↥ back to top</a></div>

## :tada: Summary

This module provided an overview of how to create, export, and import terms into the Microsoft Purview glossary.

[Continue >](../modules/module05.md)

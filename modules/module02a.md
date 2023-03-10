# Module 02 - Creating Containers & Documents

[< Previous Module](../modules/module01.md) - **[Home](../README.md)** - [Next Module >](../modules/module03.md)

## :loudspeaker: Introduction

An Azure Cosmos DB container is where data is stored. Unlike most relational databases which scale up with larger VM sizes, Azure Cosmos DB scales out. Data is stored on one or more servers, called partitions. To increase throughput or storage, more partitions are added. This provides a virtually an unlimited amount of throughput and storage for a container. When a container is created, you need to supply a partition key. This is a property you select from your documents to store. The value of that property is then used to route data to the partition to be written, updated, or deleted. It can also be used in the WHERE clause in queries for efficient data retrieval.

## :dart: Objectives

* Create a Container and add documents


> :bulb: **Did you know?**
>
> There are 2 types of partitions Logical and Physical. 
> A logical partition consists of a set of items that have the same partition key. For example, in a container that contains data about food nutrition, all items contain a foodGroup property. The underlying storage mechanism for data in Azure Cosmos DB is called a physical partition.
>   [Partitioning Overview](https://learn.microsoft.com/en-us/azure/cosmos-db/partitioning-overview).
>
>
> In this module we will walk through how to create a container and documents using data explorer.

## 1. Create a container using Azure portal

1. Navigate to Open the Data Explorer pane, and select **Open Full Screen**.

    ![OpenFullScreen](../images/module02/DataExp.png)

2. Select the Subscription and Cosmos DB account that we created earlier.

    ![Data Explorer-Subcription-Account](../images/module02/Fullscreen-sub-acct-settings.png)

3. click **New Container** from the top left corner, provide the following details. Select **OK**.

    ![New Container](../images/module02/ContainerSettings.png)


## 2. Creating Documents from Data Explorer

1. Expand the **Families** and select Items(another name for documents).

2. Select **New Item** from the menu.

   ![New Item](../images/module02/NewItem.png)

3. Type in the JSON for my first family. Omit the id when you create a new document. The id property GUID gets generated automatically.

        {
            "familyName": "Smith",
            "address": {
                "addressLine": "123 Main Street",
                "city": "Chicago",
                "state": "IL",
                "zipCode": "60601"
            },
            "parents": [
                "Peter",
                "Alice"
            ],
            "kids": [
                "Adam",
                "Jacqueline",
                "Joshua"
            ]
        }


4. Select **Save** you'll see the id property with a GUID value is created.

5. Let's add anther item with these values:

        {
            "familyName": "James",
            "address": {
                "addressLine": "6890 Choachman Dr.",
                "city": "Chicago",
                "state": "IL",
                "zipCode": "60603"
            },
            "parents": [
                "David",
                "Diana"
            ],
            "kids": [
                "Ava",
                "Brad"
            ],
            "pets": [
                "Tiger"
            ]
        }

6. Let's update the addressline to 
    "133 Wheat Ridge Ln."
    
7. Select **Update** 

8. Click on the **...** in Items to bring up a query editor.

   ![New Query](../images/module02/NewQuery.png)

9. Write and Execute these queries:

    SELECT * FROM c
    WHERE c.address.city = 'Chicago'

    SELECT * FROM c
    WHERE c.address.zipCode = '60601'

    SELECT * FROM c
    WHERE IS_DEFINED(c.pets)

    SELECT * FROM c
    WHERE ARRAY_LENGTH(c.kids) > 2


## 5. Uploading a JSON file with multiple items

1. Download the cities.json file from  [Downloads](../assests/Module02/)

2. click New Container from the top left corner, provide the following details. Select OK.

    ![New Container](../images/module02/Cities.png)

3. Expand **Cities** and Click on **CityPopulation**

4. Select **Upload Item** from the menu and browse to the extrated file and select citie.json.

5. Click **Upload**

6. Run these queries:

        SELECT cp.city, cp.state, cp.rank FROM CityPopulation cp

        SELECT cp.city, cp.state, cp.rank FROM CityPopulation cp
        WHERE StringToNumber(cp.rank) between 30 AND 50

        SELECT cp.city, cp.state, cp.rank FROM CityPopulation cp
        WHERE StringToNumber(cp.rank) between 30 AND 50
        Order by cp.growth_from_2000_to_2013 DESC

        SELECT AVG(StringToNumber(cp.population)) AveragePopulation, COUNT(cp.city) Cities, cp.state 
        FROM CityPopulation cp
        Group by cp.state 



## :mortar_board: Knowledge Check

1.	Which of the following is required when creating a container in Azure Cosmos DB? 

        A) Container ID 
        B) Database ID 
        C) Partition key 
        D) All of the above


2.	What is the purpose of a partition key in Azure Cosmos DB? 

        A) To define the logical grouping of documents within a container 
        B) To improve query performance by reducing the number of documents that need to be scanned 
        C) To increase the maximum size of a container 
        D) None of the above


3.	Which of the following options is used to set the throughput for a container in Azure Cosmos DB? 

        A) RU/s (Request Units per second) 
        B) MB/s (Megabytes per second) 
        C) GB/s (Gigabytes per second) 
        D) All of the above


4.	Which of the following is true regarding creating documents in Azure Cosmos DB? 

        A) All documents within a container must have the same schema 
        B) Documents are limited to a maximum size of 1 MB 
        C) Each document must have a unique ID within the container 
        D) None of the above


<div align="right"><a href="#module-02a---register--scan-adls-gen2">??? back to top</a></div>

## :tada: Summary

This module provided an overview of how to create Containers & Documents.

[Continue >](../modules/module03.md)

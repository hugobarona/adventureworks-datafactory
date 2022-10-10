![demo-architecture drawio](https://user-images.githubusercontent.com/5125006/194807007-a79f1e39-065c-4ba3-9b9a-555433d7948d.png)

# Using Adventure Works Sample database to migrate a SQL Database to Cosmos DB using Azure Data Factory

This repository provides all resources related to a demo showing how to transform a normalized dataset, stored in a Azure SQL relational database, and denormalize the data to be stored in a NoSQL Database - Cosmos DB.

Steps to use this demo:

- Download the AdventureWorks sample database .bak file and import it to your environment running SQL Server: [Link](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver16&tabs=ssms).
- Download [Data Migration Assistant](https://learn.microsoft.com/en-us/sql/dma/dma-overview?view=sql-server-ver16#get-data-migration-assistant) and install it in your environment.
- Open the [Azure portal](https://portal.azure.com/) and ensure you have an active and valid Azure account and subscription
- Create a resource group rg-passdcs22-demo
- Create Azure resources in the resource group (I did not export them to an ARM/bicep template because some of the resources cannot be exported. If you need any help with the creation, please create an issue in the repo or contact me.)
. Create an Azure SQL database with name **sql-adventureworks-demo**
. Update the Azure SQL database Firewall settings (Overview blade) to enable public access and add your ip address to the exclusions list.
. Create an Azure Data Factory Instance with name **df-pass22-demo**
. Create a Cosmos DB with name **cosmos-pass22-demo**
. Open Data Migration Assistant and perform the following steps:
- Create a migration project
- Configure the source to connect to your SQL Server instance and local AdventureWorks database
- Configure the destination as the Azure SQL instance you created previously
- Perform the migration and ensure the database is successfully migrated to the Azure SQL database.
. Open the Azure Portal and run some queries in the Azure SQL database to ensure the data was correctly migrated.
. Follow [this article and its steps](https://learn.microsoft.com/en-us/azure/data-factory/how-to-sqldb-to-cosmosdb) to configure your Data Factory's pipeline
. Run the pipeline and ensure the data is correctly migrated to Cosmos DB

## Azure Search

. Create an Azure Search instance on the Azure Portal
. Use the Import Data feature to import the data from Cosmos DB and create your index (if not sure about the steps, please watch again the presentation's video)
. Test your index and perform some queries

## Power BI

- Download Power BI Desktop and install in your environment
- Connect your Power BI Desktop installation with your Cosmos DB account previously created
- Perform the steps shown in the presentation's video to create your first report using the data available in Cosmos DB
- Publish the report to your Power BI account (you need to ensure to have a valid and active Power BI account. If not, you can create a [free trial here](https://powerbi.microsoft.com/en-ie/landing/free-account)).
- Open the [Power BI Service portal](https://app.powerbi.com/) and access the report
- Create a dashboard from your report as shown in the presentation's video.

### And that's it. You successfully migrated data from a relational SQL database to your **Cosmos DB** account using **Azure Data Factory** and then you extended your data solution with the introduction of Azure Search to enable the end-users of your apps to query and search the data and you created a Power BI report and dashboard to provide visualizations to your teams and business users and enable them to explore and extract insights from the data.

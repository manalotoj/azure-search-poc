## azure-search-poc
This project contains an example of how to populate an index with 2 data sources - 1) Cosmos DB (SQL API), and 2) Azure Blob Storage.

### Configure Azure Services
Create the following Azure Services within your Azure subscription:

#### Azure/Cognitive Search
Set the corresponding service tier ("Free" sku may suffice depending on how much data you may have); accept all defaults.

#### General Purpose Azure Storage V2
Create a general purpose, V2 Azure storage account. Set the "Replication" to "Locally redundant storage (LRS)" as there is no need for geo-redundancy for a POC.

Within the storage account, create a container to house your documents.

#### Cosmos DB Collection
Create a Cosmos DB collection. Note that each document must contain a property named <b>metadata_storage_path</b> whose value is equivalent to the base64 encoded fully qualified path of its corresponding blob file. This is what links the Cosmos DB data to the blob storage files.

### Postman Collection
Import the [Postman collection](https://github.com/manalotoj/azure-search-poc/blob/main/A-HRB-CogSearch-POC.postman_collection.json).

The collection relies on the following <b>Environment Variables</b>:

| Variable           | Description                    |
| ------------------ |:------------------------------:|
| searchAccount      | your search account name
| searchApiVersion   | 2019-05-06
| searchApiKey       | primary API key for search account
| cosmosDbConnString | copy "Connection String" value from Cosmos DB account. Append the value with ";Database=[database-name]"
| storageConnString. | storage account connection string value

Execute the Postman scripts in order starting with "1.0 Create idx-demo Index".

#### Test
Test the index from the Azure Portal

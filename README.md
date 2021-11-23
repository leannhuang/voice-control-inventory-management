# voice-control-inventory-management
Voice control the Power BI Dashbaord to do the inventory management using the Percept DK audio, Custom Commands, Azure Function, and Power BI.

The goal of this project is to be able to do the inventory management by voice with the Percept DK device and Audio SoM using Azure Custom Commands as the platform.  

## Prerequisites
- Percept DK ([Purchase](https://www.microsoft.com/en-us/store/build/azure-percept/8v2qxmzbz9vc))
- Azure Subscription : [Free trial account](https://azure.microsoft.com/en-us/free/)
- Azure Percept Audio 
- [Azure Percept DK setup experience](https://docs.microsoft.com/en-us/azure/azure-percept/quickstart-percept-dk-set-up)
- [Azure Percept Audio setup](https://docs.microsoft.com/en-us/azure/azure-percept/quickstart-percept-audio-setup)
- Speaker or headphones that can connect to 3.5mm audio jack (optional) 
- Download and install [Power BI Desktop](https://powerbi.microsoft.com/en-us/downloads/)
- Download and install [VS code](https://code.visualstudio.com/download) 
- Install the [IoT Hub](https://marketplace.visualstudio.com/items?itemName=vsciot-vscode.azure-iot-toolkit) and [IoT Tools](https://marketplace.visualstudio.com/items?itemName=vsciot-vscode.azure-iot-tools) Extension in VS Code 
- The [Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?tabs=v4%2Cwindows%2Ccsharp%2Cportal%2Cbash%2Ckeda#install-the-azure-functions-core-tools) version 3.x.
- The [Python extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python) for Visual Studio Code.
- The [Azure Functions extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions) for Visual Studio Code.


## Solution Architecture
![Solution Architecture](docs/images/solution-architect-1.png)

## Device Setup
1. Follow [Quickstart: unbox and assemble your Azure Percept DK components](https://docs.microsoft.com/en-us/azure/azure-percept/quickstart-percept-dk-unboxing) and the next steps.

## Content
| File             | Description                                                   |
|-------------------------|---------------------------------------------------------------|
| `readme.md`             | This readme file                                              |
| `deployment.template.json`    | The delopyment the edge modules of this Smart Plug Solution |
| `envtemplate`    | The list of the enviroment varialbes for .env use |


## Steps

1. Refence the quickstart [link](https://docs.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?tabs=azure-portal) to create an [Azure SQL Server Database](https://ms.portal.azure.com/#create/Microsoft.AzureSQL)

2. Set the Server Firewall [link](https://docs.microsoft.com/en-us/azure/azure-sql/database/firewall-configure#from-the-database-overview-page)
   
3. Create table and columns by executing the T-SQL query in the query editor window 
   1. Click Query Editor
      
      ![query editor](docs/images/query-editor.png)
   
   2. Login to your SQL server
      
      ![login](docs/images/sql-login.png)
   

   3. Copy the T-SQL query below and paste in the query editor
      ```
      CREATE TABLE Stock ( 
          color varchar(255), 
          num_box int, 
      ); 
      ``` 

   4. Run the Query to create the stock table 

      ![sql-query](docs/images/sql-query.png)

4. Visit the [azure-functions folder](https://github.com/leannhuang/voice-control-inventory-management/tree/main/azure-functions) to config Azure function

5. Visit the [custom commands folder](https://github.com/leannhuang/smart-plug-with-custom-commands/tree/main/custom-commands) to complete setting up the custom commands of the smart stock (Note down the `Application ID`, `Speech resource key`, and `region`)

6. Create a file named `.env` in this folder based on `envtemplate`. Provide values for all variables.

7. Deploy edge modules on your edge device (Note: The edge modules run on devkit will be replaced by the edge modules defined in the `deployment.template.json`)
   1. In the Visual Studio Code explorer, right-click the `deployment.template.json` file and select Generate IoT Edge Deployment Manifest.
        
        ![generate manifest](docs/images/generate-manifest.png)

   2. Use VSCode as in [here](https://docs.microsoft.com/en-us/azure/iot-edge/tutorial-develop-for-linux?view=iotedge-2020-11#deploy-modules-to-device) to deploy the modules to the Percept DK with the above files.


## Other Info
### Get your IoT Hub connection string
1. Go to IoT Hub service in Azure Portal. Click Shared access policies -> Iothubowner  
2. Click Copy the get the primary connection string 
![Get IoT Hub Connection String](docs/images/get-iot-hub-connection-string.png)
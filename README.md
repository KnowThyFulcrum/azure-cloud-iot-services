# Azure Cloud & IoT Services

Hands-on implementation of Microsoft Azure cloud, IoT, security, and ML services, plus a C# Azure Functions HTTP trigger.

**Course:** CNT 6144 – Advanced Analytics with Cloud Services in ECE, Florida International University (Spring 2026)

## Tools
Microsoft Azure (Portal, Cloud Shell / Azure CLI, PowerShell) · Azure Virtual Machines · Azure Container Instances · Virtual Networks · Blob Storage · Azure SQL Database · Azure IoT Hub · Azure IoT Edge · Azure Functions (C#, .NET 6, Functions v4) · Azure RBAC, Resource Locks, NSGs · Azure Machine Learning (AutoML) · Power BI

## What was implemented
- **Chapter 3 – Core services:** resource groups, a VM configured as a web server, Azure Container Instances, a virtual network with two VMs and connectivity test, Blob Storage, Azure SQL Database.
- **Chapter 4 – IoT & serverless:** Azure IoT Hub with a registered device (`myRaspberryPi`), Azure Functions (HTTP trigger), VM deployment from templates/PowerShell, VM creation with the Azure CLI.
- **Chapter 5 – Security & governance:** network security groups to secure traffic, RBAC access management, resource locks (tested deletion protection), resource tagging, Trust Center.
- **Chapter 7 – IoT Edge:** deployed a first IoT Edge module to a virtual Windows device.
- **Chapter 8 – ML:** classification model with Automated ML in Azure Machine Learning (UCI Bank Marketing dataset).
- **Chapter 9 – Real-time monitoring:** IoT Hub telemetry streamed to Power BI.

## Repository structure
```
src/HttpTriggerFunction/HttpTrigger01.cs               C# HTTP-triggered Azure Function
src/HttpTriggerFunction/HttpTriggerFunction.csproj     Project file (.NET 6, Functions v4)
src/HttpTriggerFunction/host.json                      Functions host config
data/bankmarketing_sample.csv                          First 100 rows of the AutoML training data
docs/cnt6144_cloud_service_project_redacted.pdf        Full project report with screenshots (sensitive details redacted)
```

## Dataset
AutoML used the UCI **Bank Marketing** dataset ([UCI ML Repository](https://archive.ics.uci.edu/dataset/222/bank+marketing)); the full training CSV is omitted, and a 100-row sample is in `data/`.

## How to run the Azure Function locally
1. Install the .NET 6 SDK and [Azure Functions Core Tools v4](https://learn.microsoft.com/azure/azure-functions/functions-run-local).
2. In `src/HttpTriggerFunction/`, create `local.settings.json` (not committed):
   ```json
   { "IsEncrypted": false, "Values": { "AzureWebJobsStorage": "UseDevelopmentStorage=true", "FUNCTIONS_WORKER_RUNTIME": "dotnet" } }
   ```
3. `func start`, then call `http://localhost:7071/api/HttpTrigger01?name=World`.

## Author
Jay Cespedes

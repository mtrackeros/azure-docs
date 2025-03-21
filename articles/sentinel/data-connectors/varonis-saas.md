---
title: "Varonis SaaS connector for Microsoft Sentinel"
description: "Learn how to install the connector Varonis SaaS to connect your data source to Microsoft Sentinel."
author: cwatson-cat
ms.topic: generated-reference
ms.date: 11/20/2024
ms.service: microsoft-sentinel
ms.author: cwatson
ms.collection: sentinel-data-connector
---

# Varonis SaaS connector for Microsoft Sentinel

Varonis SaaS provides the capability to ingest [Varonis Alerts](https://www.varonis.com/products/datalert) into Microsoft Sentinel.

Varonis prioritizes deep data visibility, classification capabilities, and automated remediation for data access. Varonis builds a single prioritized view of risk for your data, so you can proactively and systematically eliminate risk from insider threats and cyberattacks.

This is autogenerated content. For changes, contact the solution provider.

## Connector attributes

| Connector attribute | Description |
| --- | --- |
| **Log Analytics table(s)** | VaronisAlerts_CL<br/> |
| **Data collection rules support** | Not currently supported |
| **Supported by** | [Varonis](https://www.varonis.com/resources/support) |

## Query samples

**List all Varonis Alerts**

   ```kusto
VaronisAlerts_CL

   | sort by TimeGenerated desc
   ```

**List high severity Varonis Alerts**

   ```kusto
VaronisAlerts_CL

   | where Severity_s == "High"

   | sort by TimeGenerated desc
   ```



## Prerequisites

To integrate with Varonis SaaS make sure you have: 

- **Microsoft.Web/sites permissions**: Read and write permissions to Azure Functions to create a Function App is required. [See the documentation to learn more about Azure Functions](/azure/azure-functions/).


## Vendor installation instructions


> [!NOTE]
   >  This connector uses Azure Functions to connect to Varonis DatAlert service to pull alerts into Microsoft Sentinel. This might result in additional data ingestion costs. See the [Azure Functions pricing page](https://azure.microsoft.com/pricing/details/functions/) for details.


**For Azure function and related services installation use:**

 [![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FAzure-Sentinel%2Fmaster%2FSolutions%2FVaronisSaaS%2FData%2520Connectors%2Fazuredeploy.json)


STEP 1 - Obtain the Varonis DatAlert Endpoint API credentials.

 To generate the Client ID and API key:
 1. Launch the Varonis Web Interface.
 2. Navigate to Configuration -> API Keys. The API Keys page is displayed.
 3. Click Create API Key. The Add New API Key settings are displayed on the right.
 4. Fill in the name and description.
 5. Click the Generate Key button.
 6. Copy the API key secret and  save it in a handy location. You won't be able to copy it again.

For additional information, please check: [Varonis Documentation](https://help.varonis.com/s/document-item?bundleId=ami1661784208197&topicId=emp1703144742927.html&_LANG=enus)


STEP 2 - Deploy the connector and the associated Azure Function.

   Workspace Name


Use this method for automated deployment of the data connector using an ARM Template.

1. Click the Deploy to Azure button. 

	[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FAzure-Sentinel%2Fmaster%2FSolutions%2FVaronisSaaS%2FData%2520Connectors%2Fazuredeploy.json)
2. Select the preferred Subscription, Resource Group, Region, Storage Account Type.
3. Enter Log Analytics Workspace Name, Varonis FQDN, Varonis SaaS API Key.
4. Click Review + Create, Create.



## Next steps

For more information, go to the [related solution](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/varonis.microsoft-sentinel-solution-varonissaas?tab=Overview) in the Azure Marketplace.

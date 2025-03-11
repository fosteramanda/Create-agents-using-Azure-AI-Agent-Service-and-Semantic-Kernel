# Create a Bing Search Agent using Azure AI Agent Service and Semantic Kernel

## Prerequisties

### Complete Agent Setup

1. **Choose Basic or Standard Agent setup**

      **Basic Setup**:  Agents use multitenant search and storage resources fully managed by Microsoft. You don't have visibility or control over these underlying Azure resources.

      **Standard Setup**: Agents use customer-owned, single-tenant search and storage resources. With this setup, you have full control and visibility over these resources, but you incur costs based on your usage.

1. **Deploy a template**

| Template | Description   | Auto-deploy |
| ------------------- | -----------------------------------------------| -----------------------|
|`basic-agent-identity.bicep`| Deploy a basic agent setup that uses Managed Identity authentication on the AI Services/AOAI connection. | [![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure-Samples%2Fazureai-samples%2Fmain%2Fscenarios%2FAgents%2Fsetup%2Fbasic-agent-identity%2Fazuredeploy.json)
| `standard-agent.bicep`  | Deploy a standard agent setup that uses Managed Identity authentication on the AI Services/AOAI connection. | [![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure-Samples%2Fazureai-samples%2Fmain%2Fscenarios%2FAgents%2Fsetup%2Fstandard-agent%2Fazuredeploy.json)

### Create and connect a Bing resource

**Create a Grounding with Bing Search resource and connect it to your project**

You must create a Grounding with Bing Search resource and connect it to your project. [See details](https://learn.microsoft.com/en-us/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview) 

Note: You need to have owner or contributor role in your subscription or resource group.


### Install the requried dependencies

You will need to install the optional Semantic Kernel `azure` dependencies if you haven't already via:

```bash
pip install semantic-kernel[azure]
pip install azure-ai-projects
pip install azure-identity
```

Before running an Azure AI Agent, modify your .env file to include:

```bash
AZURE_AI_AGENT_PROJECT_CONNECTION_STRING = "<example-connection-string>"
AZURE_AI_AGENT_MODEL_DEPLOYMENT_NAME = "<example-model-deployment-name>"
```

The project connection string is of the following format: `<HostName>;<AzureSubscriptionId>;<ResourceGroup>;<ProjectName>`. See [here](https://learn.microsoft.com/en-us/azure/ai-services/agents/quickstart?pivots=programming-language-python-azure#configure-and-run-an-agent) for information on obtaining the values to populate the connection string.

The .env should be placed in the root directory.

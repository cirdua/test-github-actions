# AzureRM using Github Workflows
Deploy ARM Templates using Github Workflows

[![Lint ARM Templates](https://github.com/cirdua/test-github-actions/actions/workflows/main.yml/badge.svg)](https://github.com/cirdua/test-github-actions/actions/workflows/main.yml)

## Prerequisites
1. Create Resource Group
   ```bash
   az group create -n {MyResourceGroup} -l {location}
   ```
2. Create Service Principal
   ```bash
   az ad sp create-for-rbac --name {myApp} --role contributor --scopes /subscriptions/{subscription-id}/resourceGroups/{MyResourceGroup} --sdk-auth
   ```
3. In Github Repository Secrets, Define the following secrets:
   `AZURE_CREDENTIALS` - the json output of Step #2
   `AZURE_RG` - Resource Group Name you created in Step #1
   `AZURE_SUBSCRIPTION` - Azure Subscription ID. Can be found in Azure Portal > Subscriptions


## Storage Account
1. In Actions, Select `Deploy Storage Account Azure ARM` then `Run Workflow`
2. Input Storage Account Name
3. Input Location ex: southeastasia
4. Select Storage Account Type
5. Created Storage Account will be indicated in Output step of the workflow.
   Resource will be placed in Resource Group indicated in `AZURE_RG` Secret

## Tests
ARM Test Toolkit is used in Github Workflows
For details on installation, refer to this [link](https://github.com/Azure/arm-ttk/blob/master/arm-ttk/README.md)


## References
https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/deploy-github-actions
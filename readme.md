# Windows Server 2019 - Standalone Domain Controller Template

This repository offers test platform who wants to deploy quickly Active Directory Environment which will be placed on Windows Server 2019 OS for Azure deployments. This repository contains just Standalone Active Directory deployment templates that have been tested. The template is aimed at those who wish to demonstrate Azure Resource Manager Templates quickly, and/or spin up a single DC for a quick and dirty PoC.

Description | Link | Visualize
--- | --- | ---
Full deploy - Virtual Network, WS 2019 - New AD Forest  | <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fjamesvincent%2Fazure-dc-2019%2Fmaster%2Fazuredeploy.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png"/></a> | <a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Fjamesvincent%2Fazure-dc-2019%2Fmaster%2Fazuredeploy.json" target="_blank"><img src="http://armviz.io/visualizebutton.png"/></a>

 # Deploys the following infrastructure:

 This template needs parameters which will be used for deployment process.

* envName      : Please provide your environment name. It might be like this : Microsoft > msft.
* vNETAddress  : Please provide your Virtual Network Address Prefix. It should be like this : 10.0.0
* userName     : Please provide your user name you wish to use for the Local Admin account.
* userPassword : Please provide the password you wish to use for the Local Admin account.
* domainName   : Please provide your domain name. It might be like: msft.com

This template allows you to create these resources.

* Virtual Machine - ADDS Service
  * Network Security Group with RDP Rule
  * Public Ip Address - Static
  * Desired State Configuration Extension - ADDS
  * BGInfo Extension 
  * Diagnostic Storage
* Virtual Network
  * 2 subnets: Application, Management
  * DNS Server : ADDS Server


Also you can deploy this template with the Powershell. Before you have to login with your Azure Admin Account on the Azure Powershell. However, you can use Azure Cloud Shell.

```PowerShell
# --- Set resource group name and create
$ResourceGroupName = "pr-prod-rg"
New-AzureRmResourceGroup -Name $ResourceGroupName -Location "West Europe" -Force

# --- Deploy infrastructure
$DeploymentParameters = @{
    envName = "msft"
    vNETAddress = "10.0.0"
    userName = "vmadmin"
    userPassword = "Password!23"
    domainName = 'msft.com'

}

New-AzureRmResourceGroupDeployment -Name "deployment-01" -ResourceGroupName $ResourceGroupName -TemplateFile .\examples\example-linked-template.json @DeploymentParameters
```

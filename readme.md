# Windows Server 2019 - Standalone Domain Controller Template

This repository is forked from hasangural/azure-dc-2016. Small ammendments were made to push a 2019 Server. This allows you to quickly deploy a single Domain Controller fully configured offering an Active Directory Environment. The template is aimed at those who wish to demonstrate Azure Resource Manager Templates quickly, and/or spin up a single DC for a quick and dirty PoC.

Description | Link | Visualize
--- | --- | ---
Full deploy - Virtual Network, WS 2019 - New AD Forest  | <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fjamesvincent%2Fazure-dc-2019%2Fmaster%2Fazuredeploy.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png"/></a> | <a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Fjamesvincent%2Fazure-dc-2019%2Fmaster%2Fazuredeploy.json" target="_blank"><img src="http://armviz.io/visualizebutton.png"/></a>

 # Deploys the following infrastructure:

 This template needs parameters which will be used for the deployment process.

* envName      : Please provide your environment name. This is used as a prefix for resources -- keep it short!
* vNETAddress  : Please provide your Virtual Network Address Prefix. It should be like this : 10.0.0
* userName     : Please provide your user name you wish to use for the Local Admin account.
* userPassword : Please provide the password you wish to use for the Local Admin account.
* domainName   : Please provide the desired fully qualified domain name. Example: jamesvincent.com

This template will create the following resources.

* Virtual Machine - ADDS Service
  * Network Security Group with RDP Rule
  * Public IP Address - Static
  * Desired State Configuration Extension - ADDS
  * BGInfo Extension 
  * Diagnostic Storage
  
* Virtual Network
  * 2 subnets: Application, Management
  * DNS Server: ADDS Server

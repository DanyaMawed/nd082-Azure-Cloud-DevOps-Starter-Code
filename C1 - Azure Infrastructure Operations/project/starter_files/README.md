# Azure Infrastructure Operations Project: Deploying a scalable IaaS web server in Azure

### Introduction
For this project, you will write a Packer template and a Terraform template to deploy a customizable, scalable web server in Azure.

### Getting Started
1. Clone this repository

2. Create your infrastructure as code

3. Update this README to reflect how someone would use your code.

### Dependencies
1. Create an [Azure Account](https://portal.azure.com) 
2. Install the [Azure command line interface](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
3. Install [Packer](https://www.packer.io/downloads)
4. Install [Terraform](https://www.terraform.io/downloads.html)

### Instructions
Frst start by loging it to the azure account using powershell Azure CLI: **az login**
and then navigate to the folder that contains this project files.

#### 1- deploying policy:
within Azure CLI write: 

**az policy definition create --name tagging-policy --rules tags_Policy.json**

then : 

**az policy assignment create --policy tagging-policy**

by applying this policy you want be able to deploy any resource without adding tags for it.

#### 2- deploying packer

withing the powershell use the command: **packer  build <"the packer file name">**
 

#### 3- deploying terraform

Since the  Azuredevops resource group is already created for this udacity course use this command to allow terraform to manage it:

**terraform import azurerem_resource_group.udacity-rg /subscriptions/XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX/resourceGroups/Azuredevops**

Then

**terraform init** 

**terraform plan**

**terraform plan -out solution.plan**  # to save the plan 

**terraform apply "solution.plan"**

then you can delete everything using:
**terraform destroy**

### Output
1- policy:

to make sure that everything is in order use: **az policy assignment list**
it will show you the policy you created.

2- packer image: 
you will find that the packer image is created in the Azuredevops resource group.

3- terraform:
you can use **terraform state list**  to check which resources were applied. 




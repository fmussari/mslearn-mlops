
Reproducing this tutorial:   
[https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-Azure-Machine-Learning.html](https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-Azure-Machine-Learning.html)
using CLI  
  
References:  
[https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-developer-tools.html](https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-developer-tools.html)  
[https://microsoftlearning.github.io/mslearn-aml-cli/](https://microsoftlearning.github.io/mslearn-aml-cli/)

## Steps

0. Open the Azure portal and select the [>_] (Cloud Shell) button at the top of the page to the right of the search box.
  
1. Remove any ML CLI extensions (both version 1 and 2) to avoid any conflicts with previous versions with this command:  
   `az extension remove -n azure-cli-ml`  
   `az extension remove -n ml`

2. Install the Azure Machine Learning (v2) extension with the following command:  
   `az extension add -n ml -y`
  
3. Create a Resoruce Group:  
  `az group create --name "rg-mlops-labs" --location "eastus"`

4. Create an Azure Machine Learning workspace:  
  `az ml workspace create --name "mlw-mlops-labs" -g "rg-mlops-labs"`

5. Create a compute instance in your workspace:  
   `az ml compute create --name "ci71974" --size STANDARD_DS11_V2 --type ComputeInstance -w mlw-mlops-labs -g rg-mlops-labs`  
  
6. Use the CLI (v2) to create a registered data asset:  
  a. Option without .yml [link](https://learn.microsoft.com/en-us/cli/azure/ml/data?view=azure-cli-latest#az-ml-data-create)  
    `az ml data create --name diabetes-dev-folder --version 1 --path ./experimentation/data -w mlw-mlops-labs`
  b. Option with .yml [link](https://learn.microsoft.com/en-us/azure/machine-learning/reference-yaml-data?view=azureml-api-2)  

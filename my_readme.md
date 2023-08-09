
Reproducing this tutorial:   
[https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-Azure-Machine-Learning.html](https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-Azure-Machine-Learning.html)
using CLI  
  
References:  
[https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-developer-tools.html](https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-developer-tools.html)  
[https://microsoftlearning.github.io/mslearn-aml-cli/](https://microsoftlearning.github.io/mslearn-aml-cli/)

## Steps

0. Open the Azure portal and select the [>_] (Cloud Shell) button at the top of the page to the right of the search box.

1. ```
   git clone https://github.com/fmussari/mslearn-mlops.git mslearn-mlops
   cd mslearn-mlops
   code .
   ```
  
2. Remove any ML CLI extensions (both version 1 and 2) to avoid any conflicts with previous versions with this command:  
   `az extension remove -n azure-cli-ml`  
   `az extension remove -n ml`

3. Install the Azure Machine Learning (v2) extension with the following command:  
   `az extension add -n ml -y`
  
4. Create a Resoruce Group:  
  `az group create --name "rg-mlops-labs" --location "eastus"`

5. Create an Azure Machine Learning workspace:  
  `az ml workspace create --name "mlw-mlops-labs" -g "rg-mlops-labs"`

6. Create a compute instance in your workspace:  
   `az ml compute create --name "ci71974" --size STANDARD_DS11_V2 --type ComputeInstance -w mlw-mlops-labs -g rg-mlops-labs`  
  
7. Use the CLI (v2) to create a registered data asset:  
  a. Option without .yml [link](https://learn.microsoft.com/en-us/cli/azure/ml/data?view=azure-cli-latest#az-ml-data-create)  
    `az ml data create --name diabetes-dev-folder --version 1 --path experimentation/data -w mlw-mlops-labs -g rg-mlops-labs`  
  b. Option with .yml [link](https://learn.microsoft.com/en-us/azure/machine-learning/reference-yaml-data?view=azureml-api-2)  

8. Run the job:  
   `az ml job create --file ./src/job.yml -w mlw-mlops-labs -g rg-mlops-labs`
  
**I'm not sure about the need to create a registered data asset.**  
**Ran OK**

## Challenge 2: Trigger the Azure Machine Learning job with GitHub Actions
https://microsoftlearning.github.io/mslearn-mlops/documentation/02-github-actions  

1. Login:  
   `az login`  
3. Create a service principal:
   `az ad sp create-for-rbac --name "sp-mlops-labs" --role contributor \  
                              --scopes /subscriptions/<subscription-id>/resourceGroups/rg-mlops-labs \  
                              --sdk-auth`  
4. 


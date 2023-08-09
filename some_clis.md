
Reproducing 
[https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-Azure-Machine-Learning.html](https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-Azure-Machine-Learning.html)
with CLI

References:
[https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-developer-tools.html](https://microsoftlearning.github.io/mslearn-azure-ml/Instructions/02-Explore-developer-tools.html)

## Steps

0. Open the Azure portal and select the [>_] (Cloud Shell) button at the top of the page to the right of the search box.

1. Create a Resoruce Group:  
`az group create --name "rg-mlops-labs" --location "eastus"`

2. Create an Azure Machine Learning workspace:  
`az ml workspace create --name "mlw-dp100-labs" -g "rg-dp100-labs"`

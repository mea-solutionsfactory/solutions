# Windows VM Scale Set with ILB and ELB Inside Custom Vnet
## Simple deployment of a VM Scale Set of Windows VMs behind two load balancers inside Custom Vnet.

This template allows you to deploy a VM Scale Set of Windows VMs into existing vnet, and to run custom script extension after the provisioning was finished.
This VM Scale Set is connected to two Load Balancers at the same time, one is a private LB and the other is a public LB.

The public Load Balancer is used for the external network and exposes one front-end IP for the VM Scale Set.
The private Load Balancer is used for the internal network.


![diagram](https://raw.githubusercontent.com/idanshahar/vmss-ilv-elb-existing-vnet-arm-windows/master/VMSS_architecture.png)



## Parameters:

azuredeploy.paramaters.json contains the deployment parameters:

| Parameter     | Description   | Requeired  |
| ------------- |:-------------:| -----:     |
| vmSku         | The VM Size   | Yes        |
| instanceCount | Number of instances  |   Yes |
| adminUsername | Windows Admin Username     |    Yes |
| adminPassword | Windows Admin Password       |    Yes |
| existingVnetResourceGroup | The Existing Vnet Resource Group     |   Yes |
| existingVnetName | The Exitsing Vnet Name      |    Yes |
| existingSubnetName | The existing Subnet Name      |    Yes |
| artifactsLocation | Custom Script Extention script url      |    Yes |


## How to Deploy
Full documentation can be found [here](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-template-deploy-cli)

```
az group create --name ExampleGroup --location "Central US"
az group deployment create \
    --name ExampleDeployment \
    --resource-group ExampleGroup \
    --template-file "azuredeploy.json" \ 
    --parameters "azuredeploy.parameters.json
```

## TODO
1. Add parameter for choosing wether to use CSE or not
2. Add parameter for choosing wether to create Vnet or to use Custom Vnet
3. Default Value for instanceCount Parameter
4. Default Value for vmSKy Parameters
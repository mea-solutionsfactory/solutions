# MEA Solutions Factory

## What's this?

This repository is intended to provide you quickstarts for frequently requested scenarios.

## How to add a solution?

As a team member you have access to create a new solution by cloning this repository.
The branching strategy recommended to maintain your solutions follows a three-stages and tagging approach.

For example, to create a new solution called **smart-city** that is part of the **iot** solution catalog:

Create a new branch using following command:

     # git branch -b solution/iot-smart-city

Check-out your new branch by running the command:

     # git checkout solution/iot-smart-city
         
A typical folder structure for a solution called **smart-city** falling under the **iot** category is below:

```
|-- solutions
            |-- iot
                  |-- smart-city
                                |-- README.md
                                |-- images
                                |-- scripts
```

Copy a **solution-README.md** file in your new folder as **README.md** which will contain keywords, description and instructions on how to deploy the solution.

If you want to link to images in your **README.md** file, add them in the **images** folder.

If your solution has ARM templates and/or scripts to automate the deployment, add them to the **scripts** folder. Make sure to update the **Deploy to Azure** button URL to point to your **azuredeploy.json** file in this case.
   

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

Please report any bug or issue on the labs trough the [GitHub Issues Page](https://github.com/Microsoft/OpenSourceLabs/issues) page.

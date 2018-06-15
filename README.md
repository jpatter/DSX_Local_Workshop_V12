# DSX Local Workshop V1.2
In this workshop you will learn how to develop and deploy applications in DSX Local. The workshop has been divided into several stand-alone parts for those who are interested in a specific development tool or deployment task. 

## About this repository
This repository contains several lab subfolders. Some labs include notebooks and data, while others have additional instructions that are located in the *Lab Instructions* folder. 

## Prerequisites
1. Knowledge of analytics. These labs do not teach you the basics of analytics or how to implement analytics in R, Python and SPSS. The purpose of this workshop is to provide hands-on experience with analytics tools and deployment functions in DSX Local. 
2. To run this workshop you need an instance of DSX Local V1.2. 
3. Download the [DSX_Local_V12_Workshop.zip](https://github.com/SidneyPhoon/DSX_Local_Workshop_V12/blob/master/DSX%20Local%20Projects/DSX_Local_V12_Workshop.zip?raw=true).

### Setting up lab projects in DSX Local
1. Rename the downloaded **DSX_Local_V12_Workshop.zip** file and give it a unique name.  For example, add your initials.    *Note: Project names in DSX Local cluster must be unique. When we create a project "from file", the project name is inherited from the file name*.
2. Log in to DSX Local.
3. Select "New Project" and select "From File".
4. Browse to the .zip file and click **Create**.
![ProjectFromFile](/img/CreateProjectFromFile.png?raw=true).

### Lab 1: Build, Save and Test SparkML Models (Jupyter/Python)
1. Open the project you just created. 
2. Navigate to **Assets** view and open **TelcoChurn_SparkML** *Jupyter* notebook. This notebook has been implemented for the Python 2.7 runtime. You can verify the runtime by running the first cell in the notebook. 
3. Follow instructions in the notebook.

### Lab 2: Build, Save and Test Scikit-Learn Models (Jupyter/Python)
1. Navigate to **Assets** view and open **CreditCardDefault_SkLearn** notebook.  
2. Follow instructions in the notebook.

### Lab 3: Build, Save and Test SparkML models (Zeppelin/Python)
1. Navigate to **Assets** view and open **TelcoChurn_Zeppelin** notebook.  
2. Follow instructions in the notebook.

### Lab 4: Build R models in Jupyter and deploy into Shiny App
1. Navigate to **Assets** view and open **DriverClassification** notebook.  
2. Execute the code cells in the notebook, making sure to save the model into RStudio
3. Open RStudio
4. The "demoBrakeEvents" Shiny App is already included in this project.  Open demoBrakeEvents\server.R and run it.


### Lab 6: SPSS Modeler in DSX
1. Navigate to **SPSS Modeler Flows** and open the **Predict_Customer_Churn** Modeler Stream.
2. Review the Modeler steam and the palette of nodes
3. Add a C5 modeling nodes to the canvas and connect it to the Partition node.  Build the C5 model.
4. Connect an Evaluation node to the C5 model to evaluate its performance.

Optional Exercise

### Lab 7: Batch Scoring in DSX
1. Follow instructions in the **[DSX_Batch_Scoring.pdf](https://github.com/SidneyPhoon/DSX_Local_Workshop/blob/master/Lab%20Instructions/DSX_Batch_Scoring.pdf)**. 

### Lab 8: Model Evaluation
1. Follow instructions in the **[DSX_Evaluation_in_DSX.pdf](https://github.com/SidneyPhoon/DSX_Local_Workshop/blob/master/Lab%20Instructions/DSX_Evaluation_in_DSX.pdf)** 


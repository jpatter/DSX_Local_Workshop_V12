# DSX Local Workshop V1.2
In this workshop you will learn how to develop and deploy applications in DSX Local. The workshop has been divided into several stand-alone parts for those who are interested in a specific development tool or deployment task.

This lab is meant to be instructor-led.  That is, the instructor will explain the objectives of the DSX capabilities covered in each lab, and demonstrate some of those capabilities at the beginning of each lab.


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

Goals:
1. Familiarity with Jupyter notebook -- note time it takes to start notebook
2. Importing libraries (included in image and external i.e. pixiedust)
3. Save model to repository
4. Test model via UI -- also view installed packages
5. Test model via REST
6. Note notebook is still running

### Lab 2: Build, Save and Test Scikit-Learn Models (Jupyter/Python)
1. Navigate to **Assets** view and open **CreditCardDefault_SkLearn** notebook.  
2. Follow instructions in the notebook.

Goals:
1. Note faster notebook start time
2. %brunel cells

### Lab 3: Build, Save and Test SparkML models (Zeppelin/Python)
1. Navigate to **Assets** view and open **TelcoChurn_Zeppelin** notebook.  
2. Follow instructions in the notebook.

Goals:
1. Note multiple interpreters
2. Multiple magic keywords i.e. %sql, %spark.pyspark

### Lab 4: Build R models in Jupyter and deploy into Shiny App
1. Navigate to **Assets** view and open **DriverClassification** notebook.  
2. Execute the code cells in the notebook, making sure to save the model into RStudio
3. Open RStudio
4. The "demoBrakeEvents" Shiny App is already included in this project.  Open demoBrakeEvents\server.R if not already open.   
5. Select **Run App**
6. 

Goals:
1. R notebook
2. Loading R libraries
3. Saving model to RStudio File System (this will NOT show in Models view)
4. RStudio / Shiny

### Lab 6: SPSS Modeler in DSX
1. Navigate to **SPSS Modeler Flows** and open the **Predict_Customer_Churn** Modeler Stream.
2. Review the Modeler steam and the palette of nodes
3. Add a **C5** modeling node to the canvas and connect it to the Partition node.  Build a C5 model.
4. Click **View Model** in the C5 model.
4. Connect an **Evaluation** node to the C5 model and run it to evaluate its performance.
5. Connect an **Analysis node** to the C5 model and run it
6. Connect the two models and evaluate the two models side-by-side in the **Evaluation** node.

**Optional Exercise:**
1.  Calculate the **mean** of International, Local and LongDistace by **Gender** and **Status**
2.  **Merge** the means of each group to the data set
3.  **Derive** 3 new fields, the differences between International, Local and LongDistace, and their respective means.
4.  Build a model to predict **Churn** with these 3 additional derived fields.

Download [Modeler Exercise Solution](https://github.com/SidneyPhoon/DSX_Local_Workshop_V12/blob/master/modeler/Predict_Customer_Churn_Solution.str?raw=true).



### Lab 7: Create Batch Script and Test Batch Scoring
1. You must have completed "Lab 1: Build, Save and Test SparkML Models" before working through this lab.
2. Navigate the to the **Models** section of the project and click into the saved **Telco_Churn_ML_model**.
3. Click the **Batch score** tab.
4. For **Input data set**, select *TelcoModelFeedback.csv*.
5. For **Output data set**, check **"Local file"** and specify *new_customers_scores.csv*.
6. On the top right, click **Advanced Settings**.
7. Scroll through the Advanced Setting to see the various options.  Click **Save** to save the default settings.
8. Click **Generate Batch Script**.  (Note: the batch script can be edited. For example, to perform pre/post processing tasks)

![batchscoring](/img/batch_scoring.png?raw=true)

9. Click **Run now** and wait till the status changes to Success.
10. Verify that the *new_customers_scores.csv* is in the data section of the project.

### Lab 8: Create Model Evaluation Script and Test Evaluation
1. You must have completed "Lab 1: Build, Save and Test SparkML Models" before working through this lab.
2. Navigate the to the **Models** section of the project and click into the saved **Telco_Churn_ML_model**.
3. Click the **Evaluate** tab.
4. For the scripts inputs, specify these values.<br/>
![model_eval](/img/model_eval.png?raw=true)

5. Click **Advanced Settings** and change the name of the script. For example, you can name it ChurnModelEvalScript. Click Save.
6. Click **Generate evaluation Script**.
7. Click **Run now** and wait till the status changes to Success.
8. Scroll down to review the results.<br/>
![model_eval_job_results](/img/model_eval_job_results.png?raw=true)

### Lab 9: Deploy Project into Production
1. You must have completed Lab 1, Lab 7 and Lab 8 before working through this lab.
2. Navigate to the top of the project assets page and click **Commit and push**.<br/>
![commit_push](/img/commit_push.png?raw=true)
3. Specify the **commit message** about the changes you are committing, e.g. "*deploy generated scripts*".
4. Specify a **version tag**, e.g. *workshop-release*.  A version tag marks a deployment ready version of the project, and identifies a specific verion of the project.
5. Click **Commit and push**.
6. Navigate to the **Deployment Manager**.  <br/>
![deployment_manager](/img/deployment_manager.png?raw=true)
7. Click the **+** icon to create a project release.
8. Specify the following inputs
* Name: WorkshopRelease1
* Route: release1 (this string will be used in all URLs that are generated by deployment, that’s why it can’t have spaces, upper case characters, and special characters). Important: if you’re sharing a cluster, make the route unique, for example, add initials to release1. 
* Source project: the project that you want to deploy
* Tag: tag that you specified in the earlier steps. 

9. Click **Create**. This will take a few minutes because DSX is making a copy of all assets in the project.
10. The default view shows all assets that are a part of the project. Notice that you can filter them by type if you select the drop down. 
11.  Filter the assets by **Models**.
12. Click **Web service** to define an **Online Deployment** for the model.
13. Specify the name *telco-churn-online*.  Notice that the name gets appended to the URL (REST endpoint), that’s why it has to be lowercase with no special characters. 
14. Click **Create**
15. The **REST endpoint** is displayed in the model details. This endpoint won’t be live until we launch the project.<br/>
![mmd_rest_endpoint](/img/mmd_rest_endpoint.png?raw=true)<br/>
16. Filter the assets by **Scripts** and configure jobs for the batch scoring and model evaluation scripts.
17. Click the **Deployments** tab to list all the deployments you have created. <br/>
![mmd_deployments](/img/mmd_deployments.png?raw=true)<br/>
18. The deployments are in a disabled state because the project has not been launch.  Click the **Launch** button at the top right corner.<br/>
Launching the release will:
* Start all environments that will be used for deployment
* Enable the REST endpoints
* Enable URLs for “applications” (notebooks and Shiny)
* Enable schedules (if they are configured)
* Enable on-demand invocation of jobs. 

19. When all the deployments are enabled, click on any of the deployments and test them either with an API call or run a batch job on demand.







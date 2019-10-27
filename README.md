# WSL Local Workshop V1.2
In this workshop you will learn how to develop and deploy applications in WSL Local. The workshop has been divided into several stand-alone parts for those who are interested in a specific development tool or deployment task.

This lab is meant to be instructor-led.  That is, the instructor will explain the objectives of the WSL capabilities covered in each lab, and demonstrate some of those capabilities at the beginning of each lab.


## About this repository
This repository contains several lab subfolders. Some labs include notebooks and data, while others have additional instructions that are located in the *Lab Instructions* folder. 

## Prerequisites
1. Knowledge of analytics. These labs do not teach you the basics of analytics or how to implement analytics in R, Python and SPSS. The purpose of this workshop is to provide hands-on experience with analytics tools and deployment functions in WSL Local. 
2. To run this workshop you need an instance of WSL Local V1.2.3 or above. 

3. Download [WSL_Demos.zip](https://github.com/jpatter/DSX_Local_Workshop_V12/blob/master/DSX%20Local%20Projects/DSX_Demos.zip?raw=true).

### Setting up lab projects in WSL Local
1. Rename the downloaded **WSL_Demos.zip** file and give it a unique name.  For example, add your initials (i.e. WSL_Demos_JP.zip).    *Note: Project names in WSL Local cluster must be unique. When we create a project "from file", the project name is inherited from the file name*.
2. Login to WSL Local.
3. Select "New Project" and select "From File".
4. Browse to the .zip file and click **Create**.
![ProjectFromFile](/img/CreateProjectFromFile.png?raw=true).

### Lab 1: Build, Save and Test SparkML Models (Jupyter/Python)
1. Open the project you just created. 
2. Navigate to **Assets** view and open **TelcoChurn_SparkML_35** *Jupyter* notebook. This notebook has been implemented for the Python 3.5 runtime. You can verify the runtime by running the first cell in the notebook. 
3. Follow instructions in the notebook.

Review:
1. Save and checkpoint
2. How to run a cell
3. Restarting the kernel (pixiedust)
4. Testing the model
5. Setting the scoring endpoint
6. Stopping the kernel
 
Goals:
1. Familiarity with Jupyter notebook -- note time it takes to start notebook
2. Importing libraries (included in image and external i.e. pixiedust)
3. Save model to repository (dsx_ml package)
4. Test model via UI -- also view installed packages
5. Test model via REST
6. Note notebook is still running

### Lab 2: Build, Save and Test Scikit-Learn Models (Jupyter/Python)
1. Navigate to **Assets** view and open **CreditCardDefault_SkLearn** notebook.  
2. Follow instructions in the notebook.

Review:
1. Jupyter magics (i.e. %brunel, %matplotlib)

Goals:
1. Note faster notebook start time
2. %brunel cells

### Lab 3: Build, Save and Test SparkML models (Zeppelin/Python)
1. Navigate to **Assets** view and open **TelcoChurn_Zeppelin** notebook.  
2. Follow instructions in the notebook.

Review:
1. Interpreter bindings
2. Running paragraphs 
3. Zeppelin magics
4. Graph interactions

Goals:
1. Note multiple interpreters
2. Multiple magics i.e. %sql, %spark.pyspark

### Lab 4: Build R models in Jupyter and deploy into Shiny App
1. Follow the instructions in Lab Instructions/R_in_WSL.pdf

Review:
1. Jupyter notebook but R
2. system() calls -- underlying filesystem
3. Running RStudio
4. Publishing to Shiny server (unique name!)
5. Content visibility
6. Permalink (please save this when shown)

Goals:
1. R notebook
2. Loading R libraries
3. Saving model to RStudio File System (this will NOT show in Models view)
4. RStudio / Shiny
5. Publishing to Shiny

### Lab 5: Watson Machine Learning
1. Follow the instructions in Lab Instructions/WatsonMachineLearning.pdf

Goals:
1. Uploading Data Sets
2. Introduction to Watson Machine Learning

### Lab 6: SPSS Modeler in WSL -- consider changing for Lab in Lab Instructions
1. Follow the instructions in Lab Instructions/SPSS_Modeler_in_WSL.pdf

Goals:
1. Introduction to SPSS Modeler

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

Review:
1. Batch scoring
2. Options (parameters, scheduling)

Goals:
1. Introduction to batch scoring

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

### Lab 9: Deploy Project into Production -- review WSL_Deployment.pdf in Lab Instructions
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
11. Filter the assets by **Models**.
12. Select **Telco_Churn_ML_Model**
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

### Lab 10: WSL Data Sources

1. Follow the instructions in Lab Instructions/WSL_DataSources.pdf






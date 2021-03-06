


# Bank-Marketing-Project 
In this project, AutoML is used to find the best algorithm. The Dataset is used here is bank Marketing dataset. It is a classification problem 

After finding the best algorithm, model is deployed,published and made available to consume the endpoint using python SDK and Designer 

## Architectural Diagram
<img width="626" alt="screen-shot-2020-09-15-at-12 36 11-pm" src="https://user-images.githubusercontent.com/51949018/115059405-24bd3f80-9f04-11eb-8cf3-f0c66ee837af.png">
In this project, we will following the below steps:

1. Authentication
2. Automated ML Experiment
3. Deploy the best model
4. Enable logging
5. Swagger Documentation
6. Consume model endpoints
7. Create and publish a pipeline


## Key Steps
### Authentication

Since I was using the lab provided by the Udacity, the authentication was already done

For running the experiment, the dataset used is [Bank-Marketing](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv) datset. First we are going to create a compute instance of `Stanard_D12_V2` with minimum 1 node

### Dataset 
The screenshot of the loaded Dataset
![dataset](https://user-images.githubusercontent.com/51949018/115060639-bd07f400-9f05-11eb-8d1f-435385aad509.png)

Next, we are going to create AutoML experiment and below is the screenshot showing the completion of AutoML run with best algorithm as **Voting Ensemble** 
![completed_autoML](https://user-images.githubusercontent.com/51949018/115062126-a06cbb80-9f07-11eb-9797-29fee3e06087.png)

screenshot of best model 
![best_model - Copy](https://user-images.githubusercontent.com/51949018/115062293-d27e1d80-9f07-11eb-9a19-3eede017f0a6.png)

Deploying best model 

Now the best model is deployed with the name *deploy-model* and `key-based authentication is =True`
![deploy](https://user-images.githubusercontent.com/51949018/115062477-01948f00-9f08-11eb-95e5-8b2944e3f269.png)

## Enable logging 
Azure provides valuable information after deployment using App-Insights. For accessing the app-insights 

### Run log.py 
![app insight1](https://user-images.githubusercontent.com/51949018/115063130-cba3da80-9f08-11eb-9506-2dffe11e4efa.png)
![app_insights](https://user-images.githubusercontent.com/51949018/115063140-cf376180-9f08-11eb-9f42-c1edb1cc2815.png)

Now go to azure studio and in the endpoints section, we can see that the Application insights are enabled
![app insight proof](https://user-images.githubusercontent.com/51949018/115063403-25a4a000-9f09-11eb-8ce4-fab6ed77917b.png)

To enable app insights `config.json` file is downloaded in the folder where docker is running and run  logs.py file is run 

## Swagger documentation 
In this Swagger container is deployed to view the swagger documentation. To run Swagger, swagger.json file is downloaded into the swagger folder and swagger.sh and serve.py are run with port as 

` docker run -p 9000:8080 swaggerapi/swaggerui `

serve.py after running
![serve1](https://user-images.githubusercontent.com/51949018/115064166-3bff2b80-9f0a-11eb-95ac-2516afc3775e.png)
![serve2](https://user-images.githubusercontent.com/51949018/115064172-3e618580-9f0a-11eb-9f26-c0e4a15822b4.png)

after running swagger.sh 
![swaggerbash](https://user-images.githubusercontent.com/51949018/115064633-c9428000-9f0a-11eb-9cc4-a4a51feb48a6.png)
We can see GET and POST requests for swagger

## Consume End points
Now once the model is deployed. We can run endpoints.py file to check and interact with the model. To run endpoints.py file, replace `scoring_uri` and `key` of the deployed service and endpoints.py 

![endpoint](https://user-images.githubusercontent.com/51949018/115065202-787f5700-9f0b-11eb-8632-953ccd90654e.png)


## Create and Publish a pipeline
To create a pipeline, we are going to creat a pipepline instance using AutoMLConfig by passing required parameters. Once the pipeline is run, the pipeline could be published with best parameters. This published could be accessed remotely using Python SDK as RESTAPI

![pipeline2](https://user-images.githubusercontent.com/51949018/115098690-003a8500-9f4f-11eb-9b98-b6f29f416356.png)
This screenshot showing completed status which I have zoomed in
![completed status1](https://user-images.githubusercontent.com/51949018/115074403-4aa00f80-9f17-11eb-8eaf-56544f6f5587.png)

![datasets](https://user-images.githubusercontent.com/51949018/115074436-54297780-9f17-11eb-913f-bcaf87abe971.png)

publishing the pipeline and access the RESTAPI

![RESTpipeline](https://user-images.githubusercontent.com/51949018/115074860-e29df900-9f17-11eb-90fa-47987bf5f3d7.png)
![Resturl](https://user-images.githubusercontent.com/51949018/115074863-e5005300-9f17-11eb-8a3a-11499875fe92.png)

`RunWidget`
![widget2](https://user-images.githubusercontent.com/51949018/115074870-e762ad00-9f17-11eb-8411-5f5ae3f04d39.png)
![run widget](https://user-images.githubusercontent.com/51949018/115074880-e92c7080-9f17-11eb-8620-8a1f58b6ad01.png)



## Screen Recording
[YouTube Link](https://youtu.be/I2YEtZKv4Gc)

## Standout Suggestions
* Remove negative co-related features and run the model 
* Increase the number of iterations and check for accuracy 
* changing the target column and checking for output result 

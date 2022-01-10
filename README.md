# Image Classification using AWS SageMaker

Use AWS Sagemaker to train a pretrained model that can perform image classification by using the Sagemaker profiling, debugger, hyperparameter tuning and other good ML engineering practices. This is done on dog breed classication data set.

## Project Set Up and Installation
Enter AWS through the gateway in the course and open SageMaker Studio.
Download the starter files.
Download/Make the dataset available. 

## Dataset
The provided dataset is the dogbreed classification dataset which can be found in the classroom.
The project is designed to be dataset independent so if there is a dataset that is more interesting or relevant to your work, you are welcome to use it to complete the project.

### Access
Upload the data to an S3 bucket through the AWS Gateway so that SageMaker has access to the data. 

## Hyperparameter Tuning
What kind of model did you choose for this experiment and why? Give an overview of the types of parameters and their ranges used for the hyperparameter search
I used the 'resnet50' pretrained model for this experiment, because as a starter project for transfer learning this is a good choice.
The hyperparameters and the ranges used are; 
    learning-rate ContinuousParameter(0.001, 0.1),
    batch-size:   CategoricalParameter([32, 64, 128, 256, 512]),
    epochs:       IntegerParameter(2,10)
and test-batch-size: "100"

Remember that your README should:
- screenshot are available in this project folder for
    --hyperparameter tuning job
    --training jobs
    --log metrics
    
-the best best hyperparameters from all the training jobs are;
{'test-batch-size': '100',
 'epochs': '9',
 'batch-size': 256,
 'lr': '0.087281525554365'}


## Debugging and Profiling

modelVanishingGradient: NoIssuesFound
Overfit: NoIssuesFound
Overtraining: NoIssuesFound
PoorWeightInitialization: NoIssuesFound
LossNotDecreasing: NoIssuesFound
LowGPUUtilization: IssuesFound
ProfilerReport: IssuesFound

### Results
There were no issues in the debugger report.
In the profiler report there were issues with low gpu utilization.
This could be due to the powerful instance type I used, 'ml.g4dn.2xlarge'.
Where as the memory is concerned I don't see any issue, it looks ok.


## Model Deployment
The model has been deployed using the PyTorchModel. For this I used a separate script 'inference.py'. When I used the training script it gave error for smdebug model. So, instead of modifying the training script, I used separate script.

The endpoint can be queried using the code in the notebook. The url of the test image needs to used to fetch the image. Then preprocess the image and pass it to endpoint for prediction.

The screenshot of the endpoint inservice is available in this project folder.

# Image Classification using AWS SageMaker

Use AWS Sagemaker to train a pretrained model that can perform image classification by using the Sagemaker profiling, debugger, hyperparameter tuning and other good ML engineering practices. This can be done on either the provided dog breed classication data set or one of your choice.

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

The model is built with convolutional resnet34 pretrained model based on 34 layers. 
I have used for fine-tuning following hyperparameter ranges: 
1. "lr": ContinuousParameter(0.001, 0.1),
2. "batch_size": CategoricalParameter([32, 64, 128, 256])

Below is list of training jobs in the screenshot:
![Alt text](training_jobs.png?raw=true "training_jobs.png")
 
Hyperparameter tuning jobs completed jobs:
![Alt text](training_jobs.png?raw=true "training_jobs.png")
 
Logs from the last completed training job with metrics during the process:

 ![Alt text](logs.png?raw=true "logs.png")


## Debugging and Profiling
During of training I didn’t know model performance, whether accuracy is acceptable. For visualization was applied graphical representation of the Cross Entropy Loss which is shown below.

![Alt text](plots.png?raw=true "plots.png")


### Results
**TODO**: What are the results/insights did you get by profiling/debugging your model?

**TODO** Remember to provide the profiler html/pdf file in your submission.

I have tried a few training jobs, here is summary with metrics and insights of last training job: 
From shown information about trained job, built model is not overfitted, some errors are in overtraining, so need more investigate to weight initialization, probably running on GPU may impact(trigger error, so was used cpu)
![Alt text](training_metrics.png?raw=true "training_metrics.png")


## Model Deployment
The model was deployed in ml.m5.xlarge instance and used cuda-cpu as device for training.
There are deployed endpoints in inferences.
![Alt text](endpoint.png?raw=true "endpoint.png")
For querying the endpoint is needed to add the path of test data image by opening for reading this file and triggering predict function of model.


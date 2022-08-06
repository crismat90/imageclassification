# Image Classification using AWS SageMaker

Use AWS Sagemaker to train a pretrained model that can perform image classification by using the Sagemaker profiling, debugger, hyperparameter tuning and other good ML engineering practices. This can be done on either the provided dog breed classication data set or one of your choice.
In my case, I have used a pretrained Resnet50 model. We can find this model in the pytorch library: https://pytorch.org/vision/main/models/generated/torchvision.models.resnet50.html

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

I used a pretrained model from pytorch: Resnet50. I have read several articles and the results for image classification were very good, so I decided to try it in this exercise.

We can see here the training jobs:

![image](https://user-images.githubusercontent.com/23742704/183263521-3e0875a9-2f86-4650-9355-eee79dfc6b9f.png)


You can see the profiling report in this link: https://github.com/crismat90/imageclassification/blob/main/profiler-report.ipynb

Remember that your README should:
- Include a screenshot of completed training jobs
- Logs metrics during the training process
- Tune at least two hyperparameters
- Retrieve the best best hyperparameters from all your training jobs

## Debugging and Profiling

![image](https://user-images.githubusercontent.com/23742704/183263229-ee86d862-37b0-4667-8352-7986d925b52a.png)

### Results

![image](https://user-images.githubusercontent.com/23742704/183263569-ef0507b6-3a68-4a03-b90a-b245c2acc4a2.png)



The best hyperparameter post hyperparameter tuning are:
{'batch_size': 128, 'eps': '8.936808045433904e-09', 'lr': '0.059950406352148315', 'weight_decay': '0.0014226239220162377'}

Profiler html: https://github.com/crismat90/imageclassification/blob/main/profiler-report.html


![image](https://user-images.githubusercontent.com/23742704/183263798-58431d4b-1bfd-44f3-af9d-09e498180420.png)

## Model Deployment

Here we can see the code for the endpoint: https://github.com/crismat90/imageclassification/blob/main/endpoint_inference.py
As it was mentioned before, a restnet50 was used. As we have 133 classes of dogs, our output has to be 133, as many ouputs as the different dog classes that we have.


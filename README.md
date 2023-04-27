
Cloud Native Monitoring Application on EKS

We will create a monotoring application in Python using flask. We will start by building the application and contairize it using Docker file, we will build the image and then run the Container locally, then we will create an ECR or elastic container registry using Python Moto3 module, initiate the Docker image to store retrieve and use the Docker images in secure and efficient manner.Next, we will move to the deployment phase where we will create Elastic Kubernetes Cluster with nodes and deploy the application on Kubernetes. We will cerate deployment and service using Python so the applacation can be access from the internet which is deployed on Kubernetes. For that we will need the following tools:
* VSCode Editor
* AWS Account
* Docker and Kubectl installed




## Documentation

https://hub.docker.com/_/python/

https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

https://auth.acloud.guru/




## Deployment

1- Write a python code (app.py) to import psutil from flsk to The CPU and Memory metrics.

```bash
$ pip3 install psutil
```
Create a file insert and  all modules that you will be using.
```bash
$ pip3 install -r requirements.txt
```
Run the application and display its url on the browser
```bash
$ python3 app.py
```
2- Create a Dockerfile,contenerize the app and run it locally as a container.
```bash
$ docker build -t my-flask-app .
$ docker images
$ docker run -p 5000:5000 eb92dfb9d32d
````
3- Application deployment on AWS-EKS.
```bash
$ aws configure
$ AWS Access Key ID [None]:
$ AWS Secret Access Key [None]:
$ Default region name [US East (N. Virginia)]:
$ Default output format [us-east-1US East (N. Virginia) us.east-1]:
````
* Create a Cloud Repo using Python vscode (ecr.py)vs Boto3 and push the Docker image to ECR.
```bash
$ python3 ecr.py
$ aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 371032487219.dkr.ecr.us-east-1.amazonaws.com
$ docker build -t my-cloud-app .
$ docker tag my-cloud-app:latest 371032487219.dkr.ecr.us-east-1.amazonaws.com/my-cloud-app:latest
$ docker push 371032487219.dkr.ecr.us-east-1.amazonaws.com/my-cloud-app:latest
```
* Create Cluster and Nodes on Elastic Kubernets Service (EKS) and create a Python code (eks.py) to deploy the app.
```bash
$ python3 eks.py
$ kubectl get pods -n default -w
$ kubectl get service
$ kubectl get deployement -n default
$ kubectl port-forward svc/my-flask-service -p 5000:5000
```



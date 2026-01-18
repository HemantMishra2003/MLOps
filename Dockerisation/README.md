#### Deployment link using docker in Railway cloud service : 
https://mri-cancer-detector-production.up.railway.app

# Dockerisation  full process.
___________________________________________________________________________________________________

### 1. Our folder structure 
 
    │
    ├── dockerization/
    │   ├── Dockerfile
    │   ├── requirements.txt
    │   ├── README.md
    │
    ├── app/
    │   ├── app.py
    │   ├── assets/
    │   └── model/
    │
    ├── deployment/
    │   └── railway.md
    │
    └── README.md

 ## 1. Created a Dockerfile 

Inside my project, I created a Dockerfile to containerize the entire application.

The Dockerfile included:

a. Base Python image

b. Installation of requirements.txt

c. Copying all project files into the container

d. Final command to run the Streamlit app

#### Dockerfile Code

    FROM python:3.10-slim

    WORKDIR /app
- here we are makin the app folder inside the docker
  
      COPY requirements.txt .
      RUN pip install --no-cache-dir -r requirements.txt

      COPY . .
- here  we are using copy function to put all my
- folder structure into the docker inside app folder.

      CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]

## 2. Built Docker Image Locally

I used the following command to build my local Docker image:

    docker build -t myapp .
This created a local image named myapp

The image contains:
a. app.py
b. Streamlit UI
c. ML model + weights
All required Python libraries

- Now the entire project is sealed inside a single Docker image.

## 3. Created a Repository on Docker Hub

I created a Docker Hub repo named:

    vhemant/mri-cancer-detector
Then tagged my local image to match the repo name:

    docker tag myapp vhemant/mri-cancer-detector

And pushed it to Docker Hub:

    docker push vhemant/mri-cancer-detector


- This made my Docker image available online for deployment.

## 4. Deployed the Docker Image on Railway

On Railway:

a. Selected Deploy from Docker Image
b. Provided my image name:

    c. vhemant/mri-cancer-detector
    
Railway pulled the image from Docker Hub

Railway created a cloud container using that image

Set environment variable:

PORT = 8501


Exposed port 8501 as Public

#### My Streamlit ML app became available on a public URL.

## Final Deployment Flow (Easy to Remember)
     Dockerfile  
          ↓  
    Local Docker Image  
          ↓  
     Docker Hub  
          ↓  
    Railway Deployment  
          ↓  
    Public Streamlit App (Live)






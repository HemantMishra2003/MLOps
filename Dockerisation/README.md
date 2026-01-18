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

Base Python image

Installation of requirements.txt

Copying all project files into the container

Final command to run the Streamlit app

👉 This step packaged my entire ML project into a reproducible environment.





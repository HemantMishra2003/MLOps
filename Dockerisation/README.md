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

👉 Dockerfile Code

    FROM python:3.10-slim

    WORKDIR /app
- here we are makin the app folder inside the docker
  
      COPY requirements.txt .
      RUN pip install --no-cache-dir -r requirements.txt

      COPY . .
- here  we are using copy function to put all my
- folder structure into the docker inside app folder.

      CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]






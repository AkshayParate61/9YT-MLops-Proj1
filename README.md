# MLOps Project: Vehicle Classification

Welcome to the MLOps Project for Vehicle Classification! This repository demonstrates how to set up and deploy an end-to-end Machine Learning pipeline using modern MLOps practices. The project leverages various tools and services like MongoDB, AWS, Docker, CI/CD with GitHub Actions, and more. This README will walk you through the setup, features, and key components of the project.

## Project Features

- **Template Setup**: Easily set up the project structure with a single Python template.
- **MongoDB Integration**: Store and manage data on MongoDB Atlas.
- **Data Ingestion**: Fetch and process data from MongoDB into a usable format for ML tasks.
- **Model Training & Evaluation**: Train machine learning models and evaluate their performance.
- **Model Deployment**: Deploy models using AWS S3 for storage and access.
- **Prediction Pipeline**: Implement a streamlined prediction pipeline to serve model predictions.
- **CI/CD Pipeline**: Automate the entire process from development to deployment using GitHub Actions and AWS EC2.

## Getting Started

### 1. **Project Setup**

1. **Create Project Template**: 
    - Run the `template.py` file to generate the project template.
    
2. **Setup Local Packages**: 
    - Edit the `setup.py` and `pyproject.toml` to import local packages as outlined in the `crashcourse.txt` file.

3. **Create Virtual Environment**:
    - Execute the following commands to create a virtual environment and install necessary dependencies:
      ```bash
      conda create -n vehicle python=3.10 -y
      conda activate vehicle
      pip install -r requirements.txt
      ```

4. **Check Installed Packages**:
    - Verify that local packages are installed:
      ```bash
      pip list
      ```

### 2. **MongoDB Setup**

1. **Create MongoDB Atlas Account**:
    - Sign up for [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) and create a project.
    - Set up a cluster and configure your MongoDB database user credentials.

2. **Configure MongoDB Connection**:
    - Add IP address access: `0.0.0.0/0` (for access from anywhere).
    - Get your MongoDB connection string and replace the password.
    - Save the connection string for later use.

3. **Data Ingestion from MongoDB**:
    - Create a folder called `notebook`, and within that, create the `mongoDB_demo.ipynb` file to start pushing data to MongoDB using Python.

### 3. **Logging and Exception Handling**

- **Logger**: Implement logging functionality in `logger.py` and test it with `demo.py`.
- **Exception Handling**: Write custom exceptions in `exception.py` and test them in `demo.py`.

### 4. **Data Ingestion, Validation, and Transformation**

- **Data Ingestion**: 
    - Configure MongoDB connection and fetch data from the database.
    - Transform the data into a usable DataFrame format.
    - Define the `DataIngestionConfig` and `DataIngestionArtifact` classes to manage the ingestion process.

- **Data Validation**: 
    - Add necessary schema and validation logic to ensure the dataset is clean and accurate before processing.

- **Data Transformation**: 
    - Perform feature engineering and transform the dataset as needed to prepare for model training.

### 5. **Model Training and Deployment**

- **Model Trainer**: 
    - Create and train machine learning models using various algorithms. 
    - Implement the `ModelTrainer` class to manage the training process.

- **Model Evaluation**: 
    - Evaluate the model performance by defining a threshold score and pushing the model to the S3 bucket.

- **Model Pusher**: 
    - Use AWS S3 to push the trained model into a storage bucket.

### 6. **AWS Setup for Model Deployment**

1. **AWS IAM User Setup**:
    - Create a new IAM user with AdministratorAccess, then download the access keys and configure the environment variables.
    
2. **S3 Bucket Setup**:
    - Create an S3 bucket in AWS (Region: `us-east-1`) for storing models.
    
3. **Push Model to AWS S3**:
    - Use the created IAM user credentials and `aws_connection.py` to connect to S3 and push the trained model.

### 7. **Prediction Pipeline**

- **Prediction Pipeline**:
    - Set up the prediction pipeline and implement the necessary logic in `app.py` to serve predictions from the deployed model.

### 8. **CI/CD Pipeline**

1. **Docker Integration**:
    - Set up a `Dockerfile` and `.dockerignore` to containerize the application.

2. **GitHub Actions**:
    - Create a CI/CD pipeline with GitHub Actions. Set up an ECR repository to store the Docker image and automate the deployment process.

3. **EC2 Setup**:
    - Set up an AWS EC2 instance to deploy the model. Install Docker and connect your GitHub repository with the EC2 instance.

4. **Expose the Application**:
    - Open port 5000 on the EC2 instance to access the app from your browser.

### 9. **Final Steps**

- **Run the Model**: Test the model by sending data to the `/training` route for real-time predictions.
- **Monitor Deployment**: Ensure that the app is correctly deployed and can serve model predictions via the exposed public IP address.

---

## File Structure Overview

Here’s an overview of the key directories and files:

- `src/`: Contains core functionality such as configuration, database connections, and model training.
- `notebooks/`: Jupyter notebooks for MongoDB data ingestion and analysis.
- `entity/`: Contains entities like `DataIngestionConfig`, `ModelTrainer`, etc.
- `aws_storage/`: AWS S3 configurations for model storage.
- `.github/workflows/`: CI/CD pipeline configuration files.
- `static/` and `templates/`: Frontend assets for serving the model predictions.

---

## Tools and Technologies Used

- **Python**: The core programming language for all components.
- **MongoDB Atlas**: Cloud-based NoSQL database for data storage.
- **AWS S3**: Cloud storage service for saving and retrieving models.
- **Docker**: Containerization of the application.
- **GitHub Actions**: CI/CD pipeline for automating testing and deployment.
- **EC2**: Virtual servers for hosting the application.
- **Conda**: Package and environment management for Python dependencies.

---

## Conclusion

This MLOps project showcases a comprehensive and scalable approach to machine learning pipeline development, training, and deployment. By utilizing MongoDB, AWS services, Docker, and CI/CD practices, this project ensures a robust, efficient, and automated flow from data ingestion to model deployment. It's the perfect example of how modern MLOps tools can be applied in a real-world scenario!

---

### Ready to get started?

Clone this repository and follow the steps in this README to set up the project and deploy your model!
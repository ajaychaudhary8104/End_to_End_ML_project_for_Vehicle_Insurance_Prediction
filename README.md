# Vehicle Insurance Prediction - End-to-End MLOps Project

![Python](https://img.shields.io/badge/Python-3.10-blue)
![AWS](https://img.shields.io/badge/AWS-S3%20|%20ECR%20|%20EC2-orange)
![Docker](https://img.shields.io/badge/Docker-Enabled-blue)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-green)
![CI/CD](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-blueviolet)

## 📌 Project Overview
This project is a comprehensive, end-to-end Machine Learning solution designed to predict whether a customer will be interested in Vehicle Insurance. It demonstrates a full lifecycle MLOps implementation, ranging from data ingestion and preprocessing to model training, evaluation, and deployment on the cloud.

The system is built with a modular architecture, ensuring scalability and maintainability, and is deployed using Docker containers on AWS EC2 with a CI/CD pipeline via GitHub Actions.

## 🚀 Key Features
- **End-to-End Pipeline**: Automated pipeline for data ingestion, validation, transformation, model training, and evaluation.
- **MLOps Best Practices**: Implementation of modular coding, custom logging, exception handling, and artifact management.
- **Cloud Integration**: 
  - **AWS S3**: For storing model artifacts and datasets.
  - **AWS ECR**: For storing Docker images.
  - **AWS EC2**: For hosting the application.
  - **MongoDB Atlas**: As the primary data source.
- **CI/CD Automation**: Fully automated deployment pipeline using GitHub Actions and self-hosted runners.
- **Imbalance Handling**: Utilizes `SMOTEENN` to handle class imbalance in the dataset.
- **Containerization**: Dockerized application for consistent environments across development and production.

## 🛠️ Tech Stack
- **Programming Language**: Python 3.10
- **Machine Learning**: Scikit-Learn, Pandas, NumPy, Imbalanced-learn
- **Web Framework**: FastAPI (for serving predictions)
- **Database**: MongoDB
- **DevOps & Cloud**: Docker, GitHub Actions, AWS (S3, ECR, EC2)
- **Infrastructure as Code**: Setup scripts and TOML configuration.

## 📂 Project Architecture
The project follows a component-based architecture:
1.  **Data Ingestion**: Fetches data from MongoDB and splits it into train/test sets.
2.  **Data Validation**: Validates data against a defined schema.
3.  **Data Transformation**: 
    -   Handles missing values.
    -   Performs feature scaling (StandardScaler, MinMaxScaler).
    -   Encodes categorical variables.
    -   Balances the dataset using SMOTEENN.
4.  **Model Trainer**: Trains classification models.
5.  **Model Evaluation**: Evaluates the model against thresholds and previous versions.
6.  **Model Pusher**: Pushes the best-performing model to the AWS S3 bucket.
7.  **Deployment**: The application is packaged into a Docker image and deployed to an AWS EC2 instance.

## ⚙️ Installation & Setup

### Prerequisites
- Python 3.8+
- MongoDB Atlas Account
- AWS Account (with Access Keys)
- Docker

### 1. Clone the Repository
```bash
git clone https://github.com/ajaychaudhary8104/End_to_End_ML_project_for_Vehicle_Insurance_Prediction.git
cd End_to_End_ML_project_for_Vehicle_Insurance_Prediction
```

### 2. Create Virtual Environment
```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
```

### 3. Environment Variables
Create a `.env` file or export the following variables:
```bash
export MONGODB_URL="your_mongodb_connection_string"
export AWS_ACCESS_KEY_ID="your_aws_access_key"
export AWS_SECRET_ACCESS_KEY="your_aws_secret_key"
export AWS_DEFAULT_REGION="us-east-1"
```

### 4. Run the Pipeline
To start the training pipeline:
```bash
python demo.py
```

### 5. Run the Web App
To start the FastAPI application:
```bash
python app.py
```
Access the application at `http://localhost:5000`.

## 🔄 CI/CD Pipeline
The project uses **GitHub Actions** for Continuous Integration and Deployment.
1.  **Push to Main**: Triggers the pipeline.
2.  **Build**: Builds the Docker image.
3.  **Push to ECR**: Pushes the image to Amazon Elastic Container Registry.
4.  **Deploy**: A self-hosted runner on AWS EC2 pulls the latest image and runs the container.

## 🤝 Contributing
Contributions are welcome! Please fork the repository and submit a pull request.

## 📝 License
This project is licensed under the MIT License.
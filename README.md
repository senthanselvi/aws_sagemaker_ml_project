# End-to-End Machine Learning with AWS SageMaker

**Project Overview**

This project demonstrates how to build and deploy a complete machine learning pipeline using Amazon SageMaker. It covers all stages of the ML lifecycle — including data preprocessing, model training with SageMaker’s built-in algorithms, deployment to a real-time endpoint, and making predictions — all within a single, cohesive workflow.

**Technologies Used**
- AWS SageMaker Studio
- Amazon S3
- SageMaker Linear Learner Algorithm
- Python, Pandas, NumPy, Scikit-learn
- Boto3

**Problem Statement**
Predict student exam scores based on study hours using a simple linear regression model trained and deployed on SageMaker.

**Dataset**
- Name: `student_scores.csv`
- Source: Kaggle

**Project Workflow**
**1. Setup SageMaker Studio**
- Launch SageMaker in your preferred AWS region.
- Create a SageMaker domain and user profile.
- Launch JupyterLab and create a notebook.

**2. Upload Dataset**
- Use the UI or script to upload `student_scores.csv` into your environment.

**3. Data Preparation**
- Read the CSV using `pandas`.
- Perform preprocessing:
  - Convert to `float32`
  - Split data into train/test sets (80/20)
  - Format data using `sagemaker.amazon.common.write_numpy_to_dense_tensor`

**4. Create and Upload to S3**
- Create a new s3bucket.
- Upload training and test data to the bucket using `boto3`.

**5. Define and Train Model**
- Use SageMaker's `get_image_uri()` to fetch the Linear Learner container.
- Define an `Estimator` using:
  - Instance type: `ml.c4.xlarge`
  - Output path: S3 bucket URI
  - Hyperparameters: `predictor_type=regressor`, `loss=absolute_loss`, etc.
- Call `.fit()` to train the model.

**6. Deploy Model**
- Deploy the trained model as an endpoint:
  ```python
  predictor = linear.deploy(instance_type="ml.m4.xlarge", initial_instance_count=1)

**7. Delete Endpoint**
- predictor.delete_endpoint()


![image](https://github.com/user-attachments/assets/d3bd0484-fd8e-4e9f-ac88-b8450ae0329e)

![image](https://github.com/user-attachments/assets/60c3a7f4-c23f-4b73-ad7a-83de92537548)

![image](https://github.com/user-attachments/assets/862b73dd-5e73-406a-9e9b-b0aafb74febb)

![image](https://github.com/user-attachments/assets/b6f811d6-d4e3-42f8-b3ff-090aed726f1d)

![image](https://github.com/user-attachments/assets/aa3e6e71-06f4-4992-bda1-834c84554167)






 


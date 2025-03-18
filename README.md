# **End-to-End Machine Learning Project with AWS Elastic Beanstalk Deployment**  

### 🚀 **Overview**  
This project implements an **end-to-end machine learning pipeline**, covering **data ingestion, transformation, model training, and inference**. The trained models are deployed using **Flask**, and the entire application is hosted on **AWS Elastic Beanstalk (EBS)**.  

---

## ⚙️ **Machine Learning Models Implemented**  
The project trains multiple **regression models** and evaluates them using **R² scores**:  

```python
models = {
    "Linear Regression": LinearRegression(),
    "Lasso": Lasso(),
    "Ridge": Ridge(),
    "K-Neighbors Regressor": KNeighborsRegressor(),
    "Decision Tree": DecisionTreeRegressor(),
    "Random Forest Regressor": RandomForestRegressor(),
    "XGBRegressor": XGBRegressor(), 
    "CatBoosting Regressor": CatBoostRegressor(verbose=False),
    "AdaBoost Regressor": AdaBoostRegressor()
}
```

- The models are trained and stored as **model.pkl** along with **preprocessor.pkl** for data transformation.  
- Performance evaluation metrics like **R² score** are stored for comparison.  

---

## 🌐 **Flask Web App Usage**  
1. **Run Flask Application**  
   ```bash
   python application.py
   ```
2. Open **http://localhost:5000/** in the browser.  
3. **Navigate to Prediction Page**  
   - After loading the home page, manually enter `/predictdata` in the URL.  
   - Enter feature values to get predictions.  

---

## 🚀 **Deploying to AWS Elastic Beanstalk**  

### **1️⃣ Install AWS CLI & EB CLI**  
If not installed, install them:  
```bash
# AWS CLI
pip install awscli --upgrade --user  

# AWS Elastic Beanstalk CLI
pip install awsebcli --upgrade --user  
```

### **2️⃣ Configure AWS CLI**  
```bash
aws configure
```
Enter your **AWS Access Key ID**, **Secret Key**, **Region (e.g., us-east-1)**.

### **3️⃣ Create Elastic Beanstalk Application**  
```bash
eb init -p python-3.8 ML_Project --region us-east-1
```
- Select **default region**.  
- Choose **application name**: `ML_Project`.  

### **4️⃣ Set Up Beanstalk Environment**  
```bash
eb create ml-env
```
- This creates an environment **ml-env** where the app will be deployed.

### **5️⃣ Deploy Application to AWS EBS**  
```bash
eb deploy
```

### **6️⃣ Open the Application in Browser**  
```bash
eb open
```

---

## ⚙️ **Elastic Beanstalk Configuration**  

📌 **`.ebextensions/python.config`** (Handles WSGI Setup)  
```yaml
option_settings:
  "aws:elasticbeanstalk:container:python":
    WSGIPath: application:application
```
- This ensures the Flask app runs on EBS.


---

## 🏗 **Project Setup (Local Execution)**  

### **1️⃣ Clone the Repository**  
```bash
git clone https://github.com/Koushik7893/End-to-End-ML-Project-with-AWS-Elastic-Beanstalk-Deployment.git
cd End-to-End-ML-Project-with-AWS-Elastic-Beanstalk-Deployment
```

### **2️⃣ Install Dependencies**  
```bash
pip install -r requirements.txt
```

### **3️⃣ Train & Evaluate Models**  
```bash
python pipeline/train_pipeline.py
```

### **4️⃣ Run Flask App**  
```bash
python application.py
```

---

## 📌 **Technologies Used**  
- **Python**  
- **Flask** (Web Framework)  
- **AWS Elastic Beanstalk (EBS)** (Cloud Deployment)  
- **GitHub Actions** (CI/CD Pipeline)  
- **Machine Learning Libraries**:  
  - **Scikit-Learn** (Linear Regression, Decision Trees, Random Forest, etc.)  
  - **XGBoost & CatBoost** (Boosting Models)  
  - **Pandas, NumPy** (Data Processing)  

---

## 🔮 **Future Enhancements**  
- Deploying as a **serverless API using AWS Lambda**.  
- Adding **monitoring & logging** with AWS CloudWatch.  
- Implementing **feature engineering & hyperparameter tuning**.  

---

## 📜 **License**  
This project is **open-source** under the **MIT License**.  

---

### 🎯 **Final Thoughts**  
This project showcases **ML model training, deployment, and automation with AWS Elastic Beanstalk**. It provides a robust **CI/CD pipeline** via **GitHub Actions** to streamline deployment. 🚀  

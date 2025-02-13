# 🚢 **Titanic Survival Predictor: A Dockerized Streamlit App**

## 📌 **Overview**

Imagine being aboard the Titanic 🛳️—would you have survived? This **machine learning-powered web app** predicts your survival chances based on passenger details! Built with **Python, Streamlit, and scikit-learn**, it provides a sleek UI for real-time predictions. And to make deployment effortless, **Docker** packages everything into a neat container. 🐳🚀

---

## 📂 **Project Structure**

```
Titanic-Prediction-Model/
│── Dockerfile
│── requirements.txt
│── main.py
│── titanic_model.py
│── titanic_model.pkl
```

### **📜 What's Inside?**

-   **`main.py`** → The interactive Streamlit app 🎨
-   **`titanic_model.py`** → Trains and saves the prediction model 🤖
-   **`titanic_model.pkl`** → The trained model file 📂
-   **`requirements.txt`** → Dependencies list 📄
-   **`Dockerfile`** → Configuration for containerization 🐳

---

## 🤖 **Model Training (`titanic_model.py`)**

The **Random Forest Classifier** is trained on Titanic dataset features and saved as `titanic_model.pkl`.

### **🔍 How It Works:**

1️⃣ Load the dataset 📊
2️⃣ Handle missing values & encode categorical data 🧹
3️⃣ Train the **Random Forest Model** 🌲
4️⃣ Save the trained model for later predictions 💾

---

## 🎨 **Streamlit Web App (`main.py`)**

A **user-friendly UI** where you input passenger details and get an instant survival prediction! ✨

### **🚀 Features:**

✔️ **Live predictions** from the trained model 📡
✔️ **Dropdowns & sliders** for easy inputs 🎛️
✔️ **Beautiful visualizations** with Matplotlib & Plotly 📊

---

## 🐳 **Dockerizing the Application**

### **📄 Dockerfile**

```dockerfile
# Use a lightweight Python image
FROM python:3.12-slim

# Set working directory
WORKDIR /app

# Copy dependencies and install them
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application files
COPY main.py main.py
COPY titanic_model.pkl titanic_model.pkl

# Expose the application port
EXPOSE 8501

# Run the Streamlit app
CMD ["streamlit", "run", "main.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

---

## 🚀 **How to Run the App in Docker**

### **1️⃣ Navigate to the Project Folder**

```bash
cd Titanic-Prediction-Model
```

### **2️⃣ Build the Docker Image**

```bash
docker build -t titanic-prediction .
```

### **3️⃣ Run the Docker Container**

```bash
docker run -p 8501:8501 titanic-prediction
```

### **4️⃣ Open the App in Your Browser**

```
http://localhost:8501
```

---

## 🎯 **Wrapping Up**

✅ **Machine Learning Model** predicts Titanic survival
✅ **Streamlit UI** provides an interactive experience
✅ **Docker** makes deployment seamless

### 🔥 **Next Steps:**

-   🚀 **Deploy to AWS, GCP, or Vercel**
-   🎨 **Enhance UI with more interactivity**
-   🏆 **Improve model accuracy with more data features**

⚡ **Set sail on this ML adventure!** 🛳️🐳

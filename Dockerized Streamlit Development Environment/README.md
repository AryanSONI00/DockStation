# 🐳 Dockerized Streamlit Development Environment

## 🚀 Prerequisites

Before diving into the setup, make sure your system is ready with the following tools:

✅ **Docker** 🐳 – Ensure the Docker daemon is running.
✅ **Python 3.9+** 🐍 – Check installation with `python --version`.
✅ **pip** 📦 – Keep it updated using `pip --version`.
✅ **Basic Streamlit Knowledge** 📊 – A quick refresher always helps!

---

## 📂 Project Directory Structure

Your project should be organized as follows:

```
project_root/
│── .streamlit/
│   └── config.toml   # Streamlit configuration file
│── src/
│   └── main.py       # Core application logic
│── Dockerfile        # Container setup
│── requirements.txt  # Dependencies
│── README.md         # Documentation
```

---

## 📜 File Breakdown & Purpose

### 🛠 1. Streamlit Configuration (`.streamlit/config.toml`)

Streamlit settings optimized for development:

```toml
[server]
headless = true
runOnSave = true
fileWatcherType = "poll"
```

### 🏗 2. Streamlit App Logic (`src/main.py`)

This script powers your application:

-   🏠 **Home Page** – A simple app introduction.
-   📊 **Data Explorer** – Upload & inspect CSV files.
-   📈 **Visualization Page** – Generate interactive graphs.

### 🏗 3. Dockerfile – Container Blueprint 🐳

Defines how the app runs inside Docker:

```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt
COPY . /app/
EXPOSE 8501
CMD ["streamlit", "run", "src/main.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

### 📦 4. Dependencies (`requirements.txt`)

Essential libraries:

```
streamlit
pandas
numpy
matplotlib
plotly
```

---

## ⚡ Running the Application

🚀 **Step 1:** Navigate to the project directory:

```sh
cd path/to/project_root
```

🐳 **Step 2:** Build the Docker image:

```sh
docker build -t streamlit-app .
```

▶️ **Step 3:** Run the container:

```sh
docker run -p 8501:8501 streamlit-app
```

🌍 **Step 4:** Open your browser and visit:
[http://localhost:8501](http://localhost:8501) 🎉

---

## 🎯 Conclusion

Congratulations! 🎊 You now have a **fully containerized Streamlit application** running inside Docker. Happy coding! 🚀

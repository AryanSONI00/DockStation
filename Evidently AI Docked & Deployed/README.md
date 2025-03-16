# 🚢 Setting Sail with Evidently AI & Docker: A Data Voyage 🌊📊

## 🔖 All Aboard! (Introduction)

Welcome aboard, data explorers! This guide charts a course for deploying an `Evidently AI`-powered `Streamlit` dashboard inside a `Docker` container. Our mission? To monitor machine learning models effortlessly while keeping everything shipshape.

### 🔢 What’s in the Treasure Chest?

-   🔍 **Evidently AI** for real-time ML monitoring.
-   🔦 **Streamlit** for an interactive dashboard experience.
-   ⚙️ **Docker** to package and deploy your project with ease.
-   📂 **Neatly organized reports & projects.**

---

## 🛀 Charting the Course (Project Structure)

Here’s how your project directory should be organized before setting sail:

```
📂 evidently-ai-streamlit
 ├── 📂 projects                # Different ML monitoring projects
 │    ├── 📂 project_1
 │    │    ├── 📂 reports       # Stores monitoring reports
 │    │    ├── ...
 │    ├── 📂 project_2
 │    │    ├── 📂 reports
 │    │    ├── ...
 │    ├── ...
 │
 ├── 📂 src                     # Python scripts for UI and utilities
 │    ├── ui.py                 # UI components
 │    ├── utils.py              # Helper functions
 │    ├── ...
 │
 ├── 📂 static                  # Static assets (CSS, images, etc.)
 │    ├── style.css             # Custom styling
 │    ├── ...
 │
 ├── 📝 app.py                   # The main Streamlit app
 ├── 📝 Dockerfile               # Docker image definition
 ├── 📝 requirements.txt         # Python dependencies
 ├── 📝 README.md                 # Project documentation
```

---

## 🌏 Navigating the Main Deck (app.py Overview)

The `app.py` script serves as the ship’s helm, steering the user experience by:

-   Dynamically loading available projects and reports.
-   Offering selection options for projects, time periods, and reports.
-   Displaying `Evidently AI` reports within `Streamlit`.
-   Managing missing reports smoothly.
-   Utilizing `src/ui.py` for UI and `src/utils.py` for utility functions.

### 💡 Key Functions at the Helm:

-   `display_sidebar_header()`: Renders the branding & navigation sidebar.
-   `select_project()`: Lets users choose a project.
-   `select_period()`: Enables selection of a reporting period.
-   `select_report()`: Fetches and loads available reports.
-   `display_report()`: Showcases the chosen report.

---

## 🛠️ Building the Ship (Dockerfile)

```dockerfile
# Set sail with the official Python base image
FROM python:3.10

# Define the ship’s working directory
WORKDIR /app

# Load essential tools (requirements)
COPY requirements.txt /app/
RUN pip install --no-cache-dir --break-system-packages -r requirements.txt

# Bring all project files aboard
COPY . /app/

# Open port 8501 for dashboard access
EXPOSE 8501

# Launch the Streamlit dashboard upon start
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

---

## 🦄 Assembling the Crew (Python Dependencies)

```txt
category_encoders==2.6.0
evidently==0.2.6
jupyter==1.0.0
jupyter_contrib_nbextensions==0.7.0
matplotlib==3.7.0
numpy==1.24.2
pandas==1.5.3
pyarrow==11.0.0
python-box==5.4.1
requests==2.28.2
streamlit==1.19.0
pyyaml==5.1
scikit-learn==1.2.1
scipy==1.10.1
seaborn==0.12.2
altair==4.0
```

---

## 🎉 Launching the Expedition (Steps to Run)

### 1️⃣ Clone the Repository & Enter the Ship’s Hold

```sh
git clone <repo-link>
cd evidently-ai-streamlit
```

### 2️⃣ Build & Hoist the Docker Containers

```sh
docker build -t evidently-streamlit .
docker run -p 8501:8501 evidently-streamlit
```

### 3️⃣ Navigate to Your Dashboard

Open [http://localhost:8501](http://localhost:8501) in your browser.

---

## 🌟 Anchoring Our Findings (Conclusion)

💯 Successfully deployed an `Evidently AI` dashboard using `Streamlit` inside Docker.
💪 Integrated report selection for multiple projects.
🚀 Leveraged Docker for smooth deployment & scalability.
🔄 Organized the code into modular UI & utility components.

---

## 🌍 Future Voyages (Next Steps)

🔒 Implement authentication for project access.
📊 Introduce report comparisons across different time periods.
🏠 Deploy this fleet to a cloud harbor like AWS or GCP.

🛡️ Stay curious, keep exploring, and happy coding! 🌌

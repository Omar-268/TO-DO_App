# ✅ To-Do App – Full DevOps CI/CD Project

This is a **Flask-based To-Do web application** implemented as a complete DevOps project. It includes CI/CD automation using **Jenkins**, containerization with **Docker**, and remote deployment using **Ansible** to two virtual machines.

---

## 📌 Features
- Web-based To-Do app built with **Python Flask**
- **CI/CD pipeline** with Jenkins
- **Dockerized** application
- Auto-deployment with **Ansible** on two remote VMs
- Docker image hosted on Docker Hub

---

## ⚙️ Tech Stack
| Area           | Technology        |
|----------------|-------------------|
| Backend        | Python (Flask)    |
| CI/CD          | Jenkins           |
| Containerization | Docker          |
| Configuration Management | Ansible |
| Hosting        | Two VMs (via Vagrant or any cloud/local setup)

---

## 🗂 Project Structure
```plaintext
.
├── app.py                 # Flask application logic
├── requirements.txt       # Python dependencies
├── Dockerfile             # Builds the Docker image
├── jenkinsfile            # Jenkins CI/CD pipeline definition
├── ansible/
│   └── playbook.yml       # Ansible playbook to deploy on VMs
├── static/                # Static frontend assets (CSS, JS, etc.)
└── README.md              # Project documentation
```

---

## 🚀 Running the App Locally with Docker
```bash
git clone https://github.com/Omar-268/TO-DO_App.git
cd TO-DO_App
docker build -t to-do-app .
docker run -p 5000:5000 to-do-app
```
The app will be accessible at: [http://localhost:5000](http://localhost:5000)

---

## 🔁 CI/CD Pipeline with Jenkins
The `Jenkinsfile` defines a complete CI/CD pipeline:
1. **Checkout Code** from GitHub
2. **Build Docker Image**
3. **Push Image** to Docker Hub (`omar2682/to-do-app:latest`)
4. **Trigger Ansible Playbook** to deploy the image on two VMs

---

## ⚙️ Ansible Deployment
The playbook installs Docker (if needed), pulls the image from Docker Hub, and runs the container:
```yaml
- name: Deploy Docker Container
  hosts: all
  become: yes
  tasks:
    - name: Install Docker
      ...
    - name: Pull Docker Image
      docker_image:
        name: omar2682/to-do-app
        tag: latest
        source: pull
    - name: Run Docker Container
      docker_container:
        name: weather-app
        image: omar2682/to-do-app:latest
        state: started
        restart_policy: always
        published_ports:
          - "5001:5000"
```

---



# 🚀 MongoDB + Mongo Express Deployment on Kubernetes

This project demonstrates how to deploy a **MongoDB database** and **Mongo Express web UI** inside a **Kubernetes cluster**.  
It’s a simple yet practical example of how real-world web applications manage **internal services, secrets, and external access** using Kubernetes resources.

---

## 📘 Project Overview

The setup consists of two main components:
- **MongoDB Pod** – stores and manages data.
- **Mongo Express Pod** – provides a web-based interface to interact with MongoDB.

The MongoDB service is kept **internal** for security, while Mongo Express is exposed **externally** via a `NodePort` service to allow browser access.

---

## 🏗️ Architecture

```
Browser
   ↓
External Service (NodePort)
   ↓
Mongo Express Pod
   ↓
Internal Service (ClusterIP)
   ↓
MongoDB Pod
```

- **ConfigMap** stores the MongoDB connection URL.  
- **Secret** stores the MongoDB credentials (username & password).  
- **Deployments** define pod configurations for MongoDB and Mongo Express.  
- **Services** control network access within and outside the cluster.

---

## ⚙️ Prerequisites

Make sure you have the following installed:
- [Docker](https://www.docker.com/)
- [Kubernetes (kubectl)](https://kubernetes.io/docs/tasks/tools/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/) or any running cluster

---

## 🚀 Steps to Deploy

1. **Clone the Repository**
   ```bash
   git clone https://github.com/privateyash/Kubernates-Project.git
   cd Kubernates-Project
   ```

2. **Create Secret for MongoDB Credentials**
   ```bash
   kubectl apply -f mongo-secret.yaml
   ```

3. **Create ConfigMap for MongoDB URL**
   ```bash
   kubectl apply -f mongo-configmap.yaml
   ```

4. **Deploy MongoDB Pod and Service**
   ```bash
   kubectl apply -f mongo.yaml
   ```

5. **Deploy Mongo Express Pod and Service**
   ```bash
   kubectl apply -f mongo-express.yaml
   ```

6. **Check All Resources**
   ```bash
   kubectl get all
   ```

7. **Access Mongo Express in Browser**
   ```bash
   minikube service mongo-express-service
   ```
   or visit  
   `http://<node-ip>:<node-port>`

---

## 🧩 Files in the Project

| File | Description |
|------|--------------|
| `mongo-secret.yaml` | Stores MongoDB username & password as Kubernetes Secrets |
| `mongo-configmap.yaml` | Stores the MongoDB connection URL |
| `mongo.yaml` | Deployment and internal service for MongoDB |
| `mongo-express.yaml` | Deployment and external service for Mongo Express |

---

## 🔐 Security Notes
- MongoDB credentials are stored securely using Kubernetes **Secrets**.
- The database is only accessible **within the cluster** (ClusterIP service).
- Only Mongo Express is exposed externally for management.

---

## 📊 Future Enhancements
- Add persistent storage using **PersistentVolumeClaim (PVC)**.
- Implement **Ingress** for controlled HTTP routing.
- Add monitoring using **Prometheus** or **Grafana**.

---

## 📸 Screenshots (Optional)
Add screenshots to show:
- Pods and services running (`kubectl get all`)
- Mongo Express UI in the browser

---

## 🧠 Key Learnings
- Managing environment variables securely using **ConfigMaps** and **Secrets**
- Exposing only necessary services externally
- Understanding how pods communicate within a cluster

---

## 🧾 License
This project is open-source and available under the [MIT License](LICENSE).

---

### 🔗 Connect with Me
If you found this helpful or want to collaborate, feel free to reach out on [LinkedIn](https://www.linkedin.com/in/kumaryash25/) or explore more projects on my GitHub profile!

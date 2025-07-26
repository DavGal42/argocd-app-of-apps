# VoteApp — ArgoCD App of Apps Demo with Kubernetes

This project is a **GitOps-style deployment** of the [Example Voting App](https://github.com/dockersamples/example-voting-app) using **ArgoCD** with the **App of Apps** pattern.

---

<img width="600" height="400" alt="Screenshot from 2025-07-20 12-45-09" src="https://github.com/user-attachments/assets/9c33af38-e0f9-4af7-989a-a5cec53a9318" />
<img width="600" height="400" alt="Screenshot from 2025-07-20 12-45-52" src="https://github.com/user-attachments/assets/4619a983-4a49-4482-8e6a-861162c29ad2" />
<img width="600" height="400" alt="Screenshot from 2025-07-20 12-46-02" src="https://github.com/user-attachments/assets/469269bc-de56-4299-bc82-a24471b56a05" />

## Project Structure

```bash
VoteApp/
├── app-of-apps.yml
├── apps
│   ├── db-app.yml
│   ├── redis-app.yml
│   ├── result-app.yml
│   ├── vote-app.yml
│   └── worker-app.yml
├── db
│   ├── db-deployment.yaml
│   └── db-service.yaml
├── redis
│   ├── redis-deployment.yaml
│   └── redis-service.yaml
├── result
│   ├── result-deployment.yaml
│   └── result-service.yaml
├── vote
│   ├── vote-deployment.yaml
│   └── vote-service.yaml
└── worker
│   └── worker-deployment.yaml
└── README.md
```

---

## Components

| Component | Description                       | Language    |
|-----------|-----------------------------------|-------------|
| `vote`    | Frontend voting app (web UI)      | Flask (Python) |
| `result`  | Results display app               | Node.js     |
| `worker`  | Background processor              | Python      |
| `redis`   | Queue backend                     | Redis       |
| `db`      | Database backend                  | PostgreSQL  |

---

## Deployment Guide
### 1. Install ArgoCD

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### 2. Create App of Apps

```bash
kubectl create -f app-of-apps.yml -n argocd
```

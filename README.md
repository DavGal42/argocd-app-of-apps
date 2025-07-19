# <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Telegram-Animated-Emojis/main/Objects/Ballot%20Box%20With%20Ballot.webp" alt="Ballot Box With Ballot" width="50" height="50" /> VoteApp — ArgoCD App of Apps Demo with Kubernetes

This project is a **GitOps-style deployment** of the [Example Voting App](https://github.com/dockersamples/example-voting-app) using **ArgoCD** with the **App of Apps** pattern.

---

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Telegram-Animated-Emojis/main/Objects/Card%20Index%20Dividers.webp" alt="Card Index Dividers" width="30" height="30" /> Project Structure

```
VoteApp/
├── app-of-apps.yml
├── apps
│   ├── db
│   │   ├── app.yml
│   │   ├── db-deployment.yaml
│   │   ├── db-service.yaml
│   │   └── namespace.yml
│   ├── redis
│   │   ├── app.yml
│   │   ├── namespace.yml
│   │   ├── redis-deployment.yaml
│   │   └── redis-service.yaml
│   ├── result
│   │   ├── app.yml
│   │   ├── namespace.yml
│   │   ├── result-deployment.yaml
│   │   └── result-service.yaml
│   ├── vote
│   │   ├── app.yml
│   │   ├── namespace.yml
│   │   ├── vote-deployment.yaml
│   │   └── vote-service.yaml
│   └── worker
│       ├── app.yml
│       ├── namespace.yml
│       └── worker-deployment.yaml
└── README.md
```

---

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Telegram-Animated-Emojis/main/Objects/Toolbox.webp" alt="Toolbox" width="30" height="30" /> Components

| Component | Description                       | Language    |
|-----------|-----------------------------------|-------------|
| `vote`    | Frontend voting app (web UI)      | Flask (Python) |
| `result`  | Results display app               | Node.js     |
| `worker`  | Background processor              | Python      |
| `redis`   | Queue backend                     | Redis       |
| `db`      | Database backend                  | PostgreSQL  |

---

## <img src="https://raw.githubusercontent.com/Tarikul-Islam-Anik/Telegram-Animated-Emojis/main/Travel%20and%20Places/Rocket.webp" alt="Rocket" width="30" height="30" /> Deployment Guide
### 1. Install ArgoCD

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### 2. Create App of Apps

```
kubectl create -f app-of-apps.yml -n argocd
```

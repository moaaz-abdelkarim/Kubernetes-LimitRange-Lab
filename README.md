# 🚀 Kubernetes LimitRange Lab

A simple hands-on project showing how to manage resources in Kubernetes using LimitRange.

Learn how to control CPU & memory usage, set default limits, and keep your cluster stable.

# 📋 Project Overview

This project demonstrates:

How to set default CPU and memory limits for containers

How LimitRange automatically applies defaults to pods and jobs

How to prevent resource overuse and ensure balanced cluster performance

## Use this project to understand:
⚙️ Resource management best practices

📊 Kubernetes namespaces and resource governance

🔒 How to apply automatic resource control in real deployments

# 🛠️ Tech Stack
| Tool              | Purpose                      |
| ----------------- | ---------------------------- |
| 🧩 **Kubernetes** | Container orchestration      |
| 🌐 **NGINX**      | Demo web container           |
| 📦 **BusyBox**    | Lightweight CronJob task     |
| 🧾 **YAML**       | Resource configuration files |

# 🏗️ Architecture

```
graph TB
  subgraph "Kubernetes Cluster"
    subgraph "limitrange-lab Namespace"
      LR[LimitRange: resource-limits]

      subgraph "Resource Constraints"
        DEF[Default: 500m CPU / 512Mi RAM]
        REQ[Request: 200m CPU / 256Mi RAM]
        MAX[Max: 1 CPU / 1Gi RAM]
        MIN[Min: 100m CPU / 128Mi RAM]
      end

      POD[Pod: nginx-test]
      CRON[CronJob: log-task]

      LR --> DEF
      LR --> REQ
      LR --> MAX
      LR --> MIN

      DEF -.applies to.-> POD
      DEF -.applies to.-> CRON
    end
  end

  style LR fill:#326ce5,stroke:#fff,stroke-width:2px,color:#fff
  style POD fill:#009639,stroke:#fff,stroke-width:2px,color:#fff
  style CRON fill:#ff6b6b,stroke:#fff,stroke-width:2px,color:#fff
 
```
# ⚡ How to Run


## 1. Clone this repo
```
git clone https://github.com/moaaz-abdelkarim/kubernetes-limitrange-lab.git

cd kubernetes-limitrange-lab
```
## 2. Create a namespace
```
kubectl create namespace limitrange-lab
```
## 3. Apply configurations
```
kubectl apply -f limitrange.yaml
kubectl apply -f nginx-pod.yaml
kubectl apply -f log-cronjob.yaml
```
## 4. Verify results
```
kubectl get all -n limitrange-lab
kubectl describe limitrange -n limitrange-lab
```

# 🧪 Test It
- Try creating a Pod that exceeds the limits — it will fail automatically! 💥

- That’s how LimitRange keeps your cluster safe and efficient.

# 💡 Future Ideas

Add ResourceQuota for namespace limits

Integrate Prometheus + Grafana for monitoring

Build a Helm chart for easier deployment

# 💬 Connect

- GitHub: [@moaaz-abdelkarim](https://github.com/moaaz-abdelakrim)
- LinkedIn: [Moaaz Farrag](https://linkedin.com/in/moaazfarrag)
- Email: moaazfarra0@gmail.com

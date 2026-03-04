# 📊 Observability Pipeline (ELK Stack)
Visibility is the first line of defense. The Elasticsearch, Filebeat, and Kibana stack provides a "God-view" of the cluster.

Log Enrichment: Used the add_kubernetes_metadata processor in Filebeat to tag every log with its pod name, namespace, and node.

WSL2 Optimization: Custom DaemonSet configuration to handle symlinked log paths in the Windows Subsystem for Linux environment.

Security Dashboards: Real-time Kibana visualizations that distinguish between valid transaction volume and "Dropped" packets from unauthorized sources.

# 🚀 Deployment
Prerequisites
Kind (Kubernetes in Docker)

Helm (for Vault and cert-manager installation).

Installation
Provision Cluster: kind create cluster --config=kind-config.yaml

Deploy Networking: kubectl apply -f https://docs.tigera.io/calico/charts

Initialize Security:

Bash
helm install vault hashicorp/vault --set "server.dev.enabled=true"
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.13.0/cert-manager.yaml
Apply Manifests: kubectl apply -f k8s-core/ && kubectl apply -f observability/

# 🎓 SRE  Highlights


Infrastructure as Code (IaC): Every security rule and observability component is version-controlled.

Secret Management: Moving from "Base64 secrets" to HashiCorp Vault for enterprise compliance.

Incident Response: Using the ELK Stack to detect lateral movement attempts within 60 seconds.

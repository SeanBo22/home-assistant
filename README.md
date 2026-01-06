# Home Assistant on Kubernetes (MicroK8s)

This repository contains my personal Home Assistant setup running on **Kubernetes (MicroK8s)**, along with supporting services and tooling. The goal of this repo is to keep my smart home infrastructure **reproducible, modular, and GitHub-safe**.

---

## 📁 Repository Structure

```
.
├── govee/              # Govee → MQTT integration (govee2mqtt)
├── mqtt/               # MQTT broker deployment (Mosquitto) on Kubernetes
├── home-assistant/     # Home Assistant deployment on Kubernetes
├── image-builder/
│   └── ha/             # Custom Home Assistant image builder
└── README.md
```

---

## 🧩 Components

### 🔌 `govee/`
Kubernetes manifests for running **govee2mqtt**, which bridges Govee devices into MQTT for use in Home Assistant.

- Runs as a container in Kubernetes
- Uses environment variables for configuration
- MQTT connection details are injected at runtime (no hard-coded IPs)

> 📌 This integration is based on **govee2mqtt** by wez
>
> Source: https://github.com/wez/govee2mqtt/tree/main

---

### 📡 `mqtt/`
Deployment manifests for an **MQTT broker (Mosquitto)** running inside the cluster.

- Exposed via a Kubernetes Service
- Used by Home Assistant and other integrations
- Configuration kept separate from application deployments

---

### 🏠 `home-assistant/`
Manifests and configuration related to deploying **Home Assistant** on Kubernetes.

- Designed for MicroK8s
- Uses ConfigMaps and Secrets for configuration
- UI-managed dashboards (not YAML-only)
- Supports ingress and TLS (cluster-dependent)

---

### 🛠️ `image-builder/ha/`
Custom Home Assistant image builder.

Used to:
- Add additional system packages
- Include custom dependencies
- Maintain a consistent HA runtime environment

Images built here are intended to be used by the Kubernetes deployment under `home-assistant/`.

---

## 🔐 Secrets & Configuration

This repository intentionally **does not commit**:
- IP addresses
- Domain names
- Tokens or credentials

Instead, configuration is handled via:
- Kubernetes **Secrets**
- Kubernetes **ConfigMaps**
- Environment variables injected at deploy time

Example values and placeholders may be provided, but real values live only in the cluster.

---

## 🚀 Deployment Notes

- Target platform: **MicroK8s**
- Kubernetes-native patterns are preferred
- Services communicate via cluster networking
- IP-based configuration is injected only where strictly required

This repo is not intended to be a one-click install, but rather a **referenceable, auditable home infrastructure**.

---

## 📌 Disclaimer

This is a personal home automation setup and may evolve frequently. Use at your own risk, and adapt configurations to your own environment.

---

## 📄 License

This repository is provided as-is for learning and reference purposes. Third-party components retain their original licenses.



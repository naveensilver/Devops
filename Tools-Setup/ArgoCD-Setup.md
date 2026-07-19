# Prerequisites

Before installing Argo CD, ensure the following are installed and configured.

## 1. Install Docker Desktop

Download and install Docker Desktop for macOS:

https://www.docker.com/products/docker-desktop/

Verify Docker is running:

```bash
docker version
docker info
```

---

## 2. Enable Kubernetes in Docker Desktop

1. Open **Docker Desktop**.
2. Go to **Settings** (or **Preferences** on macOS).
3. Select **Kubernetes**.
4. Check **Enable Kubernetes**.
5. Click **Apply & Restart**.
6. Wait until Kubernetes shows **Running**.

Verify:

```bash
kubectl cluster-info
```

Expected output:

```text
Kubernetes control plane is running at https://...
CoreDNS is running at https://...
```

Check the nodes:

```bash
kubectl get nodes
```

Expected output:

```text
NAME             STATUS   ROLES           AGE   VERSION
docker-desktop   Ready    control-plane   ...   ...
```

---

## 3. Install kubectl

Docker Desktop usually installs `kubectl`. If it is not available:

```bash
brew install kubectl
```

Verify:

```bash
kubectl version --client
```

---

## 4. Install Helm

```bash
brew install helm
```

Verify:

```bash
helm version
```

---

## 5. Verify the Kubernetes Context

Ensure `kubectl` is connected to Docker Desktop's Kubernetes cluster:

```bash
kubectl config current-context
```

Expected output:

```text
docker-desktop
```

If it is not `docker-desktop`, switch to it:

```bash
kubectl config use-context docker-desktop
```

Verify again:

```bash
kubectl get nodes
```

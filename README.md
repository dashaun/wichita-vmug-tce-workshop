# Wichita VMUG - Tanzu Community Edition Workshop - March 2022

## Launch Slides

1. Clone the repository
    ```shell
    git@github.com:dashaun/wichita-vmug-tce-workshop.git
    ```
2. CD into the repository
    ```shell
    cd wichita-vmug-tce-workshop
    ```
3. Install [vendir](https://carvel.dev/vendir/docs/v0.24.0/install)
4. Download reveal.js
   Setup:
    ```shell
    vendir sync
    ```
5. Use docker to serve the content
    ```shell
    docker run --name workshop --rm -v $PWD/:/usr/share/nginx/html:ro -d -p 8088:80 nginx
    ``` 
6. Open browser to http://localhost:8088/

## Agenda

- PhotonOS VM ready for Tanzu CLI & kubectl
- Introduction
- Containers 101
- Kubernetes 101
- Tanzu 101
- Create Cluster
- Install Packages
    - Prometheus
    - Grafana
    - Knative Serving (Runtime)
    - kpack
    - Spring Workload
        - Buildpacks
    - Harbor
- Delete
- Custom Install

Why kubernetes?
Buildpacks!
Exposing containers to the outside world, load-balancing and ingress/egress

- Make this workshop, something the audience can take back to their orgs and deliver.
- I do, we do, you do.
    - I'll come deliver this workshop with you, to your org

Cloud -> back home -> Tanzu makes it easy to go both ways

Make sure to share links for version 0.11 details and announcements

TCE office hours - announcements

Share slides, github repo, docs, etc....






mkdir /tanzu
sudo chown dashaun: /tanzu
```





## Install Unmanaged Cluster
```bash
tanzu uc create tce-local -c calico -p 80:80 -p 443:443
```
> ```bash
> ...
> ✅ Cluster created
> 
> 🎮 kubectl context set to tce-local
> 
> View available packages:
> tanzu package available list
> View running pods:
> kubectl get po -A
> Delete this cluster:
> tanzu unmanaged delete tce-local
> ```

## Kubectl

```bash

kubectl get node
```

## kubecolor

```bash
wget https://github.com/hidetatz/kubecolor/releases/download/v0.0.20/kubecolor_0.0.20_Linux_x86_64.tar.gz
tar -xvzf kubecolor_0.0.20_Linux_x86_64.tar.gz
sudo install -o root -g root -m 0755 kubecolor /usr/local/bin/kubecolor
alias kubectl="kubecolor"
kubectl get node
```

## tanzu package repository

```bash
# List installed repositories
tanzu package repository list -A
# List all available packages from installed repositories
tanzu package available list -A
# Upgrade repository to newer version
tanzu package repository update tkg-core-repository --url projects.registry.vmware.com/tce/main:v0.10.3 -n tanzu-package-repo-global
```

## Cert-Manager

```bash
# list available versions
tanzu package available list cert-manager.community.tanzu.vmware.com -n default
# Get configuration options for 1.6.1
tanzu package available get cert-manager.community.tanzu.vmware.com/1.6.1 -n default --values-schema
# Install
tanzu package install cert-manager --package-name cert-manager.community.tanzu.vmware.com --version 1.6.1
# Check status
tanzu package installed list
# Delete
tanzu package installed delete cert-manager
```

## What about helm?

- As a platform engineer, I want to give my developers a consistent, supported platform
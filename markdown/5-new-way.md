## tanzu package repository

```bash
# List installed repositories
tanzu package repository list -A
# List all available packages from installed repositories
tanzu package available list -A
# Upgrade repository to newer version
tanzu package repository update tkg-core-repository --url projects.registry.vmware.com/tce/main:v0.10.3 -n tanzu-package-repo-global
```

---

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

---

## What about helm?

- As a platform engineer, I want to give my developers a consistent, supported platform

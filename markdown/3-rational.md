## Tanzu CLI

Install Tanzu Community Edition CLI vs [hard way](https://github.com/kelseyhightower/kubernetes-the-hard-way)

```bash
sudo mkdir /tanzu
sudo chown dashaun: /tanzu
cd /tanzu
wget https://github.com/vmware-tanzu/community-edition/releases/download/v0.10.0/tce-linux-amd64-v0.10.0.tar.gz
tar -xvzf tce-linux-amd64-v0.10.0.tar.gz
cd tce-linux-amd64-v0.10.0
./install.sh
# Validate Version
tanzu version
# bash auto completion
source <(tanzu completion bash)
```
> ```
> version: v0.10.1
> buildDate: 2022-02-14
> sha: 401d55b
> ```

---

## Install kubectl

```bash
cd /tanzu
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
source <(kubectl completion bash)
```
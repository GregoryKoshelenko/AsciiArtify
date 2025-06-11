# This is a guide how to install and use kubeplugin for local Kubernetes clusters.

### Make plugin executable:
```bash
chmod +x kubeplugin
```
#### Install kubeplugin:
```bash
sudo cp ./kubeplugin /usr/local/bin/kubectl-usage
```

#### Verify installation:
```bash
kubectl usage --help
```
#### Usage:
```bash
kubectl usage [namespace] [resource types]
```

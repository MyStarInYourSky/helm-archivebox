## helm-archivebox

This is an alternate deployment system for those wanting to deploy helm using gunicorn instead of the developmental WSGI server.

Features:
- Automatic creation of initial SuperUser
- Secure setup with no root in any container and read-only root filesystem
- Seperated static file serving using NGINX

### Adding the repo
The helm repo can be added by running
```
helm repo add iloveyatoo https://helm.catsdo.delivery/
```

### Values
| Value  	| Description  	| Defaults  	|
|---	    |---	|---	|
| imagePullSecrets | Name of the Kubernetes Secret containing Docker Pull Secrets | `[]` |
| podAnnotations | Additional annotations to be added to the pod | `[]` |
| nodeSelector | Sets the NodeSelector to constrain the pod to certain nodes | `{}` |
| tolerations | | `[]` |
| affinity | | `{}` |
| podSecurityContext.fsGroup | Permissions for volumes mounted in the pod | `1000` |
| archivebox.superUser.userName | Sets the username for the superuser of archivebox | `myuser` |
| archivebox.superUser.userEmail | Sets the user email for the superuser of archivebox | `myuser@test.com` |
| archivebox.superUser.userPassword | Sets the user password for the superuser of archivebox | `mypass` |
| archivebox.storage.archive.storageClassName | Sets the storageClass for archivebox storage | `default` |
| archivebox.storage.archive.size | | `20G` |
| archivebox.storage.temp.storageClassName | | `default` |
| archivebox.storage.temp.size | | `5G` |
| archivebox.resources.limits.cpu | | `200m` |
| archivebox.resources.limits.memory | | `512Mi` |
| archivebox.resources.requests.cpu | | `100m` |
| archivebox.resources.requests.memory | | `512Mi` |
| archivebox.image.repository | | `ghcr.io/iloveyatoo/archivebox` |
| archivebox.image.pullPolicy | | `Always` |
| archivebox.image.tag | | `""` |
| archivebox.securityContext | | `{capabilities: {drop: [ALL]}, readOnlyRootFilesystem: true, runAsGroup: 1000, runAsUser: 1000}` |


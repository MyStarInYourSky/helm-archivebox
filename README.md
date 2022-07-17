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
| tolerations | Schedule pods on nodes with matching taints | `[]` |
| affinity | Constrain Pods against labels on other Pods | `{}` |
| podSecurityContext | Permissions for volumes mounted in the pod | `{fsGroup: 1000}` |
| archivebox.superUser.userName | Sets the username for the superuser of archivebox | `myuser` |
| archivebox.superUser.userEmail | Sets the user email for the superuser of archivebox | `myuser@test.com` |
| archivebox.superUser.userPassword | Sets the user password for the superuser of archivebox | `mypass` |
| archivebox.storage.archive.storageClassName | Sets the storageClass for archivebox storage | `default` |
| archivebox.storage.archive.size | Sets the storage size for archivebox storage | `20G` |
| archivebox.storage.temp.storageClassName | Sets the storageClass for temporary storage for archivebox | `default` |
| archivebox.storage.temp.size | Sets the storage size for temporary storage for archivebox | `5G` |
| archivebox.resources.limits.cpu | Sets the CPU limits for archivebox | `200m` |
| archivebox.resources.limits.memory | Sets the Memory limits for archivebox | `512Mi` |
| archivebox.resources.requests.cpu | Sets the CPU requests for archivebox | `100m` |
| archivebox.resources.requests.memory | Sets the Memory requests for archivebox | `512Mi` |
| archivebox.image.repository | Sets the image repository for the archivebox docker image | `ghcr.io/iloveyatoo/archivebox` |
| archivebox.image.pullPolicy | Sets the pullPolicy for the archivebox docker image | `Always` |
| archivebox.image.tag | Overrides the docker tag for archivebox | `""` |
| archivebox.securityContext | Sets the securityContext for the container | `{capabilities: {drop: [ALL]}, readOnlyRootFilesystem: true, runAsGroup: 1000, runAsUser: 1000}` |
| nginx.storage.nginx.storageClassName | Sets the storage class for nginx static file storage | `default` |
| nginx.storage.nginx.size | Sets the storage size for nginx static file storage | `1G` |
| nginx.storage.nginx.resources.limits.cpu | Sets the CPU limits for nginx | `100m` |
| nginx.storage.nginx.resources.limits.memory | Sets the Memory limits for nginx | `128Mi` |
| nginx.resources.requests.cpu | Sets the CPU requests for nginx | `100m` |
| nginx.resources.requests.memory | Sets the Memory requests for nginx | `128Mi` |
| nginx.image.repository | Sets the image repository for the nginx docker image | `nginxinc/nginx-unprivileged` |
| nginx.image.pullPolicy | Sets the pullPolicy for the nginx docker image | `Always` |
| nginx.image.tag | Overrides the docker tag for nginx | `""` |
| nginx.securityContext | Sets the securityContext for the container | `{capabilities: {drop: [ALL]}, runAsUser: 101, runAsGroup: 101, readOnlyRootFilesystem: true}` |
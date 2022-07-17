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
| nameOverride |   	|   	|
| fullnameOverride |   	|   	|
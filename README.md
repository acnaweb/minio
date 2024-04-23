# MinIO

The Object Store for AI Data Infrastructure

## Install and Setup

### Helm

#### Add repo

```sh
helm repo add minio-operator https://operator.min.io
helm repo update
helm search repo minio-operator
```

#### Setup Environment

```sh
export ENVIRONMENT=object-store
export MINIO_RELEASE=minio
```

#### Install

```sh
helm install $MINIO_RELEASE minio-operator/minio-operator --namespace $ENVIRONMENT --create-namespace --version 4.3.7
```

#### Navigate

```sh
kubectl get secret $(kubectl get serviceaccount console-sa --namespace $ENVIRONMENT  -o jsonpath="{.secrets[0].name}") --namespace $ENVIRONMENT  -o jsonpath="{.data.token}" | base64 --decode
kubectl --namespace $ENVIRONMENT port-forward svc/console 9090:9090
```

> - http://localhost:9090

#### Uninstall

```sh
helm uninstall $MINIO_RELEASE --namespace $ENVIRONMENT
```

### Docker

#### Install

```sh
# clone MinIO from GitHub
git clone https://github.com/acnaweb/minio.git

# switch into MinIO directory
cd minio

# start MinIO
docker compose up
```

#### Navigate

> - [http://localhost:8000](http://localhost:9001/)
> - username: admin
> - password: password

#### API

http://localhost:9000/

## References

- https://min.io/
- https://min.io/docs/minio/kubernetes/upstream/operations/install-deploy-manage/deploy-operator-helm.html





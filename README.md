#### Create k8s `awsecrcred` secret, needed for fetching images from private ecr

> namespace has to be created before executing

```shell
kubectl create secret docker-registry awsecrcred \
  --docker-server=${AWS_ACCOUNT}.dkr.ecr.eu-central-1.amazonaws.com \
  --docker-username=AWS \
  --docker-password=$(aws ecr get-login-password --region eu-central-1) \
  --namespace=magicskunk
```

#### Services notes

- purpose of a service is to provide single point of reference to a group of pods (replicas)
- to create service of type LoadBalancer in minicube and get external ip assigned, following does
  the magic

```shell
minikube tunnel
```

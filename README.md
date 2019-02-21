# Sample Knative Build Pipeline

## Add helm repo
```
helm repo add jenkins-x https://storage.googleapis.com/chartmuseum.jenkins-x.io
```
## Install Knative Build Pipline

Using your Git and Dockerhub credentials
```
helm upgrade --install --set auth.docker.username=fred --set auth.docker.password=flintstone --set auth.docker.url=https://index.docker.io/v1/ --set auth.git.username=test-bot-user --set auth.git.password=abcdef12345 --set auth.git.url=https://github.com knative-build-pipeline jenkins-x/knative-build-pipeline
```

## Clone repo
```
git clone https://github.com/rawlingsj/knative-build-pipeline-sample-yaml.git && cd knative-build-pipeline-sample-yaml
```
## Replace `rawlingsj` with your dockerhub username
[./yaml/1-image-pipeline-resource.yaml#L9](yaml/1-image-pipeline-resource.yaml#L9)

## Apply sample yaml
```
kubectl apply -f yaml/
```

## Check status of build
```
kubectl get pods -w
```

## Check dockerhub for the new image

https://hub.docker.com/r/[YOUR_DOCKERHUB_USERNAME]

## If no build pod starts

```
kubectl get pipelineruns/tutorial-pipeline-run -o yaml
```

--------------------------

## Delete sample yaml
```
kubectl delete -f yaml/
```
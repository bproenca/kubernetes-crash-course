# Hello World Rest API

### Build and Publish image

```console
mvn clean package
docker push bproenca/hello-world-rest-api:0.0.5-SNAPSHOT
```

### Deploy GCP
```console
gcloud auth login
gcloud container clusters resize --zone us-central1-a cluster-bcp --num-nodes=3

kubectl apply -f deployment.yaml
```

### Accessing the Application

- http://\<load-balancer-ip\>:8080/hello-world

```txt
Hello World V5 abcde

watch -n 0.1 curl http://35.193.33.62:8080/hello-world
```

### Undeploy GCP
```console
kubectl delete all -l app=hello-world-rest-api
gcloud container clusters resize --zone us-central1-a cluster-bcp --num-nodes=0
```

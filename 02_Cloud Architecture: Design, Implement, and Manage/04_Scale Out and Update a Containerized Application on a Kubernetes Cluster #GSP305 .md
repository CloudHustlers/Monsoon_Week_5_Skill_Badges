# GSP305
>🚨 [PLEASE SUBSCRIBE OUR CHANNEL CLOUDHUSTLER](https://www.youtube.com/@cloudhustlers) **&** [JOIN OUR COMMUNITY](https://chat.whatsapp.com/KBfUcSleGGEFf2Xvvm8FW3)
## Run in Cloudshell
```cmd
export ZONE=
```
```cmd
gsutil cp gs://$DEVSHELL_PROJECT_ID/echo-web-v2.tar.gz .
tar -xvf echo-web-v2.tar.gz
gcloud builds submit --tag gcr.io/$DEVSHELL_PROJECT_ID/echo-app:v2 .
gcloud container clusters get-credentials echo-cluster --zone=$ZONE
kubectl create deployment echo-web --image=gcr.io/qwiklabs-resources/echo-app:v2
kubectl expose deployment echo-web --type=LoadBalancer --port 80 --target-port 8000
kubectl scale deploy echo-web --replicas=2
kubectl port-forward service/echo-web 8080:80
```

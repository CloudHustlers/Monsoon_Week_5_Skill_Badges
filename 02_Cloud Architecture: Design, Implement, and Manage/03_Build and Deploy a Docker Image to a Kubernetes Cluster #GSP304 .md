# GSP304
>🚨 [PLEASE SUBSCRIBE OUR CHANNEL CLOUDHUSTLER](https://www.youtube.com/@cloudhustlers) **&** [JOIN OUR COMMUNITY](https://chat.whatsapp.com/KBfUcSleGGEFf2Xvvm8FW3)
## Run in Cloudshell
```cmd
export ZONE=
```
```cmd
export PROJECT_ID=$(gcloud config get-value project)
gsutil cp gs://$DEVSHELL_PROJECT_ID/echo-web.tar.gz .
tar -xvf echo-web.tar.gz
cd echo-web
gcloud builds submit --tag gcr.io/$PROJECT_ID/echo-app:v1 .
gcloud container clusters create echo-cluster --num-nodes 2 --machine-type e2-standard-2 --zone $ZONE
kubectl create deployment echo-web --image=gcr.io/$PROJECT_ID/echo-app:v1
kubectl expose deployment echo-web --type=LoadBalancer --port=80 --target-port=8000
```

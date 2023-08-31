# ARC120
>🚨 [PLEASE SUBSCRIBE OUR CHANNEL CLOUDHUSTLER](https://www.youtube.com/@cloudhustlers) **&** [JOIN OUR COMMUNITY](https://chat.whatsapp.com/KBfUcSleGGEFf2Xvvm8FW3)
### Navigation Menu > Cloud Storage > Create Bucket > Name (`Copy from Task 1`) > Create
## Run in cloudshell 
```cmd
export ZONE=
```
```cmd
gcloud compute instances create my-instance \
    --machine-type=e2-medium \
    --zone=$ZONE \
    --image-project=debian-cloud \
    --image-family=debian-11 \
    --boot-disk-size=10GB \
    --boot-disk-type=pd-balanced \
    --create-disk=size=100GB,type=pd-standard,mode=rw,device-name=additional-disk \
    --tags=http-server
gcloud compute disks create mydisk \
    --size=200GB \
    --zone=$ZONE
gcloud compute instances attach-disk my-instance \
    --disk=mydisk \
    --zone=$ZONE
gcloud compute ssh my-instance --zone=$ZONE --quiet
```
```cmd
sudo apt update
sudo apt install nginx -y
sudo systemctl start nginx
```

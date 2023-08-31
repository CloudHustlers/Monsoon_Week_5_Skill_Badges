# GSP004
>🚨 [PLEASE SUBSCRIBE OUR CHANNEL CLOUDHUSTLER](https://www.youtube.com/@cloudhustlers) **&** [JOIN OUR COMMUNITY](https://chat.whatsapp.com/KBfUcSleGGEFf2Xvvm8FW3)
## Run in cloudshell 
```cmd
export ZONE=
```
```cmd
export REGION=${ZONE%-*}
gcloud compute instances create gcelab --zone $ZONE --machine-type e2-standard-2
gcloud compute disks create mydisk --size=200GB \
--zone $ZONE
gcloud compute instances attach-disk gcelab --disk mydisk --zone $ZONE
gcloud compute ssh gcelab --zone $ZONE --quiet
```
```cmd
sudo mkdir /mnt/mydisk
sudo mkfs.ext4 -F -E lazy_itable_init=0,lazy_journal_init=0,discard /dev/disk/by-id/scsi-0Google_PersistentDisk_persistent-disk-1
sudo mount -o discard,defaults /dev/disk/by-id/scsi-0Google_PersistentDisk_persistent-disk-1 /mnt/mydisk
echo '/dev/disk/by-id/scsi-0Google_PersistentDisk_persistent-disk-1 /mnt/mydisk ext4 defaults 1 1' | sudo tee -a /etc/fstab
```

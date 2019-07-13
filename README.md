# recipe-app-api
Create an advanced REST API with Python, Django REST Framework and Docker using Test Driven Development (TDD)

# Prepare setup
```buildoutcfg

## create ubuntu bionic in Google Cloud
GCP_PROJECT="YOUR_GCP_PROJECT_NAME_HERE"
gcloud compute instances create proj-machine \
--project=GCP_PROJECT \
--zone=europe-west2-c \
--machine-type=g1-small \
--tags=http-server,https-server \
--image=ubuntu-1804-bionic-v20190628 \
--image-project=ubuntu-os-cloud 

# SSH into GCP machine and follow steps below
# clone repo
git clone https://github.com/andreistefanciprian/recipe-app-api.git
cd recipe-app-api/

# install docker
sudo apt-get install docker.io -y

# use Docker as a non-root user. Log out and back in for this to take effect!
sudo usermod -aG docker $(whoami)

# create docker base container
docker build .

# create docker app container
docker-compose build

# create django app in docker container
docker-compose run app sh -c "django-admin.py startproject app ."

```
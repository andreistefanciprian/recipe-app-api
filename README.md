# recipe-app-api
Create an advanced REST API with Python, Django REST Framework and Docker using Test Driven Development (TDD)

# Prepare setup
```buildoutcfg
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
# Build and start the app
docker-compose up
# Create migrations
docker-compose run app sh -c "python manage.py makemigrations core"
# Create superuser
docker-compose run app sh -c "python manage.py createsuperuser"
# Run unit and linting tests
docker-compose run app sh -c "python manage.py test && flake8"

```

# Django commands ...
```buildoutcfg
# create django app in docker container
docker-compose run app sh -c "django-admin.py startproject app ."
# Create core app
docker-compose run app sh -c "python manage.py startapp core"
# Create user app
docker-compose run --rm app sh -c "python manage.py startapp user"
# Create recipe app
docker-compose run --rm app sh -c "python manage.py startapp recipe"
```


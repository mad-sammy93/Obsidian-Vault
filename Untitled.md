# Local Dev Setup

  

# change branch

```git checkout vbr-live```

  

## Requirements

- Docker

- Docker-compose

  

## Prepare

  

### Import database

  

1. Run command (and leave open)

```docker-compose up db_vbr```

  

2. Check ID of mysql container

```docker ps```

  

3. Copy .sql file into container

```docker cp <file.sql> <container-id>:/```

  

4. Open bash session in container

```docker exec -it <container-id> bash```

  

5. Open MYSQL connection

```mysql -u root -p$MYSQL_ROOT_PASSWORD```

  

6. Select vb database

```use vb```

  

7. Import database dump

```source <file.sql>```

  

### Copy uploads data

1. Copy site uploads to ./site/web/app/uploads

  

### Create languages folder if not created

```site/web/app/languages```

  

## First time setup (also this will first build the container)

1. Install composer dependencies for WP

```docker-compose run --rm vbr composer install```

# use if any dependencies error occure

```docker-compose run --rm vbr composer update```

  
  

2. Install comsposer dependencies for theme

```docker-compose -f docker-compose.yml -f docker-compose-theme.yml run --rm vbr composer install```

# use if any dependencies error occure

```docker-compose -f docker-compose.yml -f docker-compose-theme.yml run --rm vbr composer update```

  

3. Install yarn dependencies for theme

```docker-compose run --rm node_vbr yarn```

  

4. First time build

```docker-compose run --rm node_vbr yarn build```

  

## Run the project

1. Install composer dependencies for WP

```docker-compose up```

  

# Deploying to Staging

  

## Prerequisites

- Install Ansible

```

sudo apt update

sudo apt install software-properties-common

sudo add-apt-repository --yes --update ppa:ansible/ansible

sudo apt install ansible

```

- Set up VPN

- Set up access to Vault

  

## Deployment process

1. Update ```master``` branch

  

2. After build, update ```vb_image_version``` in file ```voicebookingwp/Ansible/_tst/group_vars/all/vars``` with build number under __Pipelines__ from repo

  

3. In ```~/.ssh``` folder, create file ```config```. Add the following in the file

```

Host voicebooking-dev

HostName vb.dev.deploy.nl

User dev

```

  

4. Turn on VPN

```sudo wg-quick up wg0```

  

5. Sign in to Vault

```vaultlogin```

  

6. Sign keys for dev server

```vaultssh-dev```

for prod server

```vaultssh-prod```

  

7. Go to ansible folder ```voicebookingwp/Ansible/```

  

8. Run deploy command

```ansible-playbook voicebooking.yml -i '_tst' --ask-vault-pass```

  
  

9. Run deploy command for staging

```ansible-playbook voicebooking.yml -i 'vbr' --ask-vault-pass```

Enter the vault password shared on Vault on prompt and proceed

  

9. Changes will be deployed after the above command has finished running

  
  

-----------------------

  

Modified plugin files

voicebookingwp/site/web/app/plugins/currency-switcher/index.php

  
  

docker exec vbr_db /usr/bin/mysqldump -u <username> -p<password> vb > backup.sql
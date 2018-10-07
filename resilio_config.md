# Resilio DCOS docker


## TODO
cmd DCOS => Create group and change perm (NAS)

## Config NEW
Username: resisyncgui  
Pass: pass$can$you$find$it  
Root: sync  
Key: ALH6YBBJFPBL4Y6RGYBXTELDVHYO3RGGL  
Link: https://link.resilio.com/#f=folders&sz=0&t=1&s=RSLZ4OQ2WX5PRHBCQKIHIS4WRTELSE5J&i=CDR4EYSMISFQSJ3GADX2Q7LLKHPR7Y3LV&v=2.5  

## Config OLD

https://hub.docker.com/r/resilio/sync/  
Username: resiliovirtu  
Password: resiliodcpass  

id:         /resilio 
path:       resilio/sync  
host path:  /mnt/ssh-nas/data-group07/sync/  
local path: /mnt/sync/resilio/  

```
{
  "id": "/resilio",
  "instances": 1,
  "portDefinitions": [],
  "container": {
    "type": "DOCKER",
    "volumes": [
      {
        "containerPath": "/mnt/sync/resilio/",
        "hostPath": "/mnt/ssh-nas/data-group07/sync/",
        "mode": "RW"
      }
    ],
    "docker": {
      "image": "resilio/sync"
    }
  },
  "cpus": 0.2,
  "mem": 1024,
  "requirePorts": false,
  "networks": [],
  "healthChecks": [],
  "fetch": [],
  "constraints": []
}
```

## SSHD NAS mdp
user : virtusers  
mdp  : virt2017  

### Commandes
sshfs virtusers@10.194.184.139:. /mnt/ssh-nas/  

### fix problem

#### (github thread)[https://github.com/moby/moby/issues/22258]
```This problem can be solved by using docker-entrypoint.sh
Using variable like MAP_USERID.
When running Docker Container, the first command to be run is docker-entrypoint.sh, will run usermod and chown directory.
# Set default WWW_DATA_USERID if not exist
# password is limited by 8 characters
: ${WWW_DATA_USERID:=33}

usermod -u $WWW_DATA_USERID www-data
groupmod -g $WWW_DATA_USERID www-data

chown -R www-data:www-data /var/www/html

exec "$@"
https://github.com/cuongtransc/docker-training/blob/master/images/wordpress/docker-entrypoint.sh#L220-L229
```

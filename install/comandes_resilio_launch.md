## interesting link
https://www.resilio.com/blog/sync-hacks-how-to-use-bittorrent-sync-as-geo-replication-for-storage

### copier un fichier dans le repo nas
sshpass -p virt2017 scp config.zip virtusers@10.194.184.139:./data-group07/
### récuperer le dit fichier
sshpass -p virt2017 scp virtusers@10.194.184.139:./data-group07/config.zip .
### le unzip
unzip config.zip

## config réelle
    export DEBIAN_FRONTEND="noninteractive"
    apt-get update && apt-get install -y apt-utils
    apt-get install -y sshpass unzip
    cd /mnt/sync/
    sshpass -p virt2017 scp -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no virtusers@10.194.184.139:./data-group07/config.zip .
    unzip config.zip


## config resilio json
    {
      "id": "/resilio",
      "backoffFactor": 1.15,
      "backoffSeconds": 1,
      "container": {
        "type": "DOCKER",
        "volumes": [
          {
            "containerPath": "/mnt/sync/folders/",
            "hostPath": "/mnt/ssh-nas/data-group07/sync/",
            "mode": "RW"
          }
        ],
        "docker": {
          "image": "resilio/sync",
          "forcePullImage": false,
          "privileged": false,
          "parameters": []
        }
      },
      "cpus": 0.2,
      "disk": 0,
      "instances": 1,
      "maxLaunchDelaySeconds": 3600,
      "mem": 1024,
      "gpus": 0,
      "networks": [
        {
          "mode": "host"
        }
      ],
      "portDefinitions": [],
      "requirePorts": false,
      "upgradeStrategy": {
        "maximumOverCapacity": 1,
        "minimumHealthCapacity": 1
      },
      "killSelection": "YOUNGEST_FIRST",
      "unreachableStrategy": {
        "inactiveAfterSeconds": 300,
        "expungeAfterSeconds": 600
      },
      "healthChecks": [],
      "fetch": [],
      "constraints": []
    }

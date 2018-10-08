[<< Back](README.md)


    /** JSON file Syncthing v1 (DockerHub) **/

    {
      "id": "/syncthing",
      "backoffFactor": 1.15,
      "backoffSeconds": 1,
      "container": {
        "type": "DOCKER",
        "volumes": [
          {
            "containerPath": "/var/syncthing",
            "hostPath": "/home/vagrant/syncthing/from_sync",
            "mode": "RW"
          }
        ],
        "docker": {
          "image": "syncthing/syncthing",
          "forcePullImage": false,
          "privileged": false,
          "parameters": []
        }
      },
      "cpus": 0.5,
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

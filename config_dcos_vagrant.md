[<< Back](README.md)

# Config Vagrant


# Config DC/OS

### Add volume on Marathon

[Deploying a Docker-based Service](https://docs.mesosphere.com/1.10/deploying-services/creating-services/deploy-docker-app/)  
[Marathon volume config](https://mesosphere.github.io/marathon/docs/external-volumes.html)  
[Marathon volume config](https://github.com/mesosphere/marathon/issues/5008)  
[Custom Docker Images](https://docs.mesosphere.com/service-docs/spark/v1.1.0-2.1.1/custom-docker/)

### Add proxy 
	{
	  "id": "nginx",
	  "container": {
		"type": "DOCKER",
		"docker": {
		  "image": "mesosphere/simple-docker",
		},
		"portMappings": [
		  { "hostPort": 80, "containerPort": 80, "protocol": "tcp" }
		]
	  },
	  "networks": [
		{
		  "mode": "container/bridge"
		}
	  ],
	  "acceptedResourceRoles": ["slave_public"],
	  "instances": 1,
	  "cpus": 0.1,
	  "mem": 64
	}
	
	
	
## Remove a package
To remove a package or installed ressources we need to remove it manually from the command line API. The GUI give the proper command to input. This is made in order to prevent unintentionall actions.

`./dcos package uninstall openvpn --app-id=/openvpn`


## Access to docker container
	docker exec -it <container_id> bash

### Install nano on container
	apt-get update
	apt-get install nano

## Mount volume
[rexray](https://github.com/thecodeteam/rexray)  
[dvdcli](https://github.com/codedellemc/dvdcli)  
[https://rexray.readthedocs.io/en/v0.3.3/user-guide/schedulers/](https://rexray.readthedocs.io/en/v0.3.3/user-guide/schedulers/)  
[https://rexray.readthedocs.io/en/v0.9.0/user-guide/schedulers/#docker-containerizer-with-marathon](https://rexray.readthedocs.io/en/v0.9.0/user-guide/schedulers/#docker-containerizer-with-marathon)  
[https://dcos.io/docs/1.7/usage/storage/persistent-volume/](https://dcos.io/docs/1.7/usage/storage/persistent-volume/)  
[https://docs.mesosphere.com/1.10/deploying-services/creating-services/](https://docs.mesosphere.com/1.10/deploying-services/creating-services/)  
[https://docs.mesosphere.com/1.10/storage/mount-disk-resources/](https://docs.mesosphere.com/1.10/storage/mount-disk-resources/)  
[https://rexray.readthedocs.io/en/stable/](https://rexray.readthedocs.io/en/stable/)  


## Add nextcloud and syncthing
docker repo : syncthing & nextcloud  
force docker to run on a1  
mount shared volume on the host a1  
bind /var/www/html/data for `nextcloud` container  
bind /var/syncthing/ in `syncthing` for config  
bind /var/syncthing/Sync in `syncthing` for data -> actually the same  

## Fix error nextcloud cannot wrinte on xxx/datas
sudo chown -R www-data: /var/www/html/data `On the syncthing container uid=33`  
sudo chown -R :vagrant /<volume_mapped> `On the host, uid 1000`  

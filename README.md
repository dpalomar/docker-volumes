Example of Volumes
===========

This example is based on [docker-apache](https://github.com/dpalomar/docker-apache.git) project.


### Image Base

Ubuntu 14.04


### How to Build

Simply `docker build -t your_image_name https://github.com/dpalomar/docker-volumes.git`

That's all

### Start the container
The container has all pre requirements set up to run any apache application. You can specify all needed environment variables. In this case we need pass the volume environment variable (*APACHE_DOCUMENTROOT*) to use another folder like document root for apache.

	$ sudo docker run -i -d -p 80 -e APACHE_DOCUMENTROOT=/webapps

**NOTE:** `/webapps` is the created default volume  folder on boot with Dockerfile:  [https://github.com/dpalomar/docker-volumes/blob/master/Dockerfile#L33-L35](https://github.com/dpalomar/docker-volumes/blob/master/Dockerfile#L33-L35)

Browser to url http://localhost:80.



### Get the container ip and port

    $ sudo docker inspect --format='{{.NetworkSettings.IPAddress}}' <container_id> 
    $ sudo docker port <container_id> 80 | cut -d ":" -f2

Now go to `<your container's ip>:<container's port>` in your browser

You should see the _"My server is up"_ message instead of default apache page.

### Stop the container

	$ sudo docker stop $(docker ps -ql)`


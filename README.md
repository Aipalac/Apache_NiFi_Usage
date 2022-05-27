# Apache_NiFi_Usage

**Install as docker image:**

*docker pull apache/nifi* -- to pull image from docker hub

to start container exec the next command:

*docker run --name nifi -p 8443:8443 -d apache/nifi*
this command would run the container with web interface on 8443 port on your localhost address.

You may set different values of env variables via *-e* flag
By default the name and password for web interface are generated when you run the container.
To see generated credentials exec the following command:

*docker logs -f nifi*

In order to set different credentials you have to run the container with flags:

*-e SINGLE_USER_CREDENTIALS_USERNAME=admin*
*-e SINGLE_USER_CREDENTIALS_PASSWORD=password*

full list of available environment variables you can find at */opt/nifi/scripts/start.sh* or at */opt/nifi/scripts/secure.sh*.

**Be careful, by default you may enter webUI only from list of defined addresses such as *localhost*, *127.0.0.1* etc.**
If you run the container on remote host even in your local network (for example 192.168.0.94), you have to use the following flag to make NiFi accessable through webUI:

*-e NIFI_WEB_PROXY_HOST='192.168.0.94:8443' *

also, using the *-e* flag you may change default port for webUI and many others things.

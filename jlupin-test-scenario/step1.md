## Task

1. Download the latest Jlupin Platform 1.6.1

`wget https://kacdab-download.s3.eu-central-1.amazonaws.com/jlupin_platform_version_1_6_1_latest.zip`{{execute}}

2. Unzip the Platform

`apt update && apt install unzip`{{execute}}
`unzip jlupin_platform_version_1_6_1_latest.zip`{{execute}}

3. Create the JLupin directory

`mkdir /opt/jlupin`{{execute}}

4. Move the Jlupin code to the JLUPIN_HOME directory

`mv platform/ /opt/jlupin/`{{execute}}

5. Set proper privileges

`chmod 750 /opt/jlupin/platform/start/start.sh`{{execute}}
`chmod 750 /opt/jlupin/platform/start/control.sh`{{execute}}

6. Set nginx user to root/root

`echo 'user root root;' | cat - /opt/jlupin/platform/start/configuration/edge.conf | tee /opt/jlupin/platform/start/configuration/edge.conf`{{execute}}

7. Set 128M for Xmx for the services

`cd /opt/jlupin/platform/application`{{execute}}
`for f in $(find . -name configuration.yml); do sed -i 's/Xmx256M/Xmx64M/g' $f; done`{{execute}}

8. Start the JLupin Platform server

`/opt/jlupin/platform/start/start.sh`{{execute}}

9. Visit the environment

Render port 8000/exchange/:

https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/exchange/

Render port 8000:

https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/

Display page allowing user to select port:

https://[[HOST_SUBDOMAIN]]-[[KATACODA_HOST]].environments.katacoda.com/

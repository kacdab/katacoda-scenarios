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

7. Set 64M for Xmx for the services

`cd /opt/jlupin/platform/application`{{execute}}
`for f in $(find . -name configuration.yml); do sed -i 's/Xmx[0-9]*M/Xmx64M/g' $f; done`{{execute}}
`for f in $(find . -name configuration.yml); do sed -i 's/Xms[0-9]*M/Xms64M/g' $f; done`{{execute}}
`for f in $(find . -name servlet_configuration.yml); do sed -i 's/Xmx[0-9]*M/Xmx128M/g' $f; done`{{execute}}
`for f in $(find . -name servlet_configuration.yml); do sed -i 's/Xms[0-9]*M/Xms128M/g' $f; done`{{execute}}
`sed -i 's/Xmx[0-9]*M/Xmx128M/g' /opt/jlupin/platform/start/control/configuration/setenv`{{execute}}
`sed -i 's/Xmx[0-9]*M/Xms192M/g' /opt/jlupin/platform/application/webcontrol/servlet_configuration.yml`{{execute}}
`sed -i 's/Xmx[0-9]*M/Xmx192M/g' /opt/jlupin/platform/application/webcontrol/servlet_configuration.yml`{{execute}}

8. Disable SSL

`cd /opt/jlupin/platform`{{execute}}
`sed -i '/ssl/ s/^#*/#/g' technical/nginx/linux/conf/servers/admin.conf`{{execute}}

9. Start the JLupin Platform server

`/opt/jlupin/platform/start/start.sh`{{execute}}

10. Visit the environment

Render port 8000/exchange/:

https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/exchange/

Render port 8000:

https://[[HOST_SUBDOMAIN]]-8000-[[KATACODA_HOST]].environments.katacoda.com/

Display page allowing user to select port:

https://[[HOST_SUBDOMAIN]]-[[KATACODA_HOST]].environments.katacoda.com/

## Task

1. Download the latest Jlupin Platform 1.6.1

`wget https://kacdab-download.s3.eu-central-1.amazonaws.com/jlupin_platform_version_1_6_1_latest.zip`{{execute}}

2. Unzip the Platform

`unzip jlupin_platform_version_1_6_1_latest.zip`{{execute}}

3. Create the JLupin directory

`mkdir /opt/jlupin`{{execute}}

4. Move the Jlupin code to the JLUPIN_HOME directory

`mv platform/ /opt/jlupin/`{{execute}}

5. Set proper privileges

`chmod 750 /opt/jlupin/platform/start/start.sh`{{execute}}
`chmod 750 /opt/jlupin/platform/start/control.sh`{{execute}}

6. Start the JLupin Platform server

`/opt/jlupin/platform/start/start.sh`{{execute}}

7. Visit the environment



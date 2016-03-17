# UnisonDocker
Dockerfile for commercial Unison

# Unison

Tremolo Security's Unison combines the identity management functions most needed by applications including:

* User Provisioning
* SSO
* LDAP Virtual Directory
* Reporting
* Workflow

## Available Tags

* latest (1.0.6)
* 1.0.6

## Deployment

Prior to deployment, a license must be obtained.  A 60 day trial license can be obtained by registering at https://www.tremolosecurity.com/support/ .  Once a license is obtained, its recommended to run Unison with a volume container.  
Create the volume controller :
```sh
$ docker  run -it -P  -v /usr/local/tremolo/tremolo-service/apps/proxy/auth -v /usr/local/tremolo/tremolo-service/conf -v /usr/local/tremolo/tremolo-service/apps/proxy/WEB-INF -v /usr/local/tremolo/tremolo-service/apps/tremolo-admin/WEB-INF -v /usr/local/tremolo/tremolo-service/apps/webservices/WEB-INF  --name 'unison-data-volume' -d tremolosecurity/unison
```
Deploy the image using the previous image as a data volume :
```sh
$ docker run -it -P  -p 9090:9090 -p 8080:8080 -p 8443:8443 -v /usr/local/tremolo/tremolo-service/logs --volumes-from unison-data-volume  --name 'unison-master' -d tremolosecurity/unison
```

# Alfresco Share in Docker

## Images created

* [`xeniteu/share-enterprise`] = enterprise Share images
* [`xeniteu/share-community`] = community Share images

## Supported Tags

* [`:5.1.5`, `:5.1`, `:5`] = major, minor, revision for enterprise
* [`:5.1.e`, `:6.1.2-ga`] =  major, minor, revision for community

## Overview

This is Xenit's repository for Alfresco Share docker images. A major-minor version has a common skeleton, based on the Dockerfile provided in the repository.
Community and enterprise-specific artifacts are then added via the [docker-alfresco plugin](https://github.com/xenit-eu/alfresco-docker-gradle-plugin).

All images are automatically built by [jenkins-2](https://jenkins-2.xenit.eu) and published to [hub.xenit.eu](https://hub.xenit.eu).
Community images are built by [Travis](https://travis-ci.org/xenit-eu/) and published to [docker hub](https://hub.docker.com/u/xeniteu).


## Image Variants

Multi-container: `share` to be used together with soon on github [`docker-alfresco`](https://github.com/xenit-eu/docker-alfresco), [`docker-solr`](https://github.com/xenit-eu/docker-solr), [`postgres`](https://github.com/xenit-eu/docker-postgres).

## Environment variables

There are several environment variables available to tweak the behaviour. While none of the variables are required, they may significantly aid you in using these images.
The variables are read by an init script which further replaces them in the relevant files. Such relevant files include:

* share-config-custom.xml

Additionally, tomcat and or java-specific environment variables can be used (see [`docker-tomcat`](https://github.com/xenit-eu/docker-tomcat), [`docker-openjdk`](https://github.com/xenit-eu/docker-openjdk)).

Environment variables:

| Variable                    |  Default                        | Java variable |
| --------------------------- | ------------------------------- | --------------------------- |
| ALFRESCO_HOST               |  alfresco                       |  |
| ALFRESCO_PORT               |  8080                           |  |
| ALFRESCO_PROTOCOL           |  http                           |  |
| ALFRESCO_CONTEXT            |  alfresco                       |  |
| TOMCAT_PORT                 |  8080                           | -DTOMCAT_PORT                |                                                         
| TOMCAT_PORT_SSL             |  8443                           | -DTOMCAT_PORT_SSL            |                                                         
| TOMCAT_AJP_PORT             |  8009                           | -DTOMCAT_AJP_PORT            |                                                          
| TOMCAT_SERVER_PORT          |  8005                           | -DTOMCAT_SERVER_PORT         |                                                          
| TOMCAT_MAX_HTTP_HEADER_SIZE |  32768                          | -DTOMCAT_MAX_HTTP_HEADER_SIZE  or -DMAX_HTTP_HEADER_SIZE   |                                         |  |
| TOMCAT_MAX_THREADS          |  200                            | -DTOMCAT_MAX_THREADS or -DMAX_THREADS                        |                                                           |  |
| JAVA_XMS                    |  512                            | -Xmx                                                         |  
| JAVA_XMX                    |  2048                           | -Xms                                                         |   
| DEBUG                       |    false                        | -Xrunjdwp:transport=dt_socket,address=0.0.0.0:8000,server=y,suspend=n |     false                                                         |  |
| JMX_ENABLED                 |    false                        | -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.local.only=false -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.rmi.port=5000 -Dcom.sun.management.jmxremote.port=5000 -Djava.rmi.server.hostname=$JMX_RMI_HOST |                                
| JMX_RMI_HOST                |                                 |                                                              |  0.0.0.0                                                            |  |
| JAVA_OPTS_\<variable\>=\<value\>       |                      | \<value\>                                                   |                                                              |  |

## Docker-compose files

For example docker-compose files, see [docker-alfresco](https://github.com/xenit-eu/docker-alfresco).

## Support & Collaboration

These images are updated via pull requests to the [xenit-eu/docker-share/](https://github.com/xenit-eu/docker-share/) Github-repository.

**Maintained by:**

Roxana Angheluta <roxana.angheluta@xenit.eu>, Lars Vierbergen <lars.vierbergen@xenit.eu>

### How to build

To build a local version of the _share_ images:

```
./gradlew buildDockerImage
```



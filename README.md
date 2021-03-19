# Alfresco Share in Docker
Alfresco Share images built and maintained by Xenit.

## Images created

* [`docker.io/xenit/share-enterprise`] = enterprise Share images
* [`docker.io/xenit/share-community`] = community Share images

Up to Alfresco version 6, share artifacts for enterprise were protected by a login on Alfresco's Nexus. From version 6 onwards, they are public. 

## Supported Tags

* [`:5.1.5`, `:5.1`, `:5`] = major, minor, revision for enterprise
* [`:5.1.e`, `:6.1.2-ga`] =  major, minor, revision for community

## Overview

This is Xenit's repository for Alfresco Share docker images. A major-minor version has a common skeleton, based on the Dockerfile provided in the repository.
Community and enterprise-specific artifacts are then added via the [docker-alfresco plugin](https://github.com/xenit-eu/alfresco-docker-gradle-plugin).

All images are automatically built by [jenkins-2](https://jenkins-2.xenit.eu) and published to [hub.xenit.eu](https://hub.xenit.eu).
Community images are built by [Github actions](https://github.com/features/actions) and published to [docker hub](https://hub.docker.com/u/xenit). Starting with version 6, all share images are public.

## Image Variants

Multi-container: `share` to be used together with [`docker-alfresco`](https://github.com/xenit-eu/docker-alfresco), [`docker-solr`](https://github.com/xenit-eu/docker-solr), [`postgres`](https://github.com/xenit-eu/docker-postgres).

## Environment variables

There are several environment variables available to tweak the behaviour. While none of the variables are required, they may significantly aid you in using these images.
The variables are read by an init script which further replaces them in the relevant files. Such relevant files include:

* share-config-custom.xml

See also environment variables from lower layers: [`docker-openjdk`](https://github.com/xenit-eu/docker-openjdk) and [`docker-tomcat`](https://github.com/xenit-eu/docker-tomcat).

Environment variables:

| Variable                    |  Default                        | Java variable |
| --------------------------- | ------------------------------- | --------------------------- |
| ALFRESCO_HOST               |  alfresco                       |  Used to generate WebDav links.|
| ALFRESCO_PORT               |  8080                           |  Used to generate WebDav links.|
| ALFRESCO_PROTOCOL           |  http                           |  Used to generate WebDav links.|
| ALFRESCO_CONTEXT            |  alfresco                       |  Used to generate WebDav links.|
| ALFRESCO_INTERNAL_HOST      |  alfresco                       |  Used for communication share-alfresco.|
| ALFRESCO_INTERNAL_PORT      |  8080                           |  Used for communication share-alfresco.|
| ALFRESCO_INTERNAL_PROTOCOL  |  http                           |  Used for communication share-alfresco.|
| ALFRESCO_INTERNAL_CONTEXT   |  alfresco                       |  Used for communication share-alfresco.|

If environment variables are not sufficient to cover the use-case desired, a custom share-config-custom.xml file can be mounted in /docker-config/share-config-custom.xml.

## Docker-compose files

For example docker-compose files, see [docker-alfresco](https://github.com/xenit-eu/docker-alfresco).

## Support & Collaboration

These images are updated via pull requests to the [xenit-eu/docker-share/](https://github.com/xenit-eu/docker-share/) Github-repository.

### How to build

To build a local version of the _share_ images:

```
./gradlew buildDockerImage
```



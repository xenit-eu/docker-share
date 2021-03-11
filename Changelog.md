# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## Unreleased

### Added
* [ALFREDOPS-687] Add image for 6.2.2.
* [DOCKER-275] Introduce variables for direct communication share-alfresco. Make sure that ALFRESCO_INTERNAL_HOST is set to the correct name of the alfresco service/container.
	
## [v1.0.1] 2020-12-14

### Added
* [DOCKER-291] Add image for 6.2.0.
* [DOCKER-347] Added build for Alfresco enterprise 5.2.7

	
### Changed
* [DOCKER-354] Move to github actions for public images.	
* [DOCKER-278] Java options have been moved to the Java layer.
* [DOCKER-274] Explicitelly add docker.io in front of public images.
* [DOCKER-257] Add namespace for hub.xenit.eu images.	
* [DOCKER-254] Allow to mount a custom share-config-custom.xml. Location to mount: /docker-config/share-config-custom.xml.
* [DOCKER-262], [DOCKER-259] Refactorings, notifications	
* [DOCKER-348] Upgraded gradle wrapper to v6.7, Alfresco docker plugin to v5.0.7 and JDK to 11
	
## [v1.0.0] Make it public

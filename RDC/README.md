Remote Data Gateway on Docker
=============
Sample Docker configurations to facilitate installation, configuration, and environment setup for DevOps users. 
This project includes quick start [dockerfiles](dockerfiles/) for Remote Data Gateway based on Oracle Linux 6 and Oracle Analytics Cloud 19.2.3 Release.

The certification of Remote Data Gateway for Oracle Analytics Cloud on Docker does not require the use of any file presented in this repository. 
Customers and users are welcome to use them as starters, and customize/tweak, or create from scratch new scripts and Dockerfiles.

For pre-built images containing Oracle software, please check the [Oracle Container Registry](https://container-registry.oracle.com).

The instructions below can also be used to build and run Remote Data Gateway for any other certified Oracle Analytics Cloud release as required.

### Building the Remote Data Gateway Image

Download the installer for [Remote Data Gateway](https://www.oracle.com/middleware/technologies/oac-downloads.html) for Linux x86-64-bit into folder `OACRemoteDataGateway/dockerfiles/V2`.

If a proxy is needed for the host to access required images, then first set up the appropriate environment, e.g.:

        $ export http_proxy=myproxy.example.com:80
        $ export https_proxy=myproxy.example.com:80
        $ export no_proxy="localhost,127.0.0.1,localaddress,.localdomain.com"

Build the image:

        $ cd OACRemoteDataGateway/dockerfiles
        $ ./buildDockerImage.sh -v V2

## Creating a Remote Data Gateway container

e.g.:

        $ docker run -it -p 8080:8080 -e username=<admin> -e pwd=<admin_password> oracle/rdc:V2


## The following example URL provides access to the Remote Data Gateway:
* http://&lt;host&gt;:&lt;port&gt;/javaads/config.jsp - Remote Data Gateway Configuration


## Known Issues
1. Docker health-check is not implemented.


## License

To download and run Remote Data Gateway Distribution regardless of inside or outside a Docker container, and regardless of the distribution, you must download the binaries from the Oracle website and accept the license indicated on that page.

All scripts and files hosted in this project and GitHub [docker/RDC](./) repository required to build the Docker images are, unless otherwise noted, released under the Universal Permissive License v 1.0 as shown at http://oss.oracle.com/licenses/upl.

## Copyright

Copyright (c) 2019 Oracle and/or its affiliates. All rights reserved.

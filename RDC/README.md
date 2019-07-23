Remote Data Connector on Docker
=============
Sample Docker configurations to facilitate installation, configuration, and environment setup for DevOps users. This project includes quick start [dockerfiles](dockerfiles/) for Remote Data Connector based on Oracle Linux 6 and Oracle FMW Infrastructure 12.2.1.3.0.

The certification of Oracle Business Intelligence on Docker does not require the use of any file presented in this repository. Customers and users are welcome to use them as starters, and customize/tweak, or create from scratch new scripts and Dockerfiles.

For pre-built images containing Oracle software, please check the [Oracle Container Registry](https://container-registry.oracle.com).

The instructions below can also be used to build and run Remote Data Connector V2, based on FMW Infrastructure 12.2.1.3.0 as required.

## Database prerequisite

You need to have a running Oracle Database, either in a Docker container or on a host. 
The database connection details are required for creating midtier schemas for use by RDC.
 
### Building the Remote Data Connector Image

Download the binary for [Remote Data Connector V2](https://www.oracle.com/technetwork/middleware/oac/downloads/index.html) for Linux x86-64-bit into folder `RDC/dockerfiles/V2`.

If a proxy is needed for the host to access required images, then first set up the appropriate environment, e.g.:

        $ export http_proxy=myproxy.example.com:80
        $ export https_proxy=myproxy.example.com:80
        $ export no_proxy="localhost,127.0.0.1,localaddress,.localdomain.com"

Build the image:

        $ cd RDC/dockerfiles
        $ ./buildDockerImage.sh -v V2

## Creating an Remote Data Connecter Container

e.g.:

        $ docker run -it -p 8080:8080 -e username=<admin> -e pwd=<admin_password> oracle/rdc:V2

##The following example URL provide access to the RDC:
* http://www.example.com:8080/javaads/config.jsp - RDC Configuration

##Known Issues
1. Docker health-check is not implemented.

## License

To download and run Remote Data Connector(RDC) V2 Distribution regardless of inside or outside a Docker container, and regardless of the distribution, you must download the binaries from the Oracle website and accept the license indicated on that page.

All scripts and files hosted in this project and GitHub [docker/RDC](./) repository required to build the Docker images are, unless otherwise noted, released under the Universal Permissive License v 1.0 as shown at http://oss.oracle.com/licenses/upl.

## Copyright

Copyright (c) 2019 Oracle and/or its affiliates. All rights reserved.

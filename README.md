NodeJS Docker images
====================

This repository contains the source for building various versions of
the Node.JS runtime as Docker images using
[source-to-image](https://github.com/openshift/source-to-image).
Users can choose between RHEL and CentOS based builder images.
The resulting image can be run using [Docker](http://docker.io).

For more information about using these images with OpenShift, please see the
official [OpenShift Documentation](https://docs.openshift.org/latest/using_images/s2i_images/nodejs.html).

For more information about contributing, see
[the Contribution Guidelines](https://github.com/sclorg/welcome/blob/master/contribution.md).
For more information about concepts used in these docker images, see the
[Landing page](https://github.com/sclorg/welcome).


Versions
---------------
Node.JS versions currently provided are:
* [NodeJS 8](8)
* [NodeJS 9](9)

RHEL versions currently supported are:
* RHEL7

CentOS versions currently supported are:
* CentOS7


Build
---------------
Choose either the CentOS or RHEL based image:
*  **RHEL based image**

    To build a RHEL based Node.JS builder, you need to run the build on a properly
    subscribed RHEL machine.

    ```
    $ git clone --recursive https://github.com/bucharest-gold/s2i-nodejs-container.git
    $ cd s2i-nodejs-container
    $ git submodule update --init
    $ make build TARGET=rhel7 VERSIONS=8
    ```

*  **CentOS based image**

    To build a CentOS based Node.JS builder run:

    ```
    $ git clone --recursive https://github.com/bucharest-gold/s2i-nodejs-container.git
    $ cd s2i-nodejs-container
    $ git submodule update --init
    $ make build TARGET=centos7 VERSIONS=8
    ```

**Notice: By omitting the `VERSIONS` parameter, the build/test action will be performed
on all provided versions of Node.JS.**


Usage
---------------------------------

For information about usage of Dockerfile for NodeJS 8,
see [usage documentation](8/README.md).
For information about usage of Dockerfile for NodeJS 9,
see [usage documentation](9/README.md).

Test
---------------------
This repository also provides a [S2I](https://github.com/openshift/source-to-image) test framework,
which launches tests to check functionality of a simple Node.JS application built on top of the s2i-nodejs image.

Users can choose between testing a Node.JS test application based on a RHEL or CentOS image.

*  **RHEL based image**

    To test a RHEL7 based Node.JS image, you need to run the test on a properly
    subscribed RHEL machine.

    ```
    $ cd s2i-nodejs-container
    $ git submodule update --init
    $ make test TARGET=rhel7 VERSIONS=8
    ```

*  **CentOS based image**

    ```
    $ cd s2i-nodejs-container
    $ git submodule update --init
    $ make test TARGET=centos7 VERSIONS=8
    ```

**Notice: By omitting the `VERSIONS` parameter, the build/test action will be performed
on all provided versions of Node.JS.**


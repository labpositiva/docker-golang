labpositiva/golang:1.8
======================

|Build Status| |GitHub issues| |GitHub license|

Requirements
------------

None

Dependencies
------------

none

Usage
-----

In order to run a basic container start a container as follows:

``docker run -P --name golang -e ENV=DEV labpositiva/golang:1.8``

Environment Variables
---------------------

This is a list of the available environment variables which can be set
at runtime using -e KEY=value. For example, to change the default
environment you can issue
``docker run -P --name golang -e ENV=dev labpositiva/golang:1.8``

.. |Build Status| image:: https://travis-ci.org/labpositiva/docker-golang.svg
   :target: https://travis-ci.org/labpositiva/docker-golang
.. |GitHub issues| image:: https://img.shields.io/github/issues/labpositiva/docker-golang.svg
   :target: https://github.com/labpositiva/docker-golang/issues
.. |GitHub license| image:: https://img.shields.io/github/license/mashape/apistatus.svg?style=flat-square
   :target: LICENSE

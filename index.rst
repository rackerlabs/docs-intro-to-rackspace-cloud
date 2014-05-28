Introduction to Rackspace Cloud
===============================

Contents:

.. toctree::
   :maxdepth: 2

Introduction
------------

This guide was designed to serve as an introduction to the Rackspace Public Cloud. It covers core concepts which are important to understand before interacting with the Rackspace Cloud, from signing up for an account to methods for interacting with your account and how to request support.

**This guide is currently a work in progress.** Issues regarding the contents can be submitted to https://github.com/rackerlabs/docs-intro-to-rackspace-cloud/issues.


Our Products and Services
-------------------------

 - Highlight which are OpenStack services; include brief paragraph on OpenStack
 - RackConnect


Support Service Levels
----------------------


Important Concepts and Terms
----------------------------

Regions
~~~~~~~

At Rackspace, we define a region as a group of one or more data centers (physical buildings) located in close geographic proximity to one another, such that it is possible to achieve <= 3 milliseconds of latency for intra-region network communication.

We currently have the following regions:

 - IAD (Northern Virginia, United States)
 - DFW (Dallas / Fort Worth, Texas, United States)
 - ORD (Chicago, Illinois, United States)
 - LON (London, United Kingdom)
 - SYD (Sydney, Australia)
 - HKG (Hong Kong)

Control Plane
~~~~~~~~~~~~~

The control plane for a cloud service is comprised of the API servers and other control infrastructure that you interact with to provision data plane resources. For example, the Cloud Servers public API, scheduler, and database make up portions of the Cloud Servers control plane.

Data Plane
~~~~~~~~~~

The data plane for a cloud service is where your data resides and ongoing data processing takes place. For example, the host machines housing virtual machine instances comprise the data plane for our Cloud Servers offering.

Regional versus Global services
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Global versus UK Cloud
~~~~~~~~~~~~~~~~~~~~~~

Interaction Methods
-------------------

Control Panel: https://mycloud.rackspace.com
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Software Development Kits (SDKs)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Command-line Clients
~~~~~~~~~~~~~~~~~~~~

Direct API Access
~~~~~~~~~~~~~~~~~

Support
-------

Getting Support from a Racker
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Community Forums
~~~~~~~~~~~~~~~~

System Status: http://status.rackspace.com
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To Do
-----

 - Signing up for an account
 - Currency / billing / consolidated invoicing / tracking usage
 - Commit and volume discounts
 - System architecture
 - Scale out not up
 - Authentication / RBAC / Identity tokens / Service catalog
 - Absolute and rate limits
 - Security
 - Compliance
 - Data in Transit
 - All APIs are HTTPS
 - Data at Rest
 - Customers can encrypt themselves
 - Physical Security
 - Physical DC security
 - All HDDs are shredded
 - SLAs: http://www.rackspace.com/information/legal/cloud/sla

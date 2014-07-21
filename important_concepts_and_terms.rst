Important Concepts and Terms
============================

Regions
-------

At Rackspace, we define a region as a group of one or more data centers
(physical buildings) located in close geographic proximity to one another, such
that it is possible to achieve <= 3 milliseconds of latency for intra-region
network communication.

We currently have the following regions:

 - IAD (Northern Virginia, United States)
 - DFW (Dallas / Fort Worth, Texas, United States)
 - ORD (Chicago, Illinois, United States)
 - LON (London, United Kingdom)
 - SYD (Sydney, Australia)
 - HKG (Hong Kong)

Control Plane
-------------

The control plane for a cloud service is comprised of the API servers and other
control infrastructure that you interact with to provision data plane resources.
For example, the Cloud Servers public API, scheduler, and database make up
portions of the Cloud Servers control plane.

Data Plane
----------

The data plane for a cloud service is where your data resides and ongoing data
processing takes place. For example, the host machines housing virtual machine
instances comprise the data plane for our Cloud Servers offering.

Regional versus Global services
-------------------------------

Many of the Rackspace Cloud services are deployed as separate instances to each
region in which they are available. Regional deployments allow for rolling
software updates and maintenances which minimize impact to each region. If you
are leveraging our APIs directly, you will notice that each of the endpoints for
these services contains the region in the URL. The service in each region has no
knowledge of the resources that are deployed in other regions (for example,
listing your Cloud Servers in DFW will not also show your Cloud Servers in ORD).
The following services are deployed separately in each region:

 - Cloud Auto Scale
 - Cloud Backup
 - Cloud Big Data
 - Cloud Block Storage
 - Cloud Databases
 - Cloud Files
 - Cloud Images
 - Cloud Load Balancers
 - Cloud Networks
 - Cloud Orchestration
 - Cloud Queues
 - Cloud Servers

Other services are deployed as a single global endpoint:

 - Cloud DNS
 - Cloud Identity
 - Cloud Monitoring

It is important to note that global services are deployed to multiple regions to
increase their availability. Interacting with the single instance of the service
propagates relevant changes to all regions in which the service is deployed.

Global versus UK Cloud
----------------------

There are currently two types of cloud accounts that you can create depending on
which region(s) you need to access:

 - Global cloud account (all regions except LON)

  - Provides access to IAD, DFW, ORD, SYD, and HKG regions
  - Sign up at https://cart.rackspace.com/cloud
  - Billed in US Dollars (USD)

 - London cloud account

  - Provides access to LON region
  - Sign up at https://buyonline.rackspace.co.uk/cloud
  - Billed in British Pounds (GBP)

In the future we plan to move toward a single global account model with the
ability to select from multiple currencies.

Authentication
--------------

TODO: RBAC / Identity tokens / Service catalog

Absolute Limits
---------------

Absolute Limits control the total number of resources you can possess
simultaneously from specific services (for example, the total number of Cloud
Servers you can have in the DFW region). As you are provisioning infrastructure,
it is important to be aware of the absolute limits in place for the services you
are consuming and to request increases with adequate lead time for a Racker to
review your request (typically 24-48 hours). If you encounter an absolute limit,
please contact Rackspace Support for further assistance or to request an
increase.

Rate Limits
-----------

Rate Limits control the frequency at which you can issue specific API requests
for specific services (for example, the number of times you can request your
server list from the Cloud Servers API per minute). Each service defines rate
limits, and requests from the Control Panel, SDKs, and direct API requests count
toward your limits. If you encounter a rate limit, please contact Rackspace
Support for further assistance or to request an increase.

TODO: Include limits here or link to somewhere else (product user guides?)?

Service Level Agreements (SLAs)
-------------------------------

The Rackspace Cloud offers industry-leading SLAs for our services. Additional
details about the SLAs for individual services can be found at
http://www.rackspace.com/information/legal/cloud/sla.
Key Concepts
============

Regions
-------

A region is a collection of one or more data centers, located in close
geographic proximity (e.g. the same metro area), with a low latency, high
bandwidth network. Specifically, regions are designed such that any two cloud
resources (e.g. two Cloud Servers, a Cloud Server and a Cloud Database)
provisioned in the same region will have a maximum network latency of 3 ms with
a typical intra-region network latency of ~1 ms. While a region may contain
multiple physical data centers for scale, one can simply think of a region as a
logically singular data center. Regions are designated by the nearest airport
code.

Geographic Choice
^^^^^^^^^^^^^^^^^

Regions are important because they provide geographic choice and awareness of
where your cloud resources are physically provisioned. This may be important to
get your application close to end users or to integrate with other Rackspace or
non-Rackspace resources in a hybrid deployment scenario.

Reliability
^^^^^^^^^^^

Rackspace operates world class data centers and our regions are designed to be
reliable. As such, no sub-region zonal constructs are required to work around
failure.

Since regions are reliable, you can build and deploy highly available
applications in a single region. If you want to protect against a widespread
regional failure (e.g. a localized geographic catastrophe), we recommend
deploying your application across multiple regions.

Current Regions
^^^^^^^^^^^^^^^

 - IAD (Northern Virginia, United States)
 - DFW (Dallas, Texas, United States)
 - ORD (Chicago, Illinois, United States)
 - LON (London, United Kingdom)
 - SYD (Sydney, Australia)
 - HKG (Hong Kong)

If you have no specific region preference in the United States, we recommend new
customers use the IAD region. At present, ORD is not available to new customers
by default. If you have a specific need to be in the ORD region, please contact
Rackspace Support.

Regional Services
-----------------

Service Independence
^^^^^^^^^^^^^^^^^^^^

By design, the majority of Rackspace Cloud services are deployed and operated as
separate, independent regional instantiations (i.e. a given service in region A
has no interaction with or dependency on the region B, C, D, etc.
instantiation). This has several important implications that are important for
users to understand.

For a given regional service:

 - Regions can be considered as independent failure domains. Should a service in
   a given region experience an operational issue, that issue will not propagate
   across regions.

 - Service updates and maintenance are performed in a rolling fashion and are
   never performed in multiple regions at the same time.

These points are particularly important for applications that are deployed
cross-region since regions can be relied on as a hard boundary for failure.

*For API users:* Since regional services are independent, you will notice
different regional API endpoints for each regional service (all available
service endpoints are dynamically provided in a service catalog after you
successfully authenticate). You target a region simply by using the appropriate
regional endpoint. No state is shared across regions so use the appropriate
regional endpoint to create, list, update, or delete resources in that region.

Current Regional Services
^^^^^^^^^^^^^^^^^^^^^^^^^

 - Cloud Auto Scale
 - Cloud Backup
 - Cloud Big Data
 - Cloud Block Storage
 - Cloud Databases
 - Cloud Feeds
 - Cloud Files
 - Cloud Images
 - Cloud Load Balancers
 - Cloud Networks
 - Cloud Orchestration
 - Cloud Queues
 - Cloud Servers

Global Services
---------------

A handful of Rackspace Cloud services are global in nature. These services are
logically singular, but state is replicated across multiple physical regional
deployments. This provides cross-region high availability, improves local
performance for all regions where the global service resides, and delivers an
eventually consistent global view of service data.

*For API users:* You will notice a single API endpoint for each global service
(all available service endpoints are dynamically provided in a service catalog
after you successfully authenticate).

Current Global Services
^^^^^^^^^^^^^^^^^^^^^^^

 - Cloud DNS
 - Cloud Identity
 - Cloud Monitoring

 .. _global-versus-uk-cloud:

Global vs. UK Accounts
----------------------

At present, there are two types of cloud accounts you can create depending on
which region(s) you need to access:

 - Global Account

  - Provides access to the IAD, DFW, ORD, SYD, and HKG regions
  - Billed in US Dollars (USD)
  - Sign up at https://cart.rackspace.com/cloud
  
 - UK Account

  - Provides access to the LON region
  - Billed in British Pounds (GBP)
  - Sign up at https://buyonline.rackspace.co.uk/cloud

Separate accounts are temporary and we are working to unify our systems towards
a single account type with access to all global regions.

Service Planes
--------------

Control Plane
^^^^^^^^^^^^^

A service control plane is comprised of API servers and other controlling
infrastructure used to provision data plane resources. For example, the Cloud
Servers public API and scheduler make up portions of the Cloud Servers control
plane.

Data Plane
^^^^^^^^^^

A service data plane includes the actual resources provisioned using the control
plane. For example, virtual and bare metal servers are part of the Cloud Servers
data plane.

Service Limits
--------------

Rate Limits
^^^^^^^^^^^

Rate limits control the frequency at which specific API requests are allowed
(e.g. the number of times you can request your server list from the Cloud
Servers API per minute). Rate limits exist to protect the service control plane
from abuse, whether malicious or accidental.

Services have separate, independent rate limits, including different regional
deployments of the same service. Requests from the Control Panel, SDKs, and
direct RESTful API requests count toward your limits.

Default rate limits for each service can be found in the service API guide.
Default rate limits are set such that most users will not encounter them,
however, rate limits can be raised if necessary. To request a rate limit
increase, open a ticket or contact Rackspace Support for assistance.

Real-time rate limit information is also available programatically via API (see
appropriate service API guide for more info). Programmatic access includes
current limits, request capacity consumed, request capacity still available, and
next available request windows. This information enables high API request
applications to dynamically throttle back requests as limits approach and to
have visibility into when they can re-ramp requests.

Absolute/Resource Limits
^^^^^^^^^^^^^^^^^^^^^^^^

Absolute (aka Resource) limits control the total amount of service resources
(e.g. the total amount of RAM of virtual Cloud Servers, the total number of
Cloud Block Storage volumes, etc.) you can possess simultaneously. Absolute
limits exist to protect service data plane capacity from abuse, whether
malicious or accidental.

Services have separate, independent absolute limits, including different
regional deployments of the same service.

Default absolute limits for each service can be found in the section below.
Default absolute limits are set to provide a reasonable amount of resources for
testing and modestly-sized environments and applications. If you require
additional resource capacity, absolute limits can be raised upon request. To
request an absolute limit increase, open a ticket or contact Rackspace Support
for assistance.

Real-time absolute limit information is available in the Rackspace Cloud Control
Panel as seen here:

TODO: Insert reach "Resource Limits" screen shot

Absolute limit information is also available programatically via API (see
appropriate service API guide for more info). Programmatic access includes
current limits as well as resources consumed. This information provides
visibility into real-time resource usage and can be used to dynamically
determine when accounts are approaching their absolute limit.

The current default absolute limits for each service are:

**Cloud Servers**

*Virtual*

128GB of total RAM across all virtual flavor classes

*OnMetal*

10 OnMetal I/O v1 servers
10 OnMetal Compute v1 servers
10 OnMetal Memory v1 servers

TODO: More here AND/OR should this all go in the specific service user guides?

Cloud Identity
--------------

All Rackspace Cloud services share a common, global identity service called
Cloud Identity. Cloud Identity provides 3 primary functions:

Service Authentication
^^^^^^^^^^^^^^^^^^^^^^

Before using a Rackspace Cloud service, you must first obtain an authentication
token. This token is used to authenticate and authorize each service call and
must be passed in with every API request. To obtain an authentication token,
authenticate to Cloud Identity using your Rackspace Cloud credentials.
Authentication tokens automatically expire after 24 hours at which time a new
token must be obtained from Cloud Identity. Should you need to, authentication
tokens may also be revoked. For more information, please see the Cloud Identity
API Guide.

Service Endpoints
^^^^^^^^^^^^^^^^^

Multiples services across a set of global regions can be a lot of API endpoints!
Rather than statically document all service endpoint URLs, they are dynamically
returned as part of your Cloud Identity authentication response. This is called
the Service Catalog. The Service Catalog can be examined to determine which
services are available, in which regions, with which API versions, and what the
service API URLs are. With both an authentication token and the service catalog,
you are now ready to access Rackspace Cloud services. For more information,
please see the Cloud Identity API Guide.

Role Based Access Control (RBAC)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The final function of Cloud Identity is to manage roles. Roles are used to limit
access to certain services and/or specific service API operations (e.g. viewing
but not deleting Cloud Servers). Primary accounts may create subusers and manage
the roles of those subusers to control access.

TODO: Should provide more info here or link to another RBAC guide 

Rackspace Networks
------------------

Network Types 
^^^^^^^^^^^^^

**PublicNet**

PublicNet provides connectivity to the public Internet and supports native
Rackspace provided IPv4 and IPv6 public addresses. Traffic inbound from the
Internet is free while traffic outbound to the Internet is billed at the
advertised utility rate.

**ServiceNet**

ServiceNet is a private, internal (although still multi-tenant) Rackspace
network that supports Rackspace provided private RFC 1918 IPv4 addresses.
ServiceNet is optimized for east-west traffic and recommended for *communication
between services* (e.g. Cloud Servers to Cloud Databases, Cloud Load Balancers
to Cloud Servers, etc.) within a region. At present, you cannot communicate
across regions using ServiceNet. ServiceNet IP addresses are all from the
10.176.0.0/12 and 10.208.0.0/12 ranges. ServiceNet IP addresses are unique per
region but may overlap across regions. All ServiceNet traffic is free.

**Cloud Networks**

Cloud Networks are isolated, single-tenant networks that can be dynamically
created and controlled by users. They support IPv4 or IPv6 and address selection
is controlled by users (we recommend using private RFC 1918 address space that
does not conflict with ServiceNet or other connected private networks). Cloud
Networks are optimized for east-west traffic and recommended for all *Cloud
Server to Cloud Server communication* within a region. At present, you cannot
communicate across regions using Cloud Networks. All Cloud Networks traffic is
free.

Communicating Between Regions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

All region to region communication must occur using PublicNet. Although
PublicNet is also used to carry Internet traffic, all region to region PublicNet
traffic transits a private, global Rackspace network rather than the Internet.
At present, the ORD, DFW, IAD, and LON regions are interconnected with dedicated
links which allow Rackspace to better control latency, ensure quality of
service, etc. The HKG and SYD regions are connected with VPN links that ensure
privacy of data. Rackspace constantly monitors and upgrades our private network
as region to region bandwidth needs grow.

Service APIs on ServiceNet
^^^^^^^^^^^^^^^^^^^^^^^^^^

All Rackspace Cloud service APIs are publically available on the Internet,
however, in same cases, it makes sense for them to also be available on
ServiceNet. This occurs when substantial amounts of data may pass to/from the
API. For example, if the public Cloud Files API is being use to store 100GB of
data from a Cloud Server, 100GB of outbound PublicNet bandwidth charges would be
incurred. To avoid this, a separate "internal" endpoint of the Cloud Files API
is also available on ServiceNet. Since ServiceNet is optimized for east-west
traffic and bandwidth is free, we recommend using internal API endpoints
wherever possible.

The following services have internal API endpoints:

 - Cloud Files
 - Cloud Queues
 - Cloud Feeds   

As with all service API URLs, they can be dynamically discovered from the
Service Catalog after Cloud Identity authentication. Internal API URLs are
designated by the "internalURL" attribute.
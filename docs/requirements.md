
# IXP Technical Requirements OIX-1

Version 2.0 ***DRAFT***, August 3, 2016

Questions: <ix-group@open-ix.org>

Following outlines the technical requirements for an IXP to be certified by
Open-IX. The requirements define minimum functionality, such that IXPs can
adhere to the Open-IX standard serving different communities with different
requirements. Varying from small single datacenter IXPs serving a limited
local community to large scale many datacenter metro environments, but leave
room for modifications that meet the need of the local community. The purpose
of the requirements is to provide publicly available information on what the
participants of the IXP can expect, and not to describe in detail how the IXP
is designed, built or operated.

The keywords used throughout the document are as defined in RFC 2119.

The IXP SHOULD follow the Best Current Operational Practices for an Internet
Exchange, posted at <http://nabcop.org/index.php/Main_Page>.


## Definition of an IXP.

A physical network infrastructure operated by a single entity with the purpose
to facilitate the exchange of Internet traffic between Autonomous Systems. The
intention is to connect more than 2 Autonomous Systems, and there MUST be a
clear and open policy for others to join.


## Services

### Minimal Service Offering

The IXP MUST provide the services described below. This in no way inhibits the
operator from providing additional services, or methods of interconnection.

#### Public Exchange VLAN (IX)

A switch platform which allows anytoany interconnection. Customer interfaces
with Ethernet frames tagged for the public exchange VLAN MUST be forwarded in
accordance with the traffic rules indicated in this document.

### Additional Service Offering
The IXP MAY provide additional services, as long as they are described on a publicly available website of the IXP.

#### Private VLAN (PVLAN)

A private switch platform, whereby any two or more parties may consent to
interconnect through either the same physical port that delivers their access
to the Public Exchange VLAN or alternatively dedicated physical port(s). If a
PVLAN service is offered, in case there are exactly two parties in the private
VLAN the connection MUST be delivered guaranteed congestion free. In case of
more than two parties the service MAY be best effort.

### Physical Interface

The IXP MUST be able to offer IEEE 802.3 Ethernet connectivity on a common
switch infrastructure.

Service offerings MAY be available at any other IEEE defined rate, including
802.3ad link aggregation of any of these rates.

The complete service offering MUST be described on a publicly available
website. The information provided MUST contain: link rate and physical media
(copper, fiber and fiber type).

### Traffic Forwarding

The IXP MUST forward frames with the following Ethertypes:

- 0x0800 IPv4
- 0x86dd IPv6

Valid frames with Ethertype 0x86dd may be suppressed on the Public Exchange
VLAN due to MLD snooping, or alternate methods used to implement IPv6 neighbor
discovery.

If there is no provision to handle ARP in any other way, the IXP MUST forward
frames with the following Ethertype:

- 0x0806 ARP

If the IXP has reason to limit certain traffic, the IXP MUST publish on a
publicly available website what traffic is not allowed and or not forwarded on
the exchange platform.

If the IXP applies a MAC address locking mechanism on a participants port,
then the IXP MUST make known to customers the process to update MAC addresses.

### Customer Interface

The IXP MUST provide a clear demarcation point between the IXP services and
the customer. This can be either directly on the exchange or via a common
demarcation point available to the participants.


## Infrastructure

### Switching Platform

The IXP switching platform MUST have backplane capacity to sufficiently handle
the aggregate traffic of all customerfacing ports, without oversubscription.
If individual switching elements contain multiple switch fabric modules, the
same conditions MUST apply during single component failures.

The IXP MUST run any inter-switch links congestion free.

The IXP SHOULD have redundant power feeds fed from discrete sources (A and B)
for all exchange infrastructure. If the IXP does not have redundant power
feeds on any components, it MUST describe where not on a publicly available
website.

If the IXP does not have full path diversity between two discrete switching
elements in different physical locations, this MUST be described on the IXPs
publicly available website.

The IXP MUST describe on a publicly available website the infrastructure and
the redundancy measures implemented to overcome single component failures.

### IP Space

In order to be independent of any of the connected parties, the IP space used
on the “Public Exchange VLAN” MUST be PI space or other IP space directly
assigned by a RIR. This applies to both IPv4 and IPv6. The IXP operator will
be responsible for obtaining address space from the respective RIR, as well as
providing all material for justification, documentation, and applicable fees
as required by the RIR.

### Route Server

If a route server service is offered then it MUST support both IPv4 and IPv6
and 4byte ASNs. The AS number used for the route server implementation MUST be
a unique AS number assigned by one of the RIRs.

The IXP MUST publish the route server setup on a publicly available website.


## Operations

### NOC

The IXP MUST publish a telephone number, email address or any other means that
provides immediate access to technical support, on a website available to its
participants, on how to contact operational staff that is capable of managing
the IXP infrastructure. The access method MUST be available 24x7, note this
does not mean staff needs to be available 24x7, but the IXP MUST publish staff
hours.

The IXP MUST provide and publish a procedure to announce service affecting
maintenance to its participants.

### Monitoring

The IXP MUST monitor the exchange platform for performance degradation and
service affecting events.

The IXP MUST provide a procedure to inform its participants on performance
degradation and service affecting events.

### Statistics

The IXP MUST publish on a publicly available website the participants on the
peering platform and the relevant AS numbers.

The IXP MUST publish on a publicly available website the total sum of all
incoming and outgoing traffic in bps from all connected networks on the public
peering VLAN. The traffic sum MUST include the traffic on customer facing
ports only and MUST be made up of 5 min average traffic measurements. A
distinction MUST be made between the traffic on the public peering VLAN and
any other interconnection service.

### Website

The IXP MUST have available and maintain a publicly available website where at
least the subjects mentioned in this document MUST be addressed.

## Miscellaneous

The IXP MUST have and maintain an accurate entry in a peering contact and
configuration directory. This entry MUST contain a list of all facilities they are present at.


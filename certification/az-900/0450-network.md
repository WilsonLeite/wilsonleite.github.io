## Describe virtual networking, including the purpose of Azure virtual networks, Azure virtual subnets, peering, Azure DNS, Azure VPN Gateway, and ExpressRoute

### Virtual networking

"A Virtual Network emulates a Network Router and defines a private IP address space. The IP range only exists within the virtual network and isn't internet routable."

<< Add example >>

Azure virtual networks and virtual subnets enable Azure resources to communicate with each other, with users on the internet, and with on-premises client computers. 

It provides:

* Isolation and segmentation

Creation of subnets or multiple Virtual Networks may be used to isolate resources.

* Internet communications

By default, resources connected to a Virtual Network have outbound access to the Internet. incoming connections from the internet can be configured by assigning a public IP address to an Azure resource, or putting the resource behind a public load balancer.

* Communicate between Azure resources

Resources like VMs, VM Scale Sets, App Services, Power Apps, and Kubernetes Services.
Service endpoints can connect to other Azure resource types, such as Azure SQL databases and storage accounts.

<< What do you mean by Service endpoints? >>

* Communicate with on-premises resources

    * Point-to-site virtual private network connections are from a computer outside an  organization back into the corporate network. In this case, the client computer initiates an encrypted VPN connection to connect to the Azure virtual network.
    * Site-to-site virtual private networks link an on-premises VPN device or gateway to the Azure VPN gateway in a virtual network. In effect, the devices in Azure can appear as being on the local network. The connection is encrypted and works over the internet.
    * Azure ExpressRoute provides a dedicated private connectivity to Azure that doesn't travel over the internet. ExpressRoute is useful for environments where there are needs for greater bandwidth and even higher levels of security.

* Route network traffic

By default, Azure routes traffic between subnets on any connected virtual networks, on-premises networks, and the internet. Those settings can vew overriden as follows:

Route tables allow rules about how traffic should be directed between subnets.

Border Gateway Protocol (BGP) works with Azure VPN gateways, Azure Route Server, or Azure ExpressRoute to propagate on-premises BGP routes to Azure virtual networks.

* Filter network traffic between subnets

* Network security groups are Azure resources that can contain multiple inbound and outbound security rules. These rules allow or block traffic, based on factors such as source and destination IP address, port, and protocol.
* Network virtual appliances are specialized VMs that can be compared to a hardened network appliance. A network virtual appliance carries out a particular network function, such as running a firewall or performing wide area network (WAN) optimization.

* Connect virtual networks by using virtual network peering

Peering allows two virtual networks to connect directly to each other. Network traffic between peered networks is private and it enables resources in each virtual network to communicate with each other. These virtual networks can be in separate regions, which allows the creation of a global interconnected network through Azure.

<< Create one using the exercise >>


### Virtual subnets

Subnets enable the segmentation of the virtual network into one or more subnetworks and allocate a portion of the virtual network's address space to each subnet. Azure resources can be deployed to a specific subnet. Resources within subnets can be secured using Network Security Groups.

### Peering

Virtual network peering enables seamlessly connecting two or more Virtual Networks in Azure. The virtual networks appear as one for connectivity purposes. Traffic between the virtual networks is kept on the Microsoft backbone network.

The Virtual Networks can be in different regions, subscriptions, tenants, and deployment models.

### Azure DNS

Azure DNS is a hosting service for DNS domains that provides name resolution by using Microsoft Azure infrastructure. By hosting your domains in Azure, you can manage your DNS records using the same credentials, APIs, tools, and billing as your other Azure services. It resolves address to Azure resources as well as to external resources.

Advantages:

* Reliability and performance

DNS domains in Azure DNS are hosted on Azure's global network of DNS name servers, providing resiliency and high availability. Azure DNS uses anycast networking, so each DNS query is answered by the closest available DNS server to provide fast performance and high availability. 

* Security

Management access uses Azure Resource Manager, providing role-based access control and activity logs.

* Ease of Use

Can be managed using the regular Azure tools like the Portal, CLI, etc.

* Customizable virtual networks

Azure DNS also supports private DNS domains. This feature allows using custom domain names in private virtual networks, rather than being stuck with the Azure-provided names.

* Alias records

<< How Alias work? >>

It can be used to map internal Azure resources URLs like Azure public IP address, an Azure Traffic Manager profile, or an Azure Content Delivery Network (CDN) endpoint.

<< Would it work with external domains? >>

### Azure VPN Gateway

Azure VPN Gateway instances are deployed in a dedicated subnet of the virtual network and enable the following connectivity:

* Connect on-premises datacenters to virtual networks through a site-to-site connection.
* Connect individual devices to virtual networks through a point-to-site connection.
* Connect virtual networks to other virtual networks through a network-to-network connection.

You can deploy only one VPN gateway in each virtual network. However, you can use one gateway to connect to multiple locations, which includes other virtual networks or on-premises datacenters.

Types of VPN:

* Policy-based: Specify statically the IP address of packets that should be encrypted through each tunnel
* Route-based: IPSec tunnels are modeled as a network interface or virtual tunnel interface. IP routing (either static routes or dynamic routing protocols) decides which one of these tunnel interfaces to use when sending each packet.

Use a route-based VPN gateway if you need any of the following types of connectivity:

* Connections between virtual networks
* Point-to-site connections
* Multisite connections
* Coexistence with an Azure ExpressRoute gateway

<<< ??? >>>

High-availability scenarios:

* Active/standby (default): Azure hides the existence on the secondary instance and switch between them automatically in case of failure or maintenance. The downtime can go from a few seconds (planned maintenance) to 90 seconds.
* Active/active: Each instance has its own public IP and tunnel and a routing protocol may be used for balancing and failover. Optionally, another VPN device may be deployed on-premises as well.
* ExpressRoute failover: A VPN Gateway may be configured on standby in case of a failure on the ExpressRoute connection.
* Zone-redundant gateways: VPN gateways and ExpressRoute gateways can be deployed connecting to different availability zones in the same region. 

### ExpressRoute

It connects on-premises networks to the Microsoft cloud over a private connection.

Connectivity can be from an any-to-any (IP VPN) network, a point-to-point Ethernet network, or a virtual cross-connection through a connectivity provider at a colocation facility. ExpressRoute connections don't go over the public Internet.

![ExpressRoute](https://learn.microsoft.com/en-us/azure/expressroute/media/expressroute-introduction/expressroute-connection-overview.png)

 It supports four models:

* CloudExchange colocation
* Point-to-point Ethernet connection
* Any-to-any connection
* Directly from ExpressRoute sites

<< The description of those is not clear enough >>

ExpressRoute Global Reach link ExpressRoute circuits together to make a private network between on-premises networks:

![ExpressRoute Global Reach](https://learn.microsoft.com/en-us/azure/expressroute/media/expressroute-global-reach/global-reach.png)

References:

Microsoft Learn: 
* [Describe Azure virtual networking](https://learn.microsoft.com/en-us/training/modules/describe-azure-compute-networking-services/8-virtual-network)
* [What is Azure Virtual Network?](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)

* [Describe Azure virtual private networks](https://learn.microsoft.com/en-us/training/modules/describe-azure-compute-networking-services/10-virtual-private-networks)
* [Virtual network peering](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-peering-overview)
* [Describe Azure ExpressRoute](https://learn.microsoft.com/en-us/training/modules/describe-azure-compute-networking-services/11-expressroute)
* [About ExpressRoute Global Reach](https://learn.microsoft.com/en-us/azure/expressroute/expressroute-global-reach)
* [Describe Azure DNS](https://learn.microsoft.com/en-us/training/modules/describe-azure-compute-networking-services/12-domain-name-system)

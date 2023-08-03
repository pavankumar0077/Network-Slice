# Network-Slice

What is network slicing
---

```
    As its name suggests, Network Slicing consists in cutting up a network into logical sub-networks, called “slices”. Each network slice is developed, deployed, and managed independently – but deployed – on a shared physical infrastructure.…
As its name suggests, Network Slicing consists in cutting up a network into logical sub-networks, called “slices”. Each network slice is developed, deployed, and managed independently – but deployed – on a shared physical infrastructure.

This solution enables operators to adapt the mobile network and levels of service to the specific needs of different types of services and users in real time.

Indeed, Orange structures the use cases of 5G into three families:

5G mobile broadband, which equates to an improvement in the “traditional” usage we have of our smartphone;
5G massive IoT, which enables low-speed connection of several billion sensors and connected objects;
and 5G Ultra Low Latency High Reliability, aimed at critical applications in the areas of connected healthcare, industry 4.0, or autonomous mobility.
As the network slices are configurable according to the uses that they support, it is possible to allocate dedicated resources to each one and thus deliver the right level of performance (in terms of reliability, security, latency, bandwidth capacity or coverage).

A 5G network split into virtual slices can thus support several types of application simultaneously – both consumer and business – without them treading on each other’s toes. We can for example imagine allocating a network slice to virtual reality, to emergency medicine, or to vehicle management.

Although Network Slicing was already technically possible with 4G, it will be made more flexible and more dynamic thanks to 5G technology, which is bringing mobile networks forwards towards more virtualisation. This virtualisation is necessary for Network Slicing to fulfil all of its promises in terms of network flexibility and optimisation, thus making it possible to go from a one-size-fits-all approach to specialised connectivity services for certain uses.
```
REF LINK : https://hellofuture.orange.com/en/a-word-of-innovation-network-slicing/

Network Slicing Architecture
---
![image](https://github.com/pavankumar0077/Network-Slice/assets/40380941/50b1195f-7899-4952-8e33-30ca2caddf61)


```
    **Infrastructure Layer:** This layer forms the foundation of the network slicing architecture and includes the physical and virtual resources required to support network services. It consists of physical infrastructure components such as servers, routers, switches, and radio access equipment, as well as virtualized resources like virtual machines, containers, and software-defined networking (SDN) controllers.

    **Management and Orchestration (MANO):** The MANO layer is responsible for the overall management and orchestration of network slices. It includes three main components:

   ** Network Slice Lifecycle Management:** This component handles the creation, modification, and termination of network slices. It ensures that the required resources are allocated, configured, and interconnected to form the desired slice.

    **Network Slice Service Management:** This component focuses on managing the services provided by network slices. It includes functions such as service instantiation, monitoring, scaling, and assurance.

    **Network Slice Resource Management: **This component deals with the allocation and optimization of network resources for each slice. It dynamically manages the allocation of virtualized resources, network bandwidth, and Quality of Service (QoS) parameters based on the slice requirements and network conditions.

   ** Control Plane:** The control plane is responsible for controlling the behavior and configuration of network elements within each network slice. It includes the following elements:

    **Network Slice Selection Function (NSSF):** The NSSF determines the appropriate network slice to use based on the service requirements, user preferences, and network conditions. It interacts with the policy and charging functions to select the best-fit slice for each user or service.

   ** Network Slice Subnet Management Function (NSSMF):** The NSSMF manages the subnet aspects of network slices. It handles the creation, modification, and deletion of subnet instances within a slice.

   ** Network Slice Instance Management Function (NSIMF):** The NSIMF is responsible for managing the network slice instances, including their lifecycle, configuration, and control.

   ** User Plane:** The user plane handles the data traffic within each network slice. It consists of various network functions and data forwarding mechanisms that enable the transport of user data between endpoints. The user plane is tailored to the specific requirements of each slice, such as latency, bandwidth, and traffic prioritization.

    **Service Layer:** The service layer represents the uppermost layer of the network slicing architecture, where specific services or applications are deployed. It includes service-specific functions, protocols, and interfaces required to provide the desired functionality. Examples of service layer components include virtualized network functions (VNFs), service gateways, application servers, and content delivery platforms.
``` 

How 5G network slicing works in AOSP
--

![image](https://github.com/pavankumar0077/Network-Slice/assets/40380941/8cabf205-b4e7-4eed-a49d-5a7d6f22b2d2)

Implementation
---
```     
    To support 5G slicing on a device, the device must have a modem that supports the IRadio 1.6 HAL which has the setupDataCall_1_6 API. This API sets up a data connection and includes the following parameters for supporting 5G slicing:

trafficDescriptor: Specifies traffic descriptor sent to the modem
sliceInfo: Specifies information for the network slice to be used in case of EPDG to 5G handover
matchAllRuleAllowed: Specifies whether using a default match-all URSP rule is allowed. Telephony sets this to true for default networks but not for slices. The match all rule is applied to default networks. When an application requests a specific slice that is not available, the specific slice is reported as not available, but the application can fallback to the default network.
Modems must also implement the getSlicingConfig API unless it's reported as unsupported by the getHalDeviceCapabilities API.

```
Enterprise requirements
---
``` The following describes requirements for enterprises to use 5G network slicing on devices in an Android enterprise deployment.

Ensure that fully managed or employee devices set up with a work profile are 5G SA-capable with modems that support the setupDataCall_1_6 API.
Work with carrier partner on slice setup and performance or SLA characteristics.
Enabling 5G slicing on devices set up with a work profile
For devices that are set up with work profiles, 5G network slicing is off by default in AOSP. To enable network slicing, enterprise IT admins can turn on or off work profile app traffic routing to the enterprise network slice on a per-employee basis through the EMM DPC, which uses the setPreferentialNetworkServiceEnabled method in the DevicePolicyManager (DPM) API (introduced in Android 12).

EMM vendors with custom DPCs must integrate the DevicePolicyManager API to support enterprise clients.
``` 

URSP rules
--- 

``` This section includes information for carriers on configuring URSP rules for different slice categories including enterprise, CBS, low latency, and high bandwidth traffic. When configuring URSP rules for different slice categories, carriers must use the following Android-specific values.

ID	Value	Description
OSId	97a498e3-fc92-5c94-8986-0333d06e4e47	The OSId for Android is a version 5 UUID generated with the namespace ISO OID and the name "Android".
``` 

Testing
---
``` 
To test 5G network slicing, use the following manual test.

To setup a device for testing, do the following:

Ensure that the URSP policy is configured with a non-default rule that matches the enterprise category and that the corresponding route-selection descriptor maps the enterprise category to the enterprise slice; and a default rule directing traffic to the default internet slice.

Ensure that a work profile is configured on the device.

Opt in to using network slicing through the DPC

To test 5G network slicing behavior, do the following:

Verify that a PDU session is established with the enterprise slice (for example, by using a specific IP address) and that apps in work profile use that PDU session.
Verify that a separate PDU session is established with the default internet slice and that apps in the personal profile use the PDU session.
```

REF LINK : https://source.android.com/docs/core/connect/5g-slicing

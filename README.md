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
    Infrastructure Layer: This layer forms the foundation of the network slicing architecture and includes the physical and virtual resources required to support network services. It consists of physical infrastructure components such as servers, routers, switches, and radio access equipment, as well as virtualized resources like virtual machines, containers, and software-defined networking (SDN) controllers.

    Management and Orchestration (MANO): The MANO layer is responsible for the overall management and orchestration of network slices. It includes three main components:

    Network Slice Lifecycle Management: This component handles the creation, modification, and termination of network slices. It ensures that the required resources are allocated, configured, and interconnected to form the desired slice.

    Network Slice Service Management: This component focuses on managing the services provided by network slices. It includes functions such as service instantiation, monitoring, scaling, and assurance.

    Network Slice Resource Management: This component deals with the allocation and optimization of network resources for each slice. It dynamically manages the allocation of virtualized resources, network bandwidth, and Quality of Service (QoS) parameters based on the slice requirements and network conditions.

    Control Plane: The control plane is responsible for controlling the behavior and configuration of network elements within each network slice. It includes the following elements:

    Network Slice Selection Function (NSSF): The NSSF determines the appropriate network slice to use based on the service requirements, user preferences, and network conditions. It interacts with the policy and charging functions to select the best-fit slice for each user or service.

    Network Slice Subnet Management Function (NSSMF): The NSSMF manages the subnet aspects of network slices. It handles the creation, modification, and deletion of subnet instances within a slice.

    Network Slice Instance Management Function (NSIMF): The NSIMF is responsible for managing the network slice instances, including their lifecycle, configuration, and control.

    User Plane: The user plane handles the data traffic within each network slice. It consists of various network functions and data forwarding mechanisms that enable the transport of user data between endpoints. The user plane is tailored to the specific requirements of each slice, such as latency, bandwidth, and traffic prioritization.

    Service Layer: The service layer represents the uppermost layer of the network slicing architecture, where specific services or applications are deployed. It includes service-specific functions, protocols, and interfaces required to provide the desired functionality. Examples of service layer components include virtualized network functions (VNFs), service gateways, application servers, and content delivery platforms.
``` 

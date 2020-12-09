# Summary of the papers on 5G network slicing (Draft)
## Articles
- [3GPP re.15](#3GPP re.15)
- [Network Slicing for 5G: Challenges and Opportunities](# Network Slicing for 5G: Challenges and Opportunities)
- [A Standards-Based, Model-Driven Solution for 5G Transport Slice Automation and Assurance](# A Standards-Based, Model-Driven Solution for 5G Transport Slice Automation and Assurance)
- [Latency-Sensitive 5G RAN Slicing for Industry 4.0](# Latency-Sensitive 5G RAN Slicing for Industry 4.0)
- [Reshaping the mobile core network via function decomposition and network slicing for the 5G Era](# Reshaping the mobile core network via function decomposition and network slicing for the 5G Era)

## 3GPP re.15[Link](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=3144)
### Type: Network Slicing basic
### Citation
```
[]3GPP, Technical Specification Group Services and System Aspects; System architecture for the 5G System (5GS); Stage 2 (Release 15), documentTS 23.501 V15.11.0 (2020-09)
```
### Note
- A Network Slice instance is defined within a PLMN and shall include: **the Core Network Control Plane** and **User Plane Network Functions**.
-  The operator can deploy multiple Network Slices delivering exactly the **same features** but for **different** groups of **UEs**.
- The network may serve **a single UE** with one or more Network Slice instances **simultaneously** via a 5G-AN regardless of the access type(s) over which the UE is registered (i.e. 3GPP Access and/or N3GPP Access).
- The **AMF** instance serving the **UE** **logically** belongs to each of the **Network Slice** instances serving the **UE**, i.e. this **AMF** instance is common to the **Network Slice** instances serving a **UE**.
- A **PDU** Session belongs to **one** and **only one** specific Network Slice instance per PLMN. **Different Network Slice** instances do not share a **PDU** Session, though **different Network Slice** instances may have slice-specific PDU Sessions using the **same DNN**.
- An **S-NSSAI** identifies a Network Slice. An S-NSSAI is comprised of:
  -  A Slice/Service type (**SST**), which refers to the expected Network Slice behaviour in terms of features and services;
  -  A Slice Differentiator (**SD**), which is optional information that complements the Slice/Service type(s) to differentiate amongst multiple Network Slices of the same Slice/Service type.
    ![image](Week1-2/img/Snipaste_2020-12-04_11-02-58.png)
- The **NSSAI** is a collection of **S-NSSAIs**.  There can be at most **eight** **S-NSSAIs** in Allowed and Requested **NSSAIs** sent in signalling messages between the **UE** and the **Network**.  
- A Network Slice instance can be associated with one or more S-NSSAIs, and an S-NSSAI can be associated with one or more Network Slice instances.
- Based on the Requested **NSSAI** (if any) and the **Subscription Information**, the **5GC** is responsible for **selection** of a Network Slice instance(s) to serve a **UE** including the **5GC Control Plane** and **User Plane Network Functions** corresponding to this Network Slice instance(s).
- The Subscription Information shall contain **one** or **more** **S-NSSAIs**.
- The **Network Slice configuration information** contains one or more Configured **NSSAI**(s). There is **at most** **one** Configured **NSSAI** per **PLMN**.
- When providing a Requested **NSSAI** to the network upon **registration**, the UE in a given **PLMN** only includes and uses **S-NSSAIs** applying to **this PLMN**
- Upon **successful completion** of a UE's Registration procedure over an Access Type, the UE obtains from the **AMF** an **Allowed** **NSSAI** for this Access Type, which includes **one or more SNSSAIs** and, if needed (see clause 5.15.4.1.2 for when this is needed), their **mapping** to the **HPLMN S-NSSAIs**.
- How the **UE** stores **(S-)NSSAI?**(page 144-145)
- The establishment of User Plane connectivity to a Data Network via a Network Slice instance(s) comprises two steps:
  - performing a RM procedure to select an AMF that supports the required Network Slices.
  - establishing one or more PDU Session to the required Data network via the Network Slice instance(s).
- When a UE application associated with a specific S-NSSAI requests data transmission:(page 151-152)
## Network Slicing for 5G: Challenges and Opportunities [Link](https://ieeexplore.ieee.org/abstract/document/8039298)
### Type: Network Slicing basic
### Citation
```
@ARTICLE{8039298,
  author={X. {Li} and M. {Samaka} and H. A. {Chan} and D. {Bhamare} and L. {Gupta} and C. {Guo} and R. {Jain}},
  journal={IEEE Internet Computing}, 
  title={Network Slicing for 5G: Challenges and Opportunities}, 
  year={2017},
  volume={21},
  number={5},
  pages={20-27},
  doi={10.1109/MIC.2017.3481355}}
```
### Note
- **Why we need NS?**: Fifth-generation networks need to integrate multiple services with various performance requirements — such as high throughput, low latency, high reliability, high mobility, and high security — into a single physical network infrastructure, and provide each service with a **customized logical network** (that is, network slicing).
-  Specifcally speaking, a network slice is a **virtual network** that’s created on top of a physical network in such a way that it gives the illusion to the slice tenant of operating its **own dedicated physical network**.
- 5G network slicing includes slicing the 5G **radio access network (RAN)**, **5G core network**, and even end-user devices. **5G RAN slicing** can be implemented through **logical abstraction** of physical radio resources (such as spectrum) and physical hardware (such as a base station). **SDN** and **NFV** can confgure the **virtual network resources** ﬂexibly, which include network bandwidth, server processing capability, and network element processing capability, to build the core network slices for specifc service requirements.
- **Virtual resources** and **VNFs** run as **virtual machine (VM)** instances. These resources are in fact an **abstraction** of the underlying physical resources managed at 5G-SDI and can be shared across slices. 

  ![image](Week1-2/img/Snipaste_2020-12-03_19-54-59.png)
- Services that have **similar** demands might share one network slice, and services with **different** service requirements can still share the slices partially.
- The slicing **MANO** functional component **manages** and **orchestrates** the **physical resources**, **virtual resources**, and **network slices** in the way the NFV-MANO will be built in.The tasks of slicing MANO include:
  - creating and managing VM instances by using the infrastructure resources;
  - mapping network functions to virtual resources and connecting network functions to create service chains; and
  - managing the life cycle of network slices by interacting with the application and service layer — for example, automated creation of service-oriented slices and dynamic maintenance by monitoring service requirements and virtual resources.


- Slices needs to be highly isolated from each other.
- **The effective isolation of network slices can ensure that the failure or security attack on one slice doesn’t affect other slices’ operation.**
- **Security**: Resource sharing among slices. Network slices serving different types of services may have different levels of security policy requirements, it’s necessary to consider the impact on multiple slices and entire network systems, when designing protocols.

## A Standards-Based, Model-Driven Solution for 5G Transport Slice Automation and Assurance [Link](https://ieeexplore.ieee.org/abstract/document/9165451)
### Type: Transport Slicing
### Citation
```
@INPROCEEDINGS{9165451,
  author={R. {Rokui} and H. {Yu} and L. {Deng} and D. {Allabaugh} and M. {Hemmati} and C. {Janz}},
  booktitle={2020 6th IEEE Conference on Network Softwarization (NetSoft)}, 
  title={A Standards-Based, Model-Driven Solution for 5G Transport Slice Automation and Assurance}, 
  year={2020},
  volume={},
  number={},
  pages={106-113},
  doi={10.1109/NetSoft48620.2020.9165451}}
```
### Note
- The **main challenges** in the current commercialization of end-to-end slicing services include: Automation, Cross-domain connection, SLA guarantee
- To create each **E2E** network slice, **Operator-X** must create a** RAN-Slice**, a **Core-Slice** and a **Transport Slice**(a “slice”, as the term is used here, in some standards development organizations is called a **sub-slice** or a **slice-subnet**).There is one E2E network slice **orchestrator** to manage and control the E2E virtual network.
  ![image](Week1-2/img/Snipaste_2020-12-03_19-14-43.png)
  ![image](Week1-2/img/Snipaste_2020-12-03_19-16-16.png)
- A **network slice** is a **logical network** that provides specific network capabilities and network characteristics. A Network Slice Instance (NSI) is set of Network Function (**NF**) instances and the required **resources**. 
- A **Transport Slice** needs to satisfy the following requirements:
  - Provide connections between various **network functions** (VNFs and PNFs);
  - Support connection **SLAs**;
  - Support multiple connection service types (L0-L3)
- An end-to-end  Network Slice Subnet Instance (NSSI) can be composed of three sub-NSSIs: wireless, transmission, and core network NSSI. 
- **Fig. 4** illustrates the logical flow among the various layers of controllers for automation of a single E2E network slice where the E2E NS Orchestrator receives a request from a customer for creation of an E2E network slice (**Step 1**). Using its NS Blueprints, it creates a profile and triggers various actions (**Step 2**). First it sends a request to the RAN Slice Controller for creation of a RAN Slice (**Step 3**). If any RAN virtual network function is needed, it will be created as part of this step. NFVO will manage the life cycle of RAN VNFs. Similarly, in **Step 4**, the Core Slice Controller will create the Core Slice. In **Step 5**, a request to create connectivity between RAN and Core slices is sent to the Transport Slice Controller; the resulting Transport Slices are sets of connections with specific SLAs. In the end, the RAN, Core and Transport Slices are associated together to create a single E2E network slice with specific ID. 3GPP refers to this ID as **S-NSSAI** which is simply an ID for newly created E2E network slice.
  ![image](Week1-2/img/Snipaste_2020-12-03_19-24-33.png)







## Latency-Sensitive 5G RAN Slicing for Industry 4.0 [Link](https://ieeexplore.ieee.org/abstract/document/8853247)
### Type: RAN Slicing
### Citation
```
@ARTICLE{8853247, 
author={J. {García-Morales} and M. C. {Lucas-Estañ} and J. {Gozalvez}},  
journal={IEEE Access},   title={Latency-Sensitive 5G RAN Slicing for Industry 4.0},   
year={2019},  
volume={7},  
number={},  
pages={143139-143159},  
doi={10.1109/ACCESS.2019.2944719}}
```
### Note
- **RAN slicing** is in charge of **splitting and configuring resources** at the **RAN** level among the slices.
- Current RAN slicing solutions are mainly designed with the objective to satisfy the users’ bandwidth or rate demands. 
- **4G** (or LTE – Long Term Evolution) defines a **fixed** slot duration. On the other hand, **5G NR** defines different slot durations, and can simultaneously 
support different numerologies to serve a variety of applications

  ![image](Week1-2/img/Snipaste_2020-12-02_20-41-43.png)

- 5G NR divides a wideband channel into **10ms frames** and **1ms sub-frames**. A **sub-frame** is in turn divided into **slots**. **Slots** include **14 consecutive OFDM** (Orthogonal FrequencyDivision Multiplexing) symbols for a normal cyclic prefix or CP; they include** 12 consecutive OFDM symbols** for the extended CP. 
- A **Resource Block (RB)** is the **smallest unit** of frequency resources that can be allocated to a node. It is defined as **12 consecutive** sub-carriers in the **frequency domain** and **one slot** in the **time domain**. 
- Each 5G NR numerology µ modifies the Sub-Carrier Spacing (SCS) 1f and the time (Tslot) duration 
- RAN slicing decides how radio resources are configured and allocated to slices in order to support nodes with different QoS requirements.
- The allocation of RBs to slices is maintained during a time period referred to as **allocation window**. This period has a duration of **Tw** slots
- Illustration of RAN slicing.

  ![image](Week1-2/img/Snipaste_2020-12-02_21-05-54.png)

- RAN slicing and lifecycle of slices.

  ![image](Week1-2/img/Snipaste_2020-12-02_21-10-02.png)
## Reshaping the mobile core network via function decomposition and network slicing for the 5G Era [Link](https://ieeexplore.ieee.org/abstract/document/7564652?casa_token=oGJu6kOG2EcAAAAA:fYTUheMWAw8lwTG3GuUrEoyBQg0nLv7zaS1ST4Yd6gjPyOXVyuZEP6XIT5833lvklqRQu1q3kw)
### Type: Core Slicing
### Citation
```
@INPROCEEDINGS{7564652,
  author={M. R. {Sama} and X. {An} and Q. {Wei} and S. {Beker}},
  booktitle={2016 IEEE Wireless Communications and Networking Conference}, 
  title={Reshaping the mobile core network via function decomposition and network slicing for the 5G Era}, 
  year={2016},
  volume={},
  number={},
  pages={1-7},
  doi={10.1109/WCNC.2016.7564652}}
```
### Note
- **Function decomposition** is an approach to separate out the tightly coupled network **sub-functions** within a network entity. Separated **sub-functions** can be run either in the same or different network entities.
- The mathematical definition of **function decomposition**: for a primary function F (e.g. PGW), a set of sub-functions f1, f2, ...fx can be identified in order to reconstruct the primary function via another function as, F = phi(f1, f2, ...fx).

  ![image](Week1-2/img/Snipaste_2020-12-03_17-15-15.png)

- The network entities in the **current EPC** can be classified into two types : **(1)** entities like the **MME** that have control tasks and thus only handle **control plane (C-plane)** traffic, and **(2)** those entities that have to also handle** user plane (U-plane)** traffic, like the **SGW** and **PGW**. 
-  The **sub-functions** of MME, SGW and PGW can be classified in meta function groups. 

    ![image](Week1-2/img/Snipaste_2020-12-03_17-21-39.png)

- **EPC** function decomposition can be classified in two categories: **horizontal decomposition** and **vertical decomposition**. The **“horizontal**" decomposition refers to decoupling the C- and U-plane functions. The **“vertical decomposition"** refers to identifying the individual functions encompassed in one network entity.
- By using the **NFV** approach such decomposed functions can be implemented as software and a chain of network functions can be selected and compiled for dedicated user groups.
- The major merit of EPC function decomposition and re-composition is to provide the feasibility to the network slice concept at the **sub-function** level. 
- One network slice can be considered as the combination of **service layer** and **infrastructure layer**. 
  - **Service layer** represents the system architecture at the **logical level**, which consists of **network functions** and their **chaining relationship**. In general, to form the service layer of a network slice can be seen as a process to identify **the compulsory functions** as **vertices** in a **graph**, with **logical links** interconnecting them. Hence service layer formation depends on the granularity of EPC function decomposition. The virtualized EPC network functions are provided as **software packages**, associated with templates to specify their deployment and operational requirements, which also contains connectivity, interface and KPIs requirements.
  - **Infrastructure layer** represents the **physical network elements** and resources involved hosting a specific service layer. It contains the **computing resources** (e.g. IT servers in data centers) and **networking resources** (e.g. aggregation switches/edge routers and cables).

    ![image](Week1-2/img/Snipaste_2020-12-03_17-35-56.png)

- The mapping from the service layer to the infrastructure layer is a typical virtual network embedding problem:
  - **First** is from the **virtual functions** to **physical mapping**, which involves the network forwarding elements and computing resource selection (e.g. type of devices and geographical location of these devices). The amount of required resources is dimensioned based on the requirements from service layer. 
  -  **Second** is from the **virtual links** to **physical links mapping**. The reserved physical link bandwidth is also based on the service layer requirements.


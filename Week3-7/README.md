# Mission in these 4 weeks: 
- Research on network slicing security
- Write a working scope of the work (focusing on network slicing security, the general 5g security is not being concerned, if not related)
- Explain the most important part in each article.
- Start working on overleafs 
# Summary on the security aspect of network slicing
## Articles
- [5G Network Slicing: A Security Overview](#5g-network-slicing-a-security-overview-link)
- [5G security recommendations Package 2: Network Slicing](#5g-security-recommendations-package-2-network-slicing-link)
- [Network slicing security: Challenges and directions](#network-slicing-security-challenges-and-directions-link)
- [Pushing Forward Security in Network Slicing by Leveraging Continuous Usage Control](#pushing-forward-security-in-network-slicing-by-leveraging-continuous-usage-control-link)
- [An Intra-Slice Security Solution for Emerging 5G Networks Based on Pseudo-Random Number Generators](#an-intra-slice-security-solution-for-emerging-5g-networks-based-on-pseudo-random-number-generators-link)
- [Security Aspects of 5G for Industrial Networks](#security-aspects-of-5g-for-industrial-networks-link)
## 5G Network Slicing: A Security Overview [Link](https://ieeexplore.ieee.org/abstract/document/9099823)
### Citation
```
@ARTICLE{9099823,
  author={R. F. {Olimid} and G. {Nencioni}},
  journal={IEEE Access}, 
  title={5G Network Slicing: A Security Overview}, 
  year={2020},
  volume={8},
  number={},
  pages={99999-100009},
  doi={10.1109/ACCESS.2020.2997702}}
```
### Note
- The network slicing security could be investigate from three prespective: **the life cycle of a network slice**; **intra-slice security**; **inter-slice security**.
- A logical network is a set of network function instances on top of physical and virtual resources.

![image](/Week3-7/img/Snipaste_2020-12-13_10-59-29.png)

- **SLICE LIFE CYCLE**
  - _PREPARATION_
     - Designing, creation, and modification of **network slices templates**. 
     - A **network slice template** is a description of **components**, **structure** and **configuration** of a slice.
  - _INSTANTIATION, CONFIGURATION, AND ACTIVATION_
      - The **resources** and **network functions** are created, installed, and configured. 
      - The slice is built from the **template**, installed, configured, and activated.
  - _RUN TIME_
  - _DECOMMISSIONING_
      - The resources and network functions are now freed. 
- **SLICE LIFE-CYCLE SECURITY**

  ![image](/Week3-7/img/Snipaste_2020-12-13_11-14-04.png)

  -  _PREPARATION PHASE_
      - A **poorly designed**, **tampered** with or **improperly** implemented network slice **template** affects all the slices built from it. 
      - **Content exposure** might also disclose sensitive information.
      - _Mitigation_:  Cryptographical protocols;  Real-time security analysis.
  - _INSTALLATION, CONFIGURATION, AND ACTIVATION PHASE_
      - Creating fake slices
      - Changing the configuration of slices
      - API
      - _Mitigation_: access and operational rights for APIs;  auditing, monitoring, and reporting securely(API)
  - _RUN-TIME PHASE_
      - Denial of Service (DoS)
      - Performance attacks
      - Privacy breaks
      - API
      - _Mitigation_:  authenticity and integrity verification for the network slice
  - _DECOMMISSIONING PHASE_
      - Exposing sensitive data
      - Consume resources improperly 
      - _Mitigation_: destruction of sensitive data;  de-allocation of network functions and resources
- **INTRA-SLICE SECURITY**

  ![image](/Week3-7/img/Snipaste_2020-12-14_15-37-16.png)
    - _5G CUSTOMER DEVICES_
        - **Unauthorized** access to slices or services.
        - Consumption of **resources**--DoS attacks
        - _Mitigation_: strong **authentication** and **access control** for 5G customer devices.
    - _SLICE-SERVICES INTERFACE_
        - Attacking a service and  damaging other services running over the same slice.
        - _Mitigation_:  A correct level of **isolation** must be implemented among the services and between the slice and the consuming services.
    - _SUB-SLICES_
        - Both the **sub-slices** themselves and the **interconnection** between the sub-slices represent attack points. 
        - The overall level of security in a chain of sub-slices is given by the **weakest** subslice.  
        - _Mitigation_: securing the subslices and implementing mechanisms to decrease risks at interconnection.(especially non-3GPP access)
    - _SLICE MANAGER_  
        - **Slice templates**, **APIs**, **access rights**, **mutual authentication** 
        - _Mitigation_: **tenants** should be prevented access to any requests, data, resources, and functions other than the ones agreed by **legal** **means**
    - _RESOURCES AND NETWORK FUNCTIONS_
        - **physical attacks**, **software attack**s, and more general **cyber-attacks**.
        - _Mitigation_: **mutual authentication**, **secure boot**, **credential access**, **physical security**, and **integrity verification**.
- **INTER-SLICE SECURITY**

  ![image](/Week3-7/img/Snipaste_2020-12-14_16-00-54.png)

  - _5G CUSTOMER DEVICES_
      - A security threat appears when a customer device authorized to access one slice might try to gain access to **another unauthorized slice**.
     - Adversarial device might damage the performance by **excessively** consuming **shared resources** in the slice it is **authorized** to access.
      - A **performance attack** can facilitate other types of attacks by **preventing** the slice to **perform security protocols** at the required level because of a **lack of resources**. 
     - The device, which attach to several slices simultaneously, leaks sensitive data from the moresecured slice to the less-secured slice.
     - _Mitigation_:  **proper isolation** between slices, , in terms of **access control**, **confidentiality**, **integrity**, **authenticity**, and **resource consumption**; The resources should be configured to guarantee their **availability** for **running security mechanisms** and also avoid DoS.
  - _SERVICE-SERVICE COMMUNICATION_
     - by attacking some services, an adversary might damage **other** services that run **on top of other slices.**
     - _Mitigation_: proper isolation; Traffic and behavioral analysis; anomaly detection; Traffic isolation(defining flow rules to prevent slice trespassing )
  - _INTRA-SLICES AND INTRA-SUB-SLICES COMMUNICATION_
      - An adversary might try to attack a **less-secured **slice (in particular the **RAN sub-slice**) to attack a **more-secured slice**.
      - _Mitigation_: proper isolation(if one slice is compromised, this should not affect in any way other slices.);  cryptographic parameters (e.g., cryptographic keys) should never be shared between slices; If the keys from the primary **authentication** are used within the slices, **new** and **independent** keys must be generated for **each slice** by using a **key derivation function**
  - _MANAGEMENT SYSTEMS_
     - A tenant might try to access other tenants’ slices or change parameters shared among slices belonging to different tenants.
     - _Mitigation_: proper **isolation**; **restriction** to perform changes on **parameters** shared among slices belonging to different tenants
  - _RESOURCE INFRASTRUCTURE_
     - an adversary might access and tamper **code** in one slice, causing changes in execution in all slices that use **the same code**
     - _Mitigation_: code protection techniques and code isolation.
  - Slices with **a significant difference** in **security levels** should not **share** resources or network functions

## 5G security recommendations Package 2: Network Slicing [Link](https://www.ngmn.org/publications/5g-security-recommendations-package-2-network-slicing.html)
### Citation
```
[]NGMN Alliance. 5G Security Recommendations Package #2: Network Slicing. NGMN; 2016. https://www.ngmn.org/fileadmin/user_upload/ 160429_NGMN_5G_Security_Network_Slicing_v1_0.pdf. Accessed April 1, 2019.
```
### Note
- **_Key Issue 1: Controlling Inter-Network Slices Communications_**
    - While not a concrete entity but rather a** logical grouping** of inter-working components (functions, etc.), a network slice will have an overall **ingress/egress communication** on the **user-plane**.  
    - In addition, both **network slices** and their **components** will have signaling and management plane **communications** requirements (with each other, and with elements such as an orchestrator).
    - We should protect against their **disruption** and ensure that there are no **undesired communications**     
    - Recommendations: 
        - All communications between slices and functions should have a mechanism to control their transmission and receipt, in order to ensure operation within expected parameters and security.   
        - For all **interfaces** between slices and functions, consider defining security mechanisms to ensure operations within expected parameters and security needs of the operator
- **_Key Issue 2: instantiation time **Impersonation** attacks against Network Slice **Manager** or **Host** (physical) platforms within an operator network_**
    - How does the **Network Slice Manager** know that the **host platform** on which a network slice is to be run is an operator **authorized** platform?
    - How do the **host platforms** know that the **Network Slice Manager** with which they are interacting has been granted appropriate **authority** by the operator?
        - Recommendations: Network Slice Managers and host platforms should support **mutual authentication**. Specifically, **Network Slice Managers** should **authenticate** the **host platforms** in the networks they control on which they want to load network slice instances.** Hosts platforms** should also authenticate the **Network Slice Manager** before allowing the instance of the network slice to be loaded.
- _**Key Issue 3: Impersonation attacks against a Network Slice instance within an operator network**_
    - Imagine the need to add **subscriptions** to an already deployed network slice instance. How can the Network Slice Manager guarantee that the correct and **authorized** instance of a given network slice is being provisioned?
    - This problem is made more difficult to address due to the possibility that virtual elements that run within the slice **might have moved** and/or might have been **destroyed** and **replaced** by a newly created instance of an equivalent element type. 
    - This could have happened for non-malicious purposes.
    - Recommendations: All virtual functions to be contained within a Network Slice instance need to be authenticated and their integrity verified.
- _**Key issue 4: Impersonation attacks against different Network Slice Managers within an operator network**_
    - In this scenario the manager in, say physical network “A, would need to create a portion of the network slice instance to be loaded on host platforms deployed **in the other physical network** “B”. The network slice manager for physical network “B” would need to request and receive permission to accomplish this task (loading a network slice instance on a host platform). How can the network slice manager for physical network “A” trust that his negotiations are not taking place with an impostor manager?
    - Recommendations: Network slice managers within an operator network need to **mutually authenticate** each other (directly or transitively) before any negotiation among them can be carried out.
- _**Key Issue 5: Different security protocols or policies in different slices**_
    - If **different slices** are offering **different services**, then those services may have **different performance constraints**, and/or **different security requirements**. 
    - It is natural to expect that security mechanisms will **vary** somewhat **between slice**s – different **“tuning”** of **security protocols** (such as frequency of re-authentication), or possibly even **different protocols**.
    - However, where security varies between slices, we need to consider how well those slices are **isolated** from each other. If someone can attack the “**lower security slice**”, can they then also impact the “**higher security slice**”?
    - We also need to consider the security of the network **as a whole**: if someone can attack a “**lower security slice**”, can they impact **the whole network**?
    - Recommendations: 
        - Demand a baseline security level in all slices:
            - in standards, a security protocol should not be accepted for one slice if it would be considered **unacceptably weak for 5G as a whole**;
            - in network configuration, security parameters (such as authentication frequency) should not be set **lower** in any one slice than would be considered **acceptably secure for the network as a whole**
        - Adequate isolation of slices with different security levels:
            - working within constraints only in slices **that need them**, rather than forcing the resulting security compromises on all slices;
            - the **isolation** between those slices should be at least **as strong as** the difference between **security levels**(it should always be more feasible for an attacker to target the “higher security slice” directly rather than trying to attack it via the “lower security slice”.)
        - Separate **authentication** of a UE accessing multiple slices at once:
            - If an UE can access multiple slices **simultaneously**, and those slices have **different security levels** with respect to network access, then the operator policy should request the UE to **(re)authenticate** **separately** for each slice.
            - Otherwise the UE may authenticate itself to the “lower security slice” and thus be allowed access to the “higher security slice”.
- _**Key Issue 6: Denial of service to other slices**_
    - By **exhausting resources** in one slice, an attacker may **exhaust resources** common to **multiple slices**, and hence cause **denial of service** or service degradation in other slices too.
    - The same concern applies if resources in the first slice are exhausted **not by a deliberate DoS attack**, but just **by accident or chance**. 
    - Note: resources common to multiple slices: hardware-level resources/ network functions
    - Recommendations: When designing the systems that allocate network resources to individual slices:
        - At least, **capping resources for individual slices**, so that each such slice is allowed at most a prescribed **maximum level of resource**.
        - Optionally **ring-fencing resources** for individual slices, so that each such slice is guaranteed a prescribed **minimum level of resource**.
- _**Key Issue 7: Exhaustion of security resources in other slices**_
    -  suppose that the attacker can **exhaust resources** in slice B, in a **targeted** (and perhaps carefully timed) way, with the result that **slice A** **is short of resource** and **unable** to run its **normal security protocol**; now, perhaps, **the attack in slice A can succeed**.
    - Recommendations: Ring-fence network resource for security protocols
- _**Key Issue 8: Side channel attacks across slices**_
    - **Side channel attacks** are a class of attack on implementations of cryptography. They occur when an attacker can learn something about cryptographic secrets by **observing or influencing the platform** on which the crypto code is running.(Examples might be observing the power consumed when the code runs, or observing the time that the code takes to run – possibly while influencing other inputs or running other code so as to influence the contents of the cache, or while somehow inducing faults on the platform.)
    - Suppose that slices A and B share some underlying hardware. If an attacker can observe or influence how code runs in functions in slice A, she may be able to affect the running of code in functions in the slice B machine, or (more importantly) extract information about the running of code in slice B.
    - Recommendations:
        - **the strength of isolation** of **virtual machines**: observing or influencing how code runs in **one** virtual machine should not allow an attacker to influence or deduce anything about how code runs in **another** virtual machine on the same hardware.
        - The second is to** avoid co-hosting** on the same hardware slices that have **very different levels of sensitivity**, or very different levels of vulnerability to influence by an attacker.
-  _**Key issue 9: Hybrid deployment models**_
    - some network functions might not be virtualized (e.g. HSS/AuC)
    - Recommendations: The 5G architecture should ensure that such deployments** maintain the same (or better) 5G security.**
- _**Key issue 10: Sealing between slices when the UE is attached to several slices**_
    -  a UE could be attached to several slices, which have **various level of sensitiveness**. If there is no separation **in the UE** between data communicated via different slices to and from the UE, then the value of separating between slices on the network side could be reduced.   For example, a UE may receive **sensitive data** via **one slice** and then publish that data **via another slice.**
    - Recommendations: Security mechanisms to address this should exist **in the network** and could also potentially **exist in the UE**.
## Network slicing security: Challenges and directions [Link](https://onlinelibrary.wiley.com/doi/10.1002/itl2.125)
### Citation
```
@article{https://doi.org/10.1002/itl2.125,
author = {Cunha, Vitor A. and da Silva, Eduardo and de Carvalho, Marcio B. and Corujo, Daniel and Barraca, Joao P. and Gomes, Diogo and Granville, Lisandro Z. and Aguiar, Rui L.},
title = {Network slicing security: Challenges and directions},
journal = {Internet Technology Letters},
volume = {2},
number = {5},
pages = {e125},
keywords = {network slicing, nfv, sdn, security},
doi = {https://doi.org/10.1002/itl2.125},
url = {https://onlinelibrary.wiley.com/doi/abs/10.1002/itl2.125},
eprint = {https://onlinelibrary.wiley.com/doi/pdf/10.1002/itl2.125},
abstract = {Network slicing emerges as a key technology in next generation networks, boosted by the integration of software-defined networking and network functions virtualization. However, while allowing resource sharing among multiple tenants, such networks must also ensure the security requirements needed for the scenarios they are employed. This letter presents the leading security challenges on the use of network slices at the packet core, the solutions that academy and industry are proposing to address them, pointing out some directions that should be considered.},
year = {2019}
}
```
### Note
- it is important to define the expected **initial isolation level** (eg, security) as well as designing **dynamic isolation mechanisms** that can enforce the isolation level of any given service. 
- Traditional security principles:
    - **Confidentiality**: packets are not made available outside of the slice that generated them; the data carried in those packets or held within the network functions (NFs) that process them must **not be available** to anyone other than **the authorized elements or end users**.
    - **Authentication**: When an **OSS/BSS** interacts with the **NSM**, both parties must be able to **verify** and **authenticate** themselves **mutually**. 
    - **Authorization**: **End users** may only be allowed to interact with slices that the slice owners **have granted access to**; **Slice owners** must manage only **their own slices**(or allowed ones); **Infrastructure** providers must have **full control** over the **NSM** and **the accounting of slices. **;The **NSM** has **full control** over the **network slice instances (NSIs)** and their **NFs**; The **NFs** have **control** over the **resources** and **data** that are provided to them.
    - **Availability**:  This means that the **NSM** and **NFs** must **remain accessible at all time**, while the **slices and application part** of the NFs must be accessible **as long as the contracted infrastructure resources are not exceeded**; The** processing and response times** must remain **under the threshold** as specified in the service-level agreement.
    - **Integrity**: the system must **not be able to be subverted**, either by tampering with data or by replacing its functionality; only **slice** **owners** may change the application part of their **NFs**, define what is the **flow processing** within the slices, or change the **interslice configurations**;** Cross-talk **between slices **cannot be allowed**, **interslice communications** must **only** happen through their respective **interfaces**.
- Network slicing defenses against the security threats:

  ![image](/Week3-7/img/Snipaste_2020-12-23_12-10-24.png)
- Related reference:

4. _Kotulski Z, Nowak TW, Sepczuk M, et al. Towards constructive approach to end-to-end slice isolation in 5G networks. EURASIP J Inf Secur. 2018(2):1-23; 2018_
7. _Mareca P, Bordel B. An intra-slice chaotic-based security solution for privacy preservation in future 5G systems. In: Rocha A, Adeli H, Reis L, Costanzo S, eds. Advances in Intelligent Systems and Computing. Vol 746. Cham, Switzerland: Springer; 2018:144-154._
8. _Bordel B, Orue AB, Alcarria R, Rivera S-dD. An intra-slice security solution for emerging 5G networks based on pseudo-random number generators. IEEE Access. 2018;6(March):16149-16164._
9. _Ni J, Lin X, Shen X. Efficient and secure service-oriented authentication supporting network slicing for 5G-enabled IoT. IEEE J Select Areas Commun. 2018;36:644-657._
10. _Liu J, Zhang L, Sun R, Du X, Guizani M. Mutual heterogeneous signcryption schemes for 5G network slicings. IEEE Access. 2018;6:7854-7863_
11. _Ehrlich M, Wisniewski L, Trsek H, Mahrenholz D, Jasperneite J. Automatic mapping of cyber security requirements to support network slicing in software-defined networks. Paper presented at: Proceedings of the 22nd IEEE ETFA; IEEE Industrial Electronics Society; 2017; Limassol, Cyprus_
12. _Canella C, Van Bulck J, Schwarz M, et al. A systematic evaluation of transient execution attacks and defenses. arXiv 1811.05441, 2018._
13. _Hutchins EM, Cloppert MJ, Amin RM. Intelligence-driven computer network Defense informed by analysis of adversary campaigns and intrusion kill chains. Paper presented at: Proceedings of the 6th International Conference on Information Warfare and Security; 2011; Washington DC.__

## Pushing Forward Security in Network Slicing by Leveraging Continuous Usage Control [Link](https://ieeexplore.ieee.org/abstract/document/9161997?casa_token=MfJfFwxovQoAAAAA:aFQoeqNQ4KCDNFqADV9_iaS7l-Y3O1cX3uOHGWaQ-4A9m8pOH21MO6heffjR472h-rkYsGFPXA)
### Type: Core slicing security
### Citation
```
@ARTICLE{9161997,
  author={B. {Martini} and P. {Mori} and F. {Marino} and A. {Saracino} and A. {Lunardelli} and A. L. {Marra} and F. {Martinelli} and P. {Castoldi}},
  journal={IEEE Communications Magazine}, 
  title={Pushing Forward Security in Network Slicing by Leveraging Continuous Usage Control}, 
  year={2020},
  volume={58},
  number={7},
  pages={65-71},
  doi={10.1109/MCOM.001.1900712}}
```
### Note
- The security of NFV resources and network slices that are managed and orchestrated by MANO platforms can be addressed through the **automation of security management functions** in order to allow network operators to keep up with the extreme dynamicity and complexity of NFV deployments.
- **security functions** are being more and more implemented and deployed as **virtualized security functions**
- the possibility to **monitor** and **orchestrate** VNFs and NSs allows quick detection of anomalous behaviors and promptly taking adequate countermeasures
- Within **ETSI**, an initiative is undergoing to extend the **NFV MANO** architecture with a **security life cycle management module**, namely **NFV Security Manager (NSM)**, supposed to interwork with the MANO functions and in charge of reacting to the internal and external events that might prevent secure network services operation in NFV environments.
- _** security-as-a-service**_
- **ONAP**(Open Network Automation Platform) features a generalized closed-loop process enabling **real-time reactions** to user-specified actionable events.
- The **NSM** scope of operation should be broadened in terms of both **involved entities** and **time span** in order to address an **end-to-end** security vision in highly changing scenarios of users, resources, and services
- NSM security contexts in NFV deployments.
  
  ![image](/Week3-7/img/Snipaste_2020-12-23_16-22-36.png)
- _**Usage Control (UCON)**_
   
    ![image](/Week3-7/img/Snipaste_2020-12-23_16-26-16.png)
    - **Pre-policy**: evaluated and enforced at the time the access is requested.
    - **Ongoing-policy**: enabling the prompt detection of improper or malicious usage of resources from users.
    - Usage Control Systems (UCS) is a software platform implementing a UCON-based authorization system as an extension of the XACML standard.The UCS is highly configurable in terms of policy specifications, attribute sources, and countermeasures specifcation.
    - in the **access control phase**, the NSP may want to:
        - Prevent untrusted verticals (i.e., with low reputation) being granted slice services.
        - Limit the number of slices granted to a vertical.
        - Impose that a frewall is specifed by the vertical as a constituent logical network function of the slice.
        - Regulate the level of VNF control and management capabilities assigned to the vertical based on its role.
        - **Pre-policy**: A vertical V can be granted a slice if (the number of slices already running for that vertical is less than S) AND (the vertical reputation rank is above a given threshold R) AND (the slice includes a VNF implementing a frewall) AND (the vertical role is equal to “bronze” AND the requested level of management and control capabilities is basic) OR (the vertical role is equal to “gold” AND the requested level of management and control capabilities is “advanced”)
    - During the **usage control phase**, the NSP may want to:
        - Prevent untrusted verticals (i.e., with degraded reputation) to keep using the slice.
        - Impose that the vertical uses encrypted communication channels to/among VNFs featuring at least a given level of encryption strength in order to have communications protected at all levels.
        - Impose limitations on the kind of ports that VNFs expose to the Internet (e.g., HTTPS only ) to reduce the attack surface
        - Maintain the integrity of the VNF software in order to avoid intrusions in the slice and hence set up a periodic check of the software integrity status of VNFs in order to detect any kind of corruption or presence of a virus.
        - Promptly detect intrusions, attempts at traffic or data modifications, or attacks with signaling ﬂooding and replaying through a NIDS embedded at the slice level. 
        - _Ongoing-policy_: A vertical V can run a slice as long as (the vertical reputation rank is above a given threshold R) AND (the encryption level on all the slice connections is higher than or equal to EL) AND (the integrity level of the VNFs belonging to the slice is higher than a threshold IL) AND (the time elapsed from the last integrity check on the slice components is less than AT) AND (a network intrusion attempt has not been observed) AND (the VNFs in the slice expose services on HTTPS ports only).
- **Workﬂow of UCON in the NFV MANO framework:**
  
  ![image](/Week3-7/img/Snipaste_2020-12-23_16-40-53.png)
  - Steps 1 and 2 describe the normal workﬂow in current MANO platforms.
## An Intra-Slice Security Solution for Emerging 5G Networks Based on Pseudo-Random Number Generators [Link](https://ieeexplore.ieee.org/abstract/document/8315003)
### Type: RAN slicing security
### Citation
```
@ARTICLE{8315003,
  author={B. {Bordel} and A. B. {Orúe} and R. {Alcarria} and D. {Sánchez-De-Rivera}},
  journal={IEEE Access}, 
  title={An Intra-Slice Security Solution for Emerging 5G Networks Based on Pseudo-Random Number Generators}, 
  year={2018},
  volume={6},
  number={},
  pages={16149-16164},
  doi={10.1109/ACCESS.2018.2815567}}
```
### Note
- (Almost unable to read because the lack of knowledge on cryptography. This article might be useful in future work)
## Security Aspects of 5G for Industrial Networks [Link](https://www.5g-acia.org/fileadmin/5G-ACIA/Publikationen/5G-ACIA_White_Paper_Security_Aspects_of__5G_for_Industrial_Networks/5G-ACIA_WhitePaper_Security_Aspects_of_5G_for_Industrial_Networks_Download.pdf)
### Citation
```

```
### Note
- When the **UE** is **authenticated** by the network upon initial access, a set of **NSSAI** (network slice selection assistance information) items denoting what is **permissible** is sent back to the UE.
- The serving network also receives a copy of the NSSAI which the UE is **entitled to access.**
- It is also possible for the NSSAI to be concealed, and therefore not exposed in the radio layer, if it is considered sensitive.
- **EAP**: 
    - When the UE is **authenticated** for network access, the serving network and the UE receives a list of **permitted network slices**, indicated by their **NSSAIs**.
    - The permitted network slices may further require **slice-specifc authentication** by the slice Authentication, Authorization and Accounting (**AAA**) function.
    - This additional slice-specifc authentication is indicated by the **UE subscription information**.
    - If it is the case, the Access and Mobility management Function (**AMF**) in the serving network triggers the **EAP** authentication procedure for slice-specifc access.



















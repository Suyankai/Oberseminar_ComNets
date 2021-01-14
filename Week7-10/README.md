# Mission in these 4 weeks:
- Introduction of STRIDE
    - Basic concept
- Research of DoS
    - What is DoS?
    - How does it occurs?
- DoS on a NS
    - As detailed as possible
    - Analysis of every aspect.(Starting from the initiation of a NS)
- Simulate/Emulate(if time allowed)
# Summary of the related papers
## The threats to our products [Link](https://adam.shostack.org/microsoft/The-Threats-To-Our-Products.docx)
### Citation
```
@ARTICLE{stride,
  author={K. {Loren} and G.{Praerit}},
  journal={Microsoft Interface}, 
  title={The threats to our products}, 
  year={April 1, 1999},
  volume={},
  number={},
  pages={},
  doi={}}
```
### Note
- **S.T.R.I.D.E.** stands for:
    - Spoofing of user identity
    - Tampering with data
    - Repudiability
    - Information disclosure (privacy breach)
    - Denial of Service (D.o.S.)
    - Elevation of privilege
- The security of the entire system typically is no better than its **weakest** link. Finding and improving such weak links is how threat analysis helps improve the security of our products and services
- **Spoofing of user identity**
    - Breaching the user's authentication information. 
    - In this case, the hacker has obtained the user's personal information or something that enables him to replay the authentication procedure.
    - _Features_:
        - Ability to change the identity associated with an object.
        - Subversion of secure logon mechanism.
        - Successful use of false credentials.
- **Tampering with data**
    - **Modifying** system or user data with or without **detection**. An unauthorized change to stored or in-transit information, formatting of a hard disk, a malicious intruder introducing an undetectable network packet in a communication, and making an undetectable change to a sensitive file are all tampering threats.
    - _Features_:
        - Modification of data that should not be accessible.
        - Causing a trusted entity to modify data improperly.
        - Elevation of privilege can enable tampering.
- **Repudiability**
    - An **untrusted** user performing an **illegal** operation without the ability **to be traced.** Repudiability threats are associated with users (malicious or otherwise) who can deny a wrongdoing without any way to prove otherwise.
    - _Features_:
        - Way to avoid logging of important security event.
        - Spoofing can be used to conceal the identity of the agent performing an action.
        - Tampering with security log can result in repudiability.
- **Information disclosure (privacy breach)**
    - **Compromising** the user's private or business-critical **information**.
    - Note that this threat differs from a **spoofing** threat in that here the perpetrator gets access to the information **directly** rather than by having to spoof a legitimate user.
    - _Features_:
        - Access to data that is considered private and should be protected.
        - Sniffing data in a network or that has been left inadvertently in storage.
        - Protocols or interfaces that improperly reveal user identity, location, passwords, and so on.
        - Spoofing or elevation of privilege can enable an attacker to access private data.
- **Denial of Service (D.o.S.)**
    - Making the system temporarily **unavailable** or **unusable**.
    - We must protect against certain types of D.o.S. threats for improved system **availability** and **reliability**.
    - _Features_:
        - Processing: consumption of CPU cycles by infinite or very long programmatic looping.
        - Storage: large allocation of memory or file quota that blocks legitimate use of the same.
        - Excessive and unwanted use of screen space, printer paper, and so forth.
        - Causing a crash or error mechanism that interferes with normal usage or that requires restarting.
        - Elevation of privilege can exacerbate D.o.S. by gaining larger resource quotas.
- **Elevation of privilege**
    - An unprivileged user gains **privileged access** and thereby has sufficient access to **completely** compromise or destroy the entire system. 
    - _Features_:
        - Improperly gaining unrestricted rights (becoming a "administrator").
        - Running untrusted data as native code in a trusted process, such as by buffer overrun.
        - Spoofing identity to gain access to resources not otherwise available.
## Towards constructive approach to end-to-end slice isolation in 5G networks [Link](https://link.springer.com/article/10.1186/s13635-018-0072-0)
### Citation
```
[]Kotulski, Z., Nowak, T., Sepczuk, M. et al. Towards constructive approach to end-to-end slice isolation in 5G networks. EURASIP J. on Info. Security 2018, 2 (2018). https://doi.org/10.1186/s13635-018-0072-0
```
### Note
- The slicing concept itself is a source of security issues. 
- Adding special properties to slices (isolation, protection, etc.) might create new attack methods by exploiting weakness of an isolation providing system to reach resources assigned to another slice with better parameters in order to lower costs or to intercept sensitive data stream.
- Therefore, a network slice instance can be shared with multiple service instances provided by the network operator. 
- Isolation may be achieved by different means, including[42]:
    - Language-based isolation (type systems, certifying compilers);
    - Sandbox-based isolation (Instruction Set Architecture, Application Binary Interface, Access Control List);
    - Virtual machine (VM) based isolation (Process VM, Hypervisor VM, Hosted VM, Hardware VM);
    - Operating system (OS) kernel based isolation;
    - Hardware based isolation;
    - Physical isolation.
-  The slice chaining concept:
    - ![image](/Week7-10/img/Snipaste_2021-01-14_20-04-20.png)
- The isolation of the slices can be considered in at least four areas:
    - _Isolation of traffic_: all slices use the same network resources, so the network slices should ensure that data flow of one slice does not move to another.
    - _Isolation of bandwidth_: all slices allocate some bandwidth and should not utilize any bandwidth assigned to other slices. Thus, it is required to ensure the isolation of bandwidth on the links and nodes CPU, storage, or network capacity.
    - _Isolation of processing_: while all virtual slices use the same physical resources, a proper processing of packet is required, which will be independent of all other slices.
    - _Isolation of storage_: data related to a slice should be stored separately from data used by another slice
-  NPT system within 5G ecosystem: logical view
    - ![image](/Week7-10/img/Snipaste_2021-01-14_20-07-50.png)

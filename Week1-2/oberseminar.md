# Oberseminar

## Topic: Security Aspects of 5G Network Slicing  

## Task Description 

Network slicing is a part of the current research and will be integrated in the new 
5G standard. It should help to guarantee network parameters such as latency 
and throughput. 5G campus networks are small, independent cellular networks targeted for large 
industry companies, e.g., car manufacturers. In this scenario, network slices must 
be separated from each other, so that no data on one slice can be intercepted on 

The task of this project is 
- research about (5G) network slicing, focus on security aspects: scientific documentation of your results 
- investigate possible attack vectors, explain and discuss findings, e.g., with existing tools
- demonstration of a proof-of-concept attack 

## Contact

- topic taken by: Yankai Su, Yankai.Su@mailbox.tu-dresden.de

## Timeline

- Report Hand-in until: end of lecturing period

## Report

- report preferably in LaTex on [TUD-Overleaf](https://tex.zih.tu-dresden.de/) 

- more information on ComNets [webpage](https://cn.ifn.et.tu-dresden.de/teaching/materials-and-tools/)
- 15-25 pages, counting only _real_ content
- module mark M = (2 * M1 + M2)/3; M1 = report, M2 = 20 minutes presentation

## Meetings

### 2020-11-25

ToDo: 

- topic introduction:
  - What is network slicing (in general)? What does it mean in the context of 3GPP, especially from the rel. 15 and newer? :arrow_forward: literature research, e.g., 3GPP technical reports, research paper (IEEE Xplore, Google Scholar), etc. :arrow_forward: short survey (first without focus on security)
  - 3 parts: RAN, transport, core slicing :arrow_forward: focus on RAN and core slicing 
  - next step: security parameters of network slicing, especially from 3GPP/5G
- attack vector investigation:
  - possible methods: threat modeling ([STRIDE](https://en.wikipedia.org/wiki/STRIDE_(security))), brain storming (How can the system be attacked? Where does data flow? :arrow_forward: interfaces)
  - explain findings (possible attacks): Why is that a problem? Possible attack? Mitigations?
  - Pick **one** attack! Describe in detail (e.g., path/methods to exploit in vulnerability, involved protocols, etc.); **HINT:** It is not necessary to find a new, yet undiscovered exploit - an existing tool is sufficient!
- work presentation:
  - 20min presentation
  - If a (live) demonstration is not possible due to, e.g., complex testbed setup, a theoretical approach is fine - an implementation is preferred though.
- timeline:
  - 120 working hours
    - 50 hours research
    - 40 attack vector investigation
    - 30 work presentation
  - until next time (~ 2020-12-09): 
    - introduction for you: https://www.youtube.com/watch?v=A5_LVYaOhZo
    - start with LaTex, tools, research search machines 
    - Which did papers did you read? Content? Preferably already documented as draft
    - first start in 3GPP technical reports: [Link](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=3144), click on tab _Versions_, download a release by clicking on the version :arrow_forward: see section 5.15 ​
# Week 7

### Grading

Task #|Points|Description|
-----|:---:|----------|
[Task 1](#task-1-safety-concerns) | 1 | Safety Concerns
[Task 2](#task-2-static-and-dynamic-analyzers) | 1 | Static and Dynamic Analysers 
[Task 3](#task-3-security-certification) | 1 | Security Certifications
[Task 4](#task-4-nis2--red) | 1 | NIS2 & RED
[Task 5](#task-5-showcase) | 1 | Showcase

**(4 POINTS MAXIMUM FOR THIS WEEK)**

---

# Tasks

### Task 1: Safety Concerns

In terms of medical equipment and automotive industry mentioned in the Lecture 13, consider the following: 

- Why are new safety concerns sometimes overlooked? 
- What are events that trigger sudden change? 

250 words **maximum**, cite if you use external sources 

[Security Engineering Lecture 13: Safety and Security](https://www.youtube.com/watch?v=uZkQtnHKcJ4) 
In both the medical equipment field and the car industry, safety issues often get missed or pushed aside. This happens because of complexity, money pressure, and also because big institutions don’t like to change fast. Ross Anderson in Security Engineering points out that both areas now depend a lot on embedded systems and networked software, but they don’t always use the strong engineering practices that older safety-critical industries had. For example, medical devices sometimes reuse old code with bugs or don’t get tested enough, especially when companies rush them to market. Cars have the same problem—braking or steering is now software-driven, and when subsystems interact in strange ways, new risks can appear that engineers didn’t expect.
Regulation is not always fixing this. In the U.S., the FDA’s 510(k) process lets medical devices get approved just by showing they are similar enough to older ones, which means deeper safety checks can be skipped. In the auto industry, cost cutting or delaying recalls—like the GM ignition switch case—has meant that safety fixes often come only after accidents already happened.
Usually, big changes only come after something goes wrong in public. Famous cases like the Therac-25 radiation overdoses or the Jeep Cherokee hack in 2015 forced both industries to react—through recalls, lawsuits, and new safety standards. Anderson calls these focusing moments, when suddenly visibility and liability push companies to act fast.
Sources:
Anderson, R. (2020). Security Engineering (3rd ed.).
Greenberg, A. (2015). Hackers Remotely Kill a Jeep on the Highway. Wired.

---

### Task 2: Static and Dynamic Analyzers

Explain the difference between static and dynamic analyzers. Explain what the advantages are of using these tools during production.  Pick one of the Static or Dynamic testing methods mentioned in the Lecture 14 and write a brief description of it. 

250 words **maximum**, cite if you use external sources 

[Security Engineering Lecture 14: Assurance and Sustainability](https://www.youtube.com/watch?v=cmWQF2FDlG8) 
Static and dynamic analyzers are both important tools but they work in different ways. Static analyzers look at the code without running it. They try to find things like buffer overflows, insecure API calls or logic errors just by scanning the source or binaries. Since they run before deployment, they can catch problems earlier and also across large codebases. Dynamic analyzers are different, they only work when the program is actually running. They watch the execution and can find memory leaks, race conditions, or strange behaviors that don’t show up until the system is live.
Using these tools in production has many advantages. Static analysis makes fixing bugs cheaper because issues are spotted before release. Dynamic analysis gives more real insight into how the system behaves under real workloads. When used together, they help companies follow regulations, improve reliability, and lower the chance of big failures. They also help with sustainability, since they keep systems safer not only at launch but also later in their lifecycle.
One static testing method mentioned is code review with automated static analysis tools. In this method, automated tools scan the code and highlight possible vulnerabilities. Then developers check those results to see if they are real problems or just false alarms. This mix of automation and human review gives both efficiency and accuracy. By putting this into the development pipeline, organizations can improve code quality and reduce the chance of exploitable flaws ending up in production.

---

### Task 3: Security Certification

Consider the different incentives (both 'Good' and 'Bad' incentives) for Security Certification of a product from the following points of view:

- Potential End User/Buyer of the product 
- Certifying authority (both vendor funded and non-profit) 
- Manufacturer/designer of the product 

400 words **maximum**, cite if you use external sources 

**(EXPLANATIONS)**

- Vendor funded = Applicant pays the certifying authority for the certification process 
- Non-profit = Applicant does not have to pay directly for the certification process 


[Security Engineering Lecture 15: Governance and Regulation](https://www.youtube.com/watch?v=PdMzMHizEaE) 
[Security Engineering Lecture 16: Ian Levy, NCSC - Protecting a country for fun and profit](https://www.youtube.com/watch?v=qv6SS5FhdUk) 
 
Security certification is meant to give confidence that a product meets some safety or security standards. But the truth is, the incentives for different groups are mixed, and this can bring both good outcomes and also some problems.  
End Users/Buyers: 
For buyers, certification is useful because it shows the product has been checked by someone outside the company. This lowers uncertainty and makes it easier to compare products. The good incentive here is trust—certification makes the product look reliable and saves time on checking everything yourself. The bad side is that users might think certification means “perfectly safe,” when in reality it often just means the product passed a minimum bar. Like Ross Anderson says, sometimes certification ends up more like a tick-box exercise than a real proof of resilience.  
Certifying Authorities:
- Vendor-funded: Their main incentive is money, since vendors pay them. The good part is that fees can support skilled staff and detailed testing. The bad part is conflict of interest—if they are too strict, vendors might go elsewhere, so there is pressure to approve things fast or easy. This can lead to rubber-stamping.  - Non-profit: Their incentive is credibility and public trust. The good side is independence, since they don’t rely on vendor money. But the bad side is limited resources, which can mean slower reviews or outdated standards.  
Manufacturers/Designers: 
For manufacturers, certification is a way to stand out in the market. The good incentive is that it pushes them to follow better engineering practices and improve long-term security. The bad incentive is that some companies only aim to meet the lowest requirement, not to really improve. Sometimes they even push for weaker standards to save cost. Ian Levy points out that governance often struggles when business incentives are stronger than security needs.  

---

### Task 4: NIS2 & RED

There are currently three European Union Directives that will affect current and future products and services. These Directives are:
- Cyber Resilience Act (CRA)
- Radio Equipment Directive (RED)
- Revised Directive on Security of Network and Information Systems (NIS2)

Traficom has collected information regarding all three quite concisely providing a good starting point for familiarizing on the subject
- (CRA) https://www.kyberturvallisuuskeskus.fi/en/toimintamme/saantely-ja-valvonta/kyberkestavyyssaados-cyber-resilience-act-cra
- (RED) https://traficom.fi/en/news/new-information-security-requirements-eu-improve-information-security-wireless-devices
- (NIS2) https://www.kyberturvallisuuskeskus.fi/en/our-activities/regulation-and-supervision/nis2-european-union-cybersecurity-directive

**PICK ONE, Either CRA, RED or NIS2 and answer the following questions**  
- Concisely explain the main goal of the directive? The main goal of NIS2 is to achieve a high common level of cybersecurity across the European Union. It aims to strengthen the resilience and incident response capabilities of both essential and important public and private sector entities.
- Which types of products does it concern? NIS2 is not a product-focused directive like the CRA or RED. It is an organizational security directive. It concerns the services provided by entities in critical sectors, not individual physical products.
- Which types of organizations does it concern? It concerns "essential" and "important" entities across many sectors. In Finland, this includes energy, transport, banking, financial market infrastructures, healthcare, drinking water supply, digital infrastructure (like IXPs and DNS providers), public administration, and certain manufacturing sectors like medical devices.
- What kind of cybersecurity measures have to be implemented for a product/organization to comply with the directive?Compliance requires the implementation of a range of measures based on a "think-tank, do-bank" principle. These include risk analysis, incident handling, business continuity, supply chain security, basic cyber hygiene practices, encryption, and access control measures.
- When (Date) do organizations/products need to comply with the directive?EU Member States, including Finland, had to transpose the directive into national law by October 17, 2024. The provisions and supervision of entities apply from that date.
- What are possible penalties?Penalties are significant to ensure compliance. They can include administrative fines of up to €10,000,000 or at least 2% of the total global annual turnover of the preceding financial year, whichever is higher.
- Your own thoughts: How does this benefit you/society overall. Are there positive and negative aspects? This greatly benefits society by making critical services (like power, water, and healthcare) more resilient to cyberattacks, protecting our societal backbone and economy. It creates a unified, higher baseline for cybersecurity across the EU and forces crucial organizations to take proactive steps, reducing the risk of major disruptive incidents. The compliance burden on organizations, especially smaller ones, is substantial. There is also a risk of it becoming a bureaucratic, checkbox exercise if not implemented with a genuine focus on security outcomes rather than just paperwork.

**You can answer directly to each bullet point with few sentences**  


--

### Task 5: Showcase

Choose a Cybersecurity tool of your choice and answer the following questions about it.

Pick a new tool that has not been featured in the course, so the following are forbidden from this task: (Threat Dragon, Nmap/Zenmap, Wazuh, thc-hydra, BurpSuite, Trivy, Hadolint, Falco)

- Name of the tool: OSQuery
- Link to the tool website/repository:https://osquery.io
- Free or Paid tool? Free
- When was the tool created and by who? Originally created by Facebook (now Meta) in 2014.
- Is the tool Open Source? Yes, it is fully open source under the Apache License.
- What is the tool used for? OSQuery is used for endpoint visibility and security monitoring. It lets you query your operating system as if it were a database, using SQL-like queries to pull information about processes, users, network connections, installed software, and more.
- What are its capabilities?Real-time monitoring of system activity,Detecting anomalies such as unauthorized processes or changes in configuration, Collecting forensic data for incident response, Integrating with SIEM (Security Information and Event Management) tools, Cross-platform support (Windows, macOS, Linux)
- Who would most benefit from this tool?Security teams, system administrators, and incident response teams in medium to large organizations. It’s especially useful for enterprises that need visibility across thousands of endpoints.
- What kind of use case could you yourself have for this tool?I could use OSQuery to monitor my own workstation for suspicious activity for example, checking if unknown processes are running, or if new software was installed without my knowledge. It would also be handy for learning how attackers might move laterally in a system, since I could simulate queries that detect unusual logins or privilege escalations.


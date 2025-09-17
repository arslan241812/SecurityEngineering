# Week 2

### Grading

Task #|Points|Description|
-----|:---:|----------|
[Task 1](#task-1-choose-a-or-b) | 1 | Browsers and Banking Security ***or*** Certifcates
[Task 2](#task-2-cards-and-payments) | 1 | Cards and Payments
[Task 3](#task-3-card-fraud) | 1 | Card Fraud
[Task 4](#task-4-wazuh) | 1 | SIEM Wazuh 

---

# Tasks

### Task 1: Choose A ***or*** B

#### Task 1A: Browsers and Banking Security

Online Banking is of the most lucrative targets for phishing and scams. How do our browsers protect us against them?

Look at the following snippets from a browsers address bar:

![Bank image 1](https://github.com/ouspg/SecurityEngineering/blob/main/Week2_Banking_and_Payments/Images/bank_1.png)

![Bank image 2](https://github.com/ouspg/SecurityEngineering/blob/main/Week2_Banking_and_Payments/Images/bank_2.png)

![Bank image 3](https://github.com/ouspg/SecurityEngineering/blob/main/Week2_Banking_and_Payments/Images/bank_3.png)

**Questions:**

- What does the "Not Secure" warning mean in the first picture and what risks does visiting sites with the warning pose? This means the website is using the old HTTP protocol instead of the secure HTTPS protocol and the connection between website and webbrowser is not encrypted.
- Why does the second site show up as "trusted" to the browser? The second site shows up as  trusted because it uses HTTPS and has a valid SSL/TLS certificate.
- What other ways are there to detect a phishing/scam site? There are many ways to detect a phishing scam i.e, Check for misspellings (danskebankk), wrong top-level domains (.io instead of .fi), or subdomains,awkward layouts,lack of professional standards, suspicious links and wrong contact information 
    - Are there any tools available online? yes there are some tools where you can detect this like Google Safe Browsing Transparency Report,VirusTotal and WHOIS Lookup Tools 
- What is typosquatting and how does it relate to the pictures?Typosquatting is a method where scammers register domain names that are intentional misspellings of popular websites. In first picture there is danskebankk.fi - Uses a common typo: double "k" while in Picture 2 danskebank.io - Uses a different top-level domain (.io instead of .fi)
    - What is **UDRP** and how does it help with combatting typosquatting? UDRP stands for the Uniform Domain-Name Dispute-Resolution Policy. It is a process for resolving disputes over the abusive registration of domain names. A owner like Danske Bank can file a UDRP complaint against someone who has registered a domain name in bad faith (e.g., danskebankk.fi).
    - If you were to own the domain **ouspg.org** and would be running your crypto banking application at **bank.ouspg.org**, what domains could you monitor for warning signs of possible phishing attempts against your customers? I should  monitor for those domains that could be used in phishing attacks against my customers like ouspgg.org, ouspb.org, ouspg.net,bank.ouspg.com, bank.ouspg.net,bank.secure-ouspg.org


#### Task 1B: Certificates

You have probably seen the following kind of warning when browsing the internet:

![Certificate image 1](https://github.com/ouspg/SecurityEngineering/blob/main/Week2_Banking_and_Payments/Images/certificate_1.png)

**Questions:**

- What are digital certificates used for?
    - Why are certificates important for online payments and banking security?
    - What other uses do certificates have?
- What kind of attacks does TLS mitigate and why is this important for online banking?
- How do browsers use certificates for ensuring browsing security?
    - What does the warning in the picture above mean?

**Certificate Authorities**

Read the following entries on Certificate Authorities and Certificate Transparency and answer questions:

https://en.wikipedia.org/wiki/Certificate_authority  
https://en.wikipedia.org/wiki/Certificate_Transparency  
https://certificate.transparency.dev/howctworks/  
https://www.ecb.europa.eu/pub/pubbydate/html/index.en.html  

**Questions:**

- Why would it be bad if a trusted certificate authority was compromised?
- Why is certificate transparency important?

---

### Task 2: Cards and Payments

**Read the following:**

https://en.wikipedia.org/wiki/Payment_card  
https://en.wikipedia.org/wiki/EMV  
https://en.wikipedia.org/wiki/Multi-factor_authentication  

**Questions: Payments**

- Why do modern payment cards use a chip and not a magnetic stripe? The shift from magnetic stripes to EMV chips  is  due to a massive increase in security.This makes cloning EMV chip cards extremely difficult and effectively killed the widespread fraud caused by skimming and counterfeit cards at physical terminals.
- What are EMV Certificates and why are they relevant for payment protection? EMV Certificates are digital passports issued by a trusted Certificate Authority. The main types are Issuer Certificates and Payment System Certificates and they build trust in payment protection.
- What attacks exist against payment cards?
    - Card-not-present?  There are two types of possible attacks  1. (Skimming): Copying data from the magnetic stripe to create a counterfeit card for use on non-EMV terminals (e.g., in other countries)  2.(Relay Attacks): Intercepting the communication from a contactless card and relaying it to a terminal elsewhere to make a fraudulent payment.
    - Contactless payment? There are some possible attack like Eavesdropping: The wireless signal could be intercepted, but the short range (a few cm) and encryption make this very difficult to exploit in practice. Stolen Card:If a card is lost or stolen, someone could use it for multiple small contactless payments (which often don't require a PIN) until it is reported and blocked.

**Questions: MFA**

- How is multi-factor authentication (MFA) used in banking? Banks use MFA to verify that a user attempting to access an account or authorize a transaction is genuinely the same person. It is typically use for: Logging into online or mobile banking, Adding a new payee or beneficiary to a transfer list.Confirming a high-value or suspicious transaction and Changing contact details or passwords.
- How does multi-factor authentication increase payment security? MFA increases security by requiring evidence from multiple factors like Password, PIN, Phone, Bank card, Fingerprint and Face ID.
- What MFA methods are you using in you daily life? I am using all of the above mentioned factors for high level of security
- What attacks exists against different forms of 2FA?
    - Time-based-one-time-password? Phishing (Real-time):A fake login site captures the user's password and their current TOTP code. Man-in-the-Middle: Intercepting communication between the user and the legitimate service to capture the credentials and the 2FA code
    - Text Message? SIM Swapping: An attacker transfers the victim's phone number to a SIM card in their possession. This allows them to receive all SMS-based 2FA codes. Device Theft: Simply stealing the victim's phone to receive the code.

---

### Task 3: Card Fraud

One part of understanding payment card security is monitoring how the cards are used for frauds. The following articles are reports on card fraud by the European Central Bank and will give you an overview of how the fraud landscape has evolved between 2008-2019. Read through the articles and then answer the questions in the questions section.

**Read the following reports:**


https://www.ecb.europa.eu/pub/pdf/cardfraud/cardfraudreport201207en.pdf  
https://www.ecb.europa.eu/pub/cardfraud/html/ecb.cardfraudreport202008~521edb602b.en.html  
https://www.ecb.europa.eu/pub/cardfraud/html/ecb.cardfraudreport202110~cac4c418e8.en.html  

**Supporting Resources:**

https://www.ecb.europa.eu/pub/pubbydate/html/index.en.html (Search: "Fraud")  
https://www.ecb.europa.eu/paym/intro/mip-online/2018/html/1803_revisedpsd.en.html  


**Questions:**

Write a summary (max 700 words) on "Evolution of card fraud" in which you answer **at least** the following questions:

- What kinds of card fraud exist?
    - How does card fraud type prevalence differ geographically?
- How has the fraud landscape changed between 2008-2019? Why?
    - What type of fraud has seen a notable increase during the last decade?
    - What technologies or regulations have had an impact on card fraud?
- How has the transaction landscape changed in the same period?
    - What kind of transactions have become increasingly popular?
    - What kind of transactions have had a high risk of being fraudulent?
        - Has this changed at all during 2008-2019?
- What effect has internet and e-commerce had on card fraud?
- Why is preventing data breaches important in preventing card fraud?
    - How does payment card tokenisation help in this?
-Anything interesting you found?
Card frauds cagorized into two categories: card-present (CP) and card-not-present (CNP) fraud. CP fraud includes activities like using cloned or skimmed cards, lost or stolen card fraud, and fraud involving card theft at ATMs or point-of-sale (POS) terminals. CNP fraud occurs in transactions where the physical card is not required, such as online purchases, phone orders, or e-commerce transactions. Other specific types include identity theft, phishing scams, account takeovers, and friendly fraud.
Card fraud trends vary according to the region. Europe has a sharp decline in CP fraud due to the widespread adoption of EMV (chip) technology and regulatory measures like the Revised Payment Services Directive. In contrast, North America has the highest share of CNP fraud by value  partly due to higher data breach rates and slower EMV migration initially . Latin America and Asia-Pacific also experienced rising CNP fraud, driven by rapid e-commerce growth and less mature fraud prevention infrastructure.
Between 2008 and 2019, the fraud landscape shifted to CNP fraud. This change was largely driven by the global rollout of EMV chip technology, which made counterfeiting cards extremely difficult. The rise of e-commerce, which increased opportunities for CNP fraud. Regulatory interventions, such as the implementation of Strong Customer Authentication (SCA) under PSD2 in Europe, which reduced CNP fraud by requiring multi-factor authentication for online transactions. By 2019, CNP fraud accounted for 84% of total card fraud value, while CP fraud declined significantly.
Over the last decade, CNP fraud has seen the most significant increase. This is directly linked to the growth of online shopping, which expanded the attack surface for fraudsters. Types of CNP fraud that grew include: Phishing and social engineering scams. Account takeovers (ATO), where fraudsters gain access to user accounts. Friendly fraud (chargeback abuse).
Key technologies and regulations that reduced fraud includes, EMV Chip Technology: Reduced counterfeit card fraud by generating dynamic transaction codes,
Strong Customer Authentication (SCA): Mandated under PSD2, requiring multi-factor authentication for online payments in Europe,AI and Machine Learning: Used for real-time fraud detection and risk scoring.
The transaction landscape evolved significantly during this period because E-commerce transactions became increasingly popular, with global sales rising from $1.3 trillion in 2014 to $4.2 trillion in 2021 also Contactless payments gained traction, though they introduced new risks like relay attacks while Cross-border transactions grew, accounting for 63% of card fraud value by 2021 due to varying security standards across regions.
Transactions with the highest fraud risk are Card-not-present (CNP) transactions,Cross-border transactions and high-value purchases. The risk shifted from card-present environments to card-not-present environments due to the increased availability of stolen card data from data breaches.
The internet and e-commerce revolutionized card fraud by enabling CNP fraud on a global scale and facilitating data breaches and the sale of stolen card information on dark web marketplaces. it also introduced new fraud tactics  where fraudsters set up fake e-commerce sites to do fraud easily.
Preventing data breaches is critical because breaches expose sensitive card data which fuels CNP fraud. Stolen data can be used for identity theft and account takeovers. Breaches fade consumer trust and lead to financial losses for businesses.
Tokenization helps mitigate fraud by replacing sensitive card details with unique, randomized tokens that are useless if stolen.Enhancing security for recurring payments and digital wallets without adding friction.
my interesting findings from this are
1. Friendly fraud (chargeback abuse) accounts for 61% of all chargebacks and is a growing problem for merchants .
2. Biometric authentication (e.g., via FIDO standards) is emerging as a more secure alternative to passwords .
3. AI-powered fraud detection systems can reduce false declines and improve real-time decision-making .
4. Despite advancements, social engineering (e.g., phishing) remains a highly effective tactic for fraudsters .

---

### Task 4: [Wazuh](https://www.wazuh.com)

---

> **note**
> Task tested to work on v4.9.0, written and designed on v4.5.1. v4.9 has a couple of known issues with details being unable to be read from events. If you face issues, fallback to e.g v4.5.1, which still works.

---

Wazuh is an free and open source "unified XDR and SIEM protection for endpoints and cloud workloads." In this task we are going to focus more on the [SIEM](https://www.gartner.com/en/information-technology/glossary/security-information-and-event-management-siem) side of things. Take a look at their [website](https://wazuh.com/platform/siem/) and [github](https://github.com/wazuh/wazuh) to familiarize yourself with the capabilities and features Wazuh SIEM offers.

Start of with deploying the Wazuh [single-node on Docker](https://documentation.wazuh.com/current/deployment-options/docker/wazuh-container.html). You should go through the documentation to understand what's going on, but the following commands should be enough:

```console
git clone https://github.com/wazuh/wazuh-docker.git -b <VERSION NUMBER e.g v4.9.0 or v4.5.1>
cd wazuh-docker/single-node
docker-compose -f generate-indexer-certs.yml run --rm generator
docker-compose up -d
```

You can access the Wazuh (WUI)WebUI at your localhost, to do this go to [https://localhost](https://localhost). By default Wazuh uses self signed certs and you won't be directed to the site directly, instead click the advanced tab and find the button for "Accept the risk and continue". This will direct you to the site, and from then on you should be able to use it normally.

Next deploy an agent or agents. You can deploy the agent(s) on your own platform(server, desktop, etc...) or the course virtual machine. For the course virtual machine use the "installation from source" --> "installing Wazuh agent from sources". Arch linux, the course VM uses pacman for package management so you could use that. [Installation alternatives](https://documentation.wazuh.com/current/deployment-options/wazuh-from-sources/wazuh-agent/index.html) in the documents.  

For other environments, find the appropriate [installation documention](https://documentation.wazuh.com/current/installation-guide/wazuh-agent/index.html), many can be installed in the Wazuh WUI(Web User Interface), for windows, choose windows and fill out the details, run the command and start the agent. For the ip address of the server, you can use your internal ip address.

Create a directory named integrity and add a file to it, then enable FIM(File Integrity Monitoring) on your agent(s) on that folder, you should also set the scan frequency at around 60 seconds, so you won't have to wait for the events. 

You are to trigger the FIM with atleast two different events. Then answer the questions below.

**What to return:**
1. What rule descriptions did you get?
2. What are the MITRE ATT&CK techniques(include ID) Wazuh reports for these events?
3. What is the reported MITRE techniques for deleting files or directories inside monitored directories?
4. Explain in your own words where, when and why should these systems be used, would they be helpful in banking.
5. FIM is critical because it is sensitive for Data Protection because banks handle highly sensitive customer data, financial records, and transaction logs and unauthorized changes to these files could lead to data breaches, fraud, or financial loss. other standards like PCI DSS require file integrity monitoring to ensure cardholder data environments are secure. Integrating FIM with active response can reduce the time to mitigate threats, which is crucial in fast-moving banking environments.

### Feedback
Be sure to give feedback on these tasks. Do you feel these to be the kind of skills you might need or want?
really impressive to do these task. a bit complicated in terms of execution but overall good experience.

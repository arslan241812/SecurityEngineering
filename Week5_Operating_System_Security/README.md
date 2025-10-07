# Week 5

### Grading

Task #|Points|Description|
-----|:---:|----------|
[Task 1](#task1-bring-your-own-devices) | 1 | Bring Your Own Device
[Task 2](#task2-attacks-on-cpu-execution) | 1 | Attacks on CPU Execution
[Task 3](#task3-securing-os) | 1 | Securing OS
[Task 4](#task4-logging) | 1 | Logging 

---

# Tasks

### Task1: Bring your own devices

Following link containing NIST:s [security recommendations for workplace bring your own device](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.1800-22.pdf). On the page 12 is listed following 9 threat events, and your job is to make one A4 sized poster or otherwise shortly summarize what each listed threat event means based on the document or your own research.

- Intrusive application practices
Apps you install can access more data than needed (contacts, location, files) and may share it with third parties, potentially exposing sensitive work information. there is high risk of data leakage, surveillance, or misuse of personal/enterprise info.

- Account credential theft through phishing
Fake emails or texts trick you into entering your work username and password on a fraudulent website, giving attackers direct access to company systems.we can mitigate this by training users to recognize phishing and use multifactor authentication (MFA) or deploy email filtering.

- outdated phones
Using a device with an old operating system means known security vulnerabilities are not patched, making it easy for attackers to compromise the device and its data.

- Sensitive data transmissions
Sending work data over unencrypted networks (like public Wi-Fi) allows eavesdroppers to intercept and read confidential information. mitigation is possible by enforcing VPN use, apply TLS/HTTPS and disable public Wi-Fi access for work apps.

- Brute-force attacks to unlock a phone
   An attacker with physical access to your device can use automated tools to guess your passcode through repeated attempts, gaining full access.mitigation require strong passcodes,automatic lockout enable mode or data wipe after failed attemptsand by using  biometric unlock.
  
- Application credential storage vulnerability
  Work applications that store your login credentials in an insecure way can be exploited by malware, leaking your corporate account details. Use of secure app frameworks, encrypt credentials and vet app security before deployment can mitigate it.
  
- Unmanaged device protection
  If your personal device isn't properly enrolled in the company's management system, it lacks essential security policies, making it a weak link in the corporate defense. there is risk of no enforcement of policies, encryption or remote wipe.
- Lost or stolen data protection
  A lost or stolen device that isn't protected by a strong passcode and encryption gives anyone who finds it immediate access to all its corporate data. By enforcing full-disk encryption,enable remote locate/wipe and educate users to report loss immediately can mitigate this.
- Protecting enterprise data from being inadvertently backed up to a cloud service
  It means personal cloud services may automatically back up work files where it is no longer under the company's control or protection.

---

### Task2: attacks on CPU execution
spectre and meltdown are two original side channel attacks discovered in 2017 that target cpu, and over the years more have been discovered. [This wikipedia article](https://en.wikipedia.org/wiki/Transient_execution_CPU_vulnerability) list some of them. Pick 3 of them to research about how exactly each exploits the system,their differences, which systems they targeted and how they can be mitigated. 

Answer in max 300 words. You are free to use tables or otherwise make to comparison easier to read if you wish.
Here is a concise comparison of three recent transient execution speculative side-channel attacks beyond Spectre/Meltdown.
1.Foreshadow (L1 Terminal Fault):
This attack exploits a race condition in the L1 Data Cache during speculative execution. It tricks the CPU into speculatively accessing memory that should be protected, such as inside SGX enclaves, before the permission check is complete. The result transiently leaks this data into the L1 cache, where it can be extracted. It has targeted primarily Intel CPUs with SGX (Software Guard Extensions) which is a secure area for isolating sensitive code and data. Later variants also affected non-SGX systems. They mitigated it in sucha way that microcode updates to flush the L1 cache when entering and exiting secure enclaves. OS patches to address the broader vulnerability. Ultimately requires disabling Hyper-Threading for full protection.
2. ZombieLoad:
A Microarchitectural Data Sampling (MDS) attack that targets CPU internal buffers like the Line Fill Buffer. When a CPU core encounters a fault or misspeculation,transient operations can leave data in these buffers. ZombieLoad exploits this to sample and leak data that other applications, operating systems or even secure enclaves were using on the same physical core.It targets a wide range of modern Intel CPUs of various generations with simultaneous multithreading.
Mitigation of this includes Microcode updates that implement "Verw" instruction-based buffer clearing. OS kernels were patched to use this instruction during context switches. The most robust mitigation is disabling Hyper-Threading.
3.CacheOut (L1D Eviction Sampling):
This attack is also another MDS attack but it specifically targets the L1 Data Cache (L1D). The attacker uses eviction techniques to force the CPU to transiently move a victim's secret data from the L1 cache into a vulnerable internal structure, from which it can then be sampled. This allows leakage of OS kernel data,Co resident virtual machines data. this attack affects Intel CPUs from Skylake through Cascade Lake (2015–2019 era) while AMD CPUs are not affected. It requires local code execution because it not remotely exploitable by itself. The same microcode updates and "Verw" instruction mitigations used for ZombieLoad and other MDS attacks. It also relies on the same principle of clearing CPU buffers to prevent data sampling across security domains.

---

### Task3: Securing OS
Following is a list of some of the more common vulnerabilities and attack vectors existing in operating systems.  

- Malware and Viruses:it Can corrupt files, steal sensitive data, slow down the system or even take control of the system. Windows Defender provides real time protection. In addition Windows has a firewall and SmartScreen to block malicious apps and websites. In windows its Primarily built-in (OS function) but third-party antivirus software can be used.

- Exploiting Software Vulnerabilities:Attackers can run arbitrary code, escalate privileges, or cause a system crash. Windows update automatically delivers security patches. The OS also includes Address Space Layout Randomization (ASLR) and Data Execution Prevention (DEP) to make exploitation harder. function includes OS function (patch management and built-in security features).

- Phishing and Social Engineering: These attacks trick users into revealing passwords, financial information or installing malware. Windows includes SmartScreen in Edge and Explorer to warn about malicious websites and files. However, the primary mitigation is user education and external tools like browser extensions and email filters.Funtions are the combination of OS built-in browser protections and external tools third-party email clients and security awareness.
- Drive-by Downloads:The attack is unintended download of malware by visiting a compromised website. Windows Defender and SmartScreen help block malicious downloads and websites. Additionally, keeping the browser and plugins updated via Windows Update reduces vulnerabilities.
  
- Zero-Day Exploits: Attacks that exploit unknown vulnerabilities therefore no patch is available and it leads to potential system compromise.Windows Defender Advanced Threat Protection (ATP) can use behavior-based detection to block suspicious activities. Also, EMET (Enhanced Mitigation Experience Toolkit) and its successor, Windows Defender Exploit Guard, provide additional security mitigations (like ASLR, DEP, Control Flow Guard) to make exploitation harder.

- USB/Removable Media Attacks: Malware can spread via USB devices or maliciously crafted USB devices can exploit the OS (e.g., BadUSB).Windows can be configured via Group Policy to restrict USB device usage (e.g., write protection, or disabling auto-run). Windows Defender can scan removable media.
  
- Password Cracking:it is an unauthorized access to user accounts and sensitive data in which attackers guess, steal or brute-force credentials to access systems.Windows uses strong password policies (enforced via Group Policy) and supports multi-factor authentication. It also stores passwords in a hashed format (NTLM or Kerberos) and has account lockout policies to prevent brute-force attacks.

Make short write up about each that answers following questions 
1. What harm can it cause to you?
2. How OS of your choosing (Windows, Mac, Linux) can mitigate it?
     - Function of the OS itself or external tools?


---

### Task4: Logging
Log files are records of events or actions that occur in a system, application, or program. Logs are essential for troubleshooting, debugging, and analyzing the behavior of software or hardware.

Find answers to following questions:
1. What kind of information would be saved into following types of log files
- Application logs:These logs record events related to a specific application. This includes errors, warnings, informational messages, user actions, and application-specific events. For example, a web server log might record HTTP requests, response codes, and client IP addresses.
- Event logs: Event logs typically capture system-wide events, such as user logins, system startups and shutdowns, security-related events (like failed authentication), and hardware issues. In Windows, this is centralized in the Event Viewer.
- Service logs:These logs are generated by system services or daemons. They include details about service startups, stops, errors, and performance metrics. For example, a database service log might record queries, connections, and failures.
- System logs:System logs cover operating system events, such as kernel messages, device drivers, system errors, and hardware events. They provide a broad view of system health and operations.

2. Where in each of the common Operating Systems those logs would be stored (Windows, Mac, Linux(changes per distro so provide in answer which you are using)
(Windows)
Application Logs: Stored in the Event Viewer under "Applications and Services Logs" or in specific application directories. For example, IIS logs are in C:\inetpub\logs\.
Event Logs: Primarily in the Event Viewer (e.g., Security, System, Application logs). The files are stored in C:\Windows\System32\winevt\Logs\.
Service Logs: Often in Event Viewer under "Services" or in log files within the service's installation directory.
System Logs: In Event Viewer under "System" or in files like C:\Windows\System32\config\systemprofile.
Mac (macOS):
Application Logs: Located in /Library/Logs/ for system-wide apps or ~/Library/Logs/ for user-specific apps.
Event Logs: macOS uses the Unified Logging System, accessible via the log command or Console app. Logs are stored in a binary format in /var/log/ and private databases.
Service Logs: Located In /Library/Logs/ or /var/log/ for system services.
System Logs: Located In /var/log/ files like system.log, kernel.log, etc.
Linux (OS Ubuntu):
Application Logs: Typically located in /var/log/ with specific files like /var/log/apache2/access.log for Apache.
Event Logs: Often handled by syslog or rsyslog and stored in /var/log/syslog, /var/log/messages.
Service Logs: Located In /var/log/ for services like mysql, nginx, etc.
System Logs: Located In /var/log/syslog, /var/log/kern.log for kernel messages, /var/log/auth.log for authentication.
4. What kind of threats could you notice by monitoring each log file?
Application Logs: Unusual errors, frequent crashes, which might indicate bugs or attacks like injection attempts.
Event Logs: Multiple failed logins (brute-force), new user creations or privilege escalations.
Service Logs: Unexpected service stops or restarts which could be due to exploits or denial-of-service.
System Logs: Hardware failures or kernel errors which might suggest hardware issues or low-level malware.
6. How would you go about monitoring logs on your personal computer?
I would use Event Viewer to browse logs. For real-time monitoring, use of  PowerShell scripts or third-party tools like Splunk or LogRhythm to automate log collection and analysis.

remember to list sources for information you use!
https://docs.microsoft.com/en-us/windows/win32/eventlog/event-logging
https://support.apple.com/guide/console/welcome/mac
https://help.ubuntu.com/community/LinuxLogFiles
https://graylog.org/post/how-to-read-log-files-on-windows-mac-and-linux/
https://hogonext.com/how-to-detect-and-mitigate-security-threats-using-log-analysis/

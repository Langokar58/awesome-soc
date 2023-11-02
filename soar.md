# SOAR: Table of content

* What is SOAR?
* Simple and commonly needed automation tools
* Common automations


## What is SOAR?

As per [Gartner definition](https://securityboulevard.com/2021/08/gartner-soar-magic-quadrant-when-where-and-how/):

![image](https://user-images.githubusercontent.com/16035152/186781422-ebb3996a-da66-4d27-a55f-6065fa84fca5.png)

Hence 3 critical tools (see above): SIRP, TIP, SOA, on top of SIEM.

And in my view, SOAR is more an approach, a vision, based on technology and processes, than a technology or tool per say. 


## Simple and commonly needed automation tools

* Online automated hash checker (script):
  * my recommendation: [Munin](https://github.com/Neo23x0/munin), or with PowerShell [Posh-VT](https://github.com/darkoperator/Posh-VirusTotal)

* Online URL automated analysis:
  * my recommendation: [CyberGordon](https://cybergordon.com/), [URLScan.io](https://urlscan.io/)

* Online automated sample analyzer:
  * my recommendation, via script and without sample submission: [Malwoverview](https://github.com/alexandreborges/malwoverview);
  * my recommendations for online dynamic analysis: [Hybrid-Analysis](https://www.hybrid-analysis.com/), [Joe's sandbox](https://www.joesandbox.com/#windows)

* Offline automated sample analyzer:
  * My recommendation: [Qu1cksc0pe](https://github.com/CYB3RMX/Qu1cksc0pe)

* (pure) Windows tasks automation:
  * My recommendations: [AutoIT](https://www.autoitscript.com/site/), [Chocolatey](https://chocolatey.org/)

* SaaS-based (and partly free, for basic stuff) SOA:
  * [Shuffle](https://shuffler.io/)

## Common automations

### My recommendations for detection (alerts handling):

Try to implement at least the following automations, leveraging the SOA/SIRP/TIP/SIEM capabilities:
* Make sure all the context from any alert is being automatically transfered to the SIRP ticket, with a link to the SIEM alert(s) in case of.
  * Leverage API (through SOA) if needed to retrieve the missing context info, when using built-in integrations.
* Automatically query the TIP for any artefacts or even IOC that is associated to a SIRP ticket.
* Automatically retrieve the history of antimalware detections for an user and/or endpoint, that is associated to a SIRP ticket.
* Automatically retrieve the history of SIEM detections for an user and/or endpoint, that is associated to a SIRP ticket.
* Automatically retrieve the history of SIRP tickets for an user and/or endpoint, that is associated to a new SIRP ticket.
* Automatically query AD or the assets management solution, for artefact enrichment (user, endpoint, IP, application, etc.).

### My recommendations for response (incident response, containment/eradication steps):
* Block an IP on all firewalls (including VPN), SWG and CASB.
* Block an URL on SWG. 
* Block an email address (sender) on SEG.
* Block an exe file (by hash) on endpoints (leveraging antimalware/EDR or AppLocker).
* Block an exe file (by hash) on gateways and CASB: SWG, SEG, CASB.
* Reset an AD account password.
* Disable an AD account (both user and computer, since computer account disabling will block authentication with any AD account on the endpoint, thus preventing from lateral movement or priv escalation).
* Report a (undetected) sample to security vendors, via email. Here are a few addresses, in case of: 
  * Files samples (to be attached in a password-protected Zip file, with 'infected' as password): samples@eset.com, newvirus@kaspersky.com, report@sentinelone.com, virus_submission@bitdefender.com, vsamples@f-secure.com, virus_malware@avira.com, submitvirus@fortinet.com, virus_research@avertlabs.com, virus_doctor@trendmicro.com
  * URL/IP samples: samples@eset.com, samples@kaspersky.com, report@sentinelone.com, virus_submission@bitdefender.com, vsamples@f-secure.com, phish@office365.microsoft.com, report@openphish.com, reportphishing@apple.com, abuse@clean-mx.de, datasubmission@mcafee.com
* Report a false positive to security vendors, via email;
  * You may want to have a look at [this page](https://github.com/yaronelh/False-Positive-Center) to know the required email address.
* Report a malicious URL (for instance, phishing) to a security vendor for takedown steps
  * My recommendation: [Netcraft](https://www.netcraft.com/cybercrime/) [via API](https://report.netcraft.com/api/v3), or [PhishReport](https://phish.report/docs).
* Block an IP address on web servers, linux firewalls, etc. based on community-driven CTI:
  * My recommendation: [CrowdSec bouncer](https://www.crowdsec.net/blog/crowdsec-not-your-typical-fail2ban-clone)
  

# End
Go to [main page](https://github.com/cyb3rxp/awesome-soc/blob/main/README.md).
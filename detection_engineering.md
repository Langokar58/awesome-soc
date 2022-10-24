# SOC detection engineering and management

This page deals with SOC detection engineering and management (detection use case creation, detection capabilities assessment, etc.)

# TOC

* Must read
* Generic recommended approach
* PDCA applied to SOC
* How to feed the Plan phase (detection engineering)


# Must read:
* MITRE, [top TTP for ransomwares](https://top-attack-techniques.mitre-engenuity.org/)
* LinkedIn, [Risk assessment with ISO 27005](https://www.linkedin.com/pulse/iso-27005-risk-management-aron-lange/?trackingId=oRjjiIdY9BNjne1ALRq02A%3D%3D)
* Ch33r10, [Enterprise purple teaming](https://github.com/ch33r10/EnterprisePurpleTeaming)
* SIEM rules publications:
  * [Sigma HQ (detection rules)](https://github.com/SigmaHQ/sigma/tree/master/rules) 
  * [Splunk Security content (free detection rules for Splunk)](https://research.splunk.com/) 
  * [Michel De Crevoisier's Git](https://github.com/mdecrevoisier/SIGMA-detection-rules)
* Known exploited vulnerabilities: 
  * [CISA catalog](https://www.cisa.gov/known-exploited-vulnerabilities-catalog)
* Medium, ["About detection engineering"](https://cyb3rops.medium.com/about-detection-engineering-44d39e0755f0)


# Generic recommended approach

## PDCA multi-loop:

As per [Wikipedia](https://en.wikipedia.org/wiki/PDCA#/media/File:PDCA-Multi-Loop.png)
![image](https://user-images.githubusercontent.com/16035152/197550801-47f57a99-8d3b-45b1-9c97-be4355a4d9f0.png)



# PDCA being applied to SOC:

## Plan:

### Sensors:
* Determine which sensors or endpoint/app logs, you miss in terms of detection capabilities
* Determine how to generate and ingest their logs in the SIEM
* Build a projet agenda

### SIEM rules:
* Determine which detection logic you miss, directly in the SIEM;
* Build a project agenda.


## Do:

### Sensors:
* Ingest the logs of the security sensor, or endpoint/app logs, that you previously identified;
* Make sure your data ingestion is compliant with the datamodel you use.


### SIEM rules:
* Create the detection rules (SIEM searches) that match your previously identified needs;
* Create the alert objects in the SIEM or SIRP, to contain the contents of the SIEM searches in case something is found;


## Check:

### Logs:
* Make sure your data ingestion is compliant with the datamodel you use (or, at least, the SIEM one).

### SIEM rules [first run for the assessed detection capabilities]:
* Test the detection logics with narrowed use cases (specific events, generated on demand).

### SIEM rules [following runs for the assessed detection capabilities]
* Assess your detection capabilities with purpleteaming;
* Report your results and findings in purpose-built app like Vectr.

## Act:
* Fix everything that was previously identified as not working, or not matching your needs.


# How to feed the "Plan" phase

## TTP detection priorities identification:
* Use [MITRE Engenuity calculator](https://ctid.mitre-engenuity.org/our-work/top-attack-techniques/):
  * focus on the [top TTP for ransomwares](https://top-attack-techniques.mitre-engenuity.org/): 
    * T1486: Data Encrypted for Impact, T1490: Inhibit System Recovery, T1027: Obfuscated Files or Information, T1047: Windows Management Instrumentation, T1036: Masquerading, T1059: Command and Scripting Interpreter, T1562: Impair Defenses, T1112: Modify Registry, T1204: User Execution, T1055: Process Injection.

## Focus on top relevant vulnerabilities:
- that are confirmed exploited in the wild;
- **AND** that are confirmed as valid (unpatched) within your organization
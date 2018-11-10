---
layout:     post
title:      Firewall Tips and Best Practices
date:       2018-11-10
author:     SecEventsPen
summary:    Firewall Tips and Best Practices
categories: Top Tips
thumbnail:  puzzle-piece
tags:
 - 2018
 - Firewall
 - Best Practices
 - Methodology
 - Tips
---

Once again, its been a while, in fact nearly a year! Trying to keep on top of the blog hasn't really went well with work and family commitments, please accept my apologies!

Anyway moving on, today we have a new post covering an overview of some tips and best practices when it comes to administering/reviewing firewalls as a result of some recent engagement I undertook. The majority of the content below is not new or ground breaking, but comes from recommendations I've made or information I've collected and used as references during my time reporting on firewall reviews. Due to this and my recent work, I thought I'd write up a few things which hopefully help some folks out when it comes to these types of engagements. Possible use cases for the following information could be:

- Provide the following points to non-tech Points-of-Contact or inexperienced firewall admins
- Use sections of this blog post as the basis for recommendations where issues have been identified with the ruleset or ACLs in use.
- Or simply as a refresher for the new or more experiences among us

Enjoy!

**A Simple Guide / Set of Best Practices for Maintaining Firewalls**


The exact procedures for adjusting a firewalls settings will vary depending on the firewall(s), vendor, make and model and whether they are using a hardware or software-based solution; however, regardless of the kind of technology in use, following a simple guide which promotes a 'best practice' methodology when creating or administering firewalls and their corresponding rulesets/ACLs can help maximise the effectiveness of their solution whilst providing a robust security posture.

Again, just to stress, the following content is not original work and has been cobbled together from my own notes, recommendations I've made during firewall reviews and information gathered publicly from the web. All of the following information is or should be common sense and freely available, all I have done is collate what I feel is relevant and compiled it into some logical steps!

**Administering your Firewalls**


The following points aim to underpin a series of best practices or form the basis of a methodology when it comes to administering firewalls and their rulesets/ACLs:

**ALWAYS Document your firewall rules**


Any member of the clients IT security/firewall team should be able to tell very quickly, what each firewall rule is intended to do by looking at documentation associated with that firewall. At a minimum, the client should ideally be keeping a track of the following data:

- The purpose of the firewall rule
- The service(s) it affects
- The users and devices it affects
- The date the rule was added
- When the rule should expire (if it is temporary)
- The name of the person who added the rule

Furthermore, where possible, it is also recommended that the use of 'categories' or 'section titles' are implemented, thus allowing for the grouping of similar rules together. This can be especially helpful when it comes identifying a particular rule and also in determining the logical order for the rules in use or  one thats have been newly created.

*Note: The client, if not already doing so, should implement a process of fine-tuning and optimising their firewall rules. Advise they take time to revisit their existing rulesets/ACLs and make sure that they all have current and relevant documentation for each of them. There is a high chance that certain rules are being followed that were installed by default, without anyone really understanding why they are there or rules that have been around for a long time which may be subverting other network controls and security measures.*

**Establish and Follow a Change Procedure for Firewall Configuration Changes** ***(if not already doing so!)***


Before a client begins to change any of their existing firewall rules, they should establish a formal process that they will use for any modifications, if they do not already have such a process in place. A typical change procedure might involve the following steps:

- A change request process that business users or internal stakeholders can submit in order to ask for alterations to the firewall configuration/ruleset/ACL
- An assessment process with which the firewall team can analyses the risk and determines the best course of action to balance the business/stakeholder users' needs with that of the security needs need to protect the network
- A testing process that ensures that any changes to firewall rules will have the desired effect
- A deployment process for moving the new rule into production after it has been tested
- A validation process to ensure that the new firewall settings are operating as intended
- A documentation process to track the changes that have been made

If the client has a small security team, it might be tempting for them to skip or fast track the above points, or even implement changes less formally; however, following these processes strictly can and will help avoid lapses in the clients rulesets/ACLs and environment security posture caused by poor firewall configuration.

**Review firewall rules regularly**


Networks along with firewall rules can change frequently due to modern technology, network/user requirements, along with gaining new users and new devices whether that be through bring-your-own-devices (BYOD) implementations. Those users and devices will most likely require access to new applications and new services, which have not previously been catered for. This could mean applications, network devices and services, which may have been hosted services internally and accounted for a high percentage of network traffic may now become far less popular and consequently make those previous rules surplus to requirements.

Any of the points highlighted above could very well, and probably will mean, that the client will need to create new, update existing firewall rules or delete firewall rules that are no longer necessary. Points worth noting:

- Advise the client should not delay fixing something until it becomes critically important, firewalls are far too important for a reactive approach.
-	Advise the client not updating their firewall rules under pressure
- Advise the client to schedule regular maintenance and reviews of specific rule sections rather than a full ruleset/ACL. They should aim to find a timeline that works within their business needs and availability.

**Remove unused or overlapping firewall rules**


Once a firewall review schedule has been put in place, a client should go through the list of firewall rules scheduled for review and update that documentation as they go along. This should highlight or indicate any potential issues and consequently they may find that they have an overlap of rules, where one of more rules serve the same purpose. Identifying and eliminate overlapping or duplicate rules can reduce network overheads, workload and ultimately speed up the network or device in question.

Similarly, it is highly plausible that rules in use are never applied because none of the clients traffic meets the specific criteria outlined in those rules. Should this be the case, the client should take into consideration whether the rule is necessary. If not, deleting or at the very least disabling the rule pending further review should be the next logical step for them.

*Note: Disabling rules should only be done for a short period or time and not indefinitely. If a rule is not required, the specific rule should be removed and documented accordingly.*

**Audit the Firewall Logs**


Every firewall comes with built-in reporting tools (these vary depending on the make and model) that provide details about the traffic the firewall manages. Advise the client to auditing those firewall logs regularly to look for changes or anomalies that might lead to or suggest modifications to their current firewall settings/configuration.

The log data generated by the firewall will most likely be a critical source of information about which rules are being invoked most frequently, and which aren't ever being used at all. Both types of information are critical for optimising and refining the firewalls behaviour.

Log data can also help you find "false positives," traffic that should not trigger security rules but is doing so any way. Changing/modifying those firewall rules may help cut down on those false positives and consequently improve service to end users.

*Note: If the client has a particularly large or active network, they may find that they need additional log analysis tools beyond those provided by the firewall manufacturer to make sense of the log data. The more recent advanced firewall reporting tools can include artificial intelligence or machine learning capabilities that can help spot/identify important details that might otherwise have been missed.*

**Organise Your Firewall Rules, This Can Help to Maximise Speeds Across the Network**


Whilst not true of every firewall solution, some firewalls apply rules in the order that they are listed in the firewall configuration or rule base. In short, this means that the firewall will start at the top of the ruleset list and move down until it reaches a rule that would require it to carry out an action for the traffic in question. If none of the rules apply, the traffic will pass through.

*Note: Firewall vendor Checkpoint Software notes [1], "Having the same rules, but putting them in a different order, can radically alter the effectiveness of the firewall. Always place more specific rules first and the more general rules last to prevent a general rule from being applied before a more specific rule."*

Another good practice is to put rules that are invoked more often higher in the ruleset order than rules that are invoked less often. This can have speeds performance increases.

In a recent Sans Firewall Checklist [2], the SANS Institute recommends the following order for rules:

- Anti-spoofing filters (blocked private addresses, internal addresses appearing from the outside)
- User permit rules (e.g. allow HTTP to public web server)
- Management permit rules (e.g. SNMP traps to network management server)
- Noise drops (e.g. discard OSPF and HSRP chatter)
- Deny and Alert (alert systems administrator about traffic that is suspicious)
- Deny and log (log remaining traffic for analysis)


**Traffic Blocking Using Network Devices**


Another way to improve the performance of a clients firewall is to use other network devices with this ability i.e. routers, to handle a portion of the traffic-blocking activities. By offloading some work from the firewall(s), The client may be able to eliminate some firewall rules and consequently improve throughput for their network.

*Note: As with all network changes, ensure this is tested and monitored carefully in a test/low impact environment (where possible) to make sure that the change is having the intended impact and returning the results hoped for.*

**Firewall Software and Firmware Updates/Upgrades**


Infrastructure devices are more commonly becoming the focus for attackers, due to the level of access they would provide should any exploitation be successful. This has been highlighted within the last year or so by the leaking of NSA tools by the ‘Shadow Brokers’ group, which included an exploit for Cisco ASA Firewalls. Since then a lot of work has been published by companies and independent security researchers in relation to firewall evasions and exploitation.

Infrastructure devices, such as firewalls should have their own separate patch management policies and procedures so that updates are regularly installed. Frequent monitoring of the firewalls vendor’s security bulletins can also ensure a quick response to critical issues.
A well-implemented and robust set of firewall rules will not stop an attack on your organisation if your firewall has a known vulnerability that hasn't been patched which consequently allows attackers to take control of this device.

**Communicate with your teams and business**


Finally yet importantly, enforce to your client that they need to communicate with all their business units/internal stakeholders and end users about any changes to the firewall rules. A high-level overview should be more than sufficient for end users, with only in-depth technical oversight being provided to the relevant network and security teams. Getting input from the business can help make sure that the firewall in use and their configuration meets business and end users' needs whilst maintaining a robust security posture.

Opening and maintaining a working dialog with business/internal stakeholders and users can also help them understand the multiple steps and risks involved when they make a request for a change. Promoting a clear and concise change request policy that both technical and non-technical users can understand, along with working together the business can help ensure they are meeting the dual goals of security and service availability.

**Reviewing Firewall Configs, File Formats and Automation**


From the review side of things, as consultants/testers, we ideally want the firewall configurations we'll be reviewing in a manageable format! Having the configs exported into a format that will allow us to automate the initial ruleset review and get a rough idea of what issues we'll be faced with. This should then be followed up by a second more in-depth and focused manual sweep off any issues identified. Being able to automate firewall reviews can save a lot of time and be extremely helpful; however, there is no substitute for manually reviewing the target firewall configuration files and you should not solely rely on tools that automated and produce a report for you.

That said and done, this is where everyones favourite love it or hate it tool, Nipper made by Titania Studios, comes in handy. Nipper parses the majority of vendor firewall configs; however, it's not the be all and end all nor a holy grail of firewall review solution for that matter! Nipper does produce some daft findings and false positives, these can be pain staking to discount when working with large rulesets!

A list of vendors that Nipper currently supports can be found **[here](https://www.titania.com/content/nipper-studio-supported-devices)**

Should a client be using one of the Nipper supported vendor Firewalls then to aid you in getting a Nipper parsable file, the good folks at Titania/Nipper have set up instructions for a list of firewalls which can be followed by the client. This list can be found **[here](https://www.titania.com/support/nipper-studio)**.

Now your client has no reason not to provide you with a file format that makes your life a little bit easier!

If all else fails and it's the "manual review life for you" then you may find Excel with filtering options in use and/or using Grep-fu with regex's is the way to go to aid in identifying issues! I have found myself here more times than I like to remember!

Touching briefly on what you should be looking for, at a minimum, when reviewing a firewall config:

***Permissive Rules - Cleartext Services***

These services (telnet, HTTP, FTP) do not implement any form encryption and therefore, hold a risk to the confidentiality, integrity and availability to any data being transmitted across them.

***Permissive Rules - Service Not Defined***

These rules increase the threat surface of the destination device and therefore increases the risk of a vulnerable service being exposed and exploited.

***Permissive Rules - Any Source***

These rules increase the threat surface of the destination device and therefore increases the risk of a vulnerable service being exposed and exploited. Whilst this level of access may be required, it does increase the potential threat sources for the destination host.

***Permissive Rules - Any Destination***

These rules increase the threat surface of the destination device and therefore increases the risk of a vulnerable service being exposed and exploited.

*Uncommented Rules*

Rules which are missing comments detailing their purposes, whilst this does not pose a direct threat, it does increase complexity of firewall management and increases the probability of accidental firewall rule modification.

***Temporary/Test Rules***

Temporary/Test rules increase the complexity of a ruleset and often do not accurately represent required access, potentially being more permissive than required.

***Disabled Rules***

Disabled rules increase the complexity of the ruleset, and increase the likelihood of accidental activation.

After looking for the above issues, context needs applied to any issues identified, as this will aid in attributing a risk rating to the finding in your report. This can often be difficult as with being a contracted party, we are not likely to have a full in-depth insight needed. If in doubt highlight the issue with your POC directly or in the report and caveat with this particular issue may need further review for reasons a, b and c etc.

*Side Note*

Recently I was provided 3 firewall configs in a PDF format, yup thats right **PDF**. Each of the PDFs contained data tables. After some searching around and a friendly nudge, I ended up using a tool called Tabula, a link to the tool download can be found **[here ](https://tabula.technology)** and the GitHub repo **[here](https://github.com/tabulapdf/tabula)**.

Tabula allowed me to export the data tables contain the firewall rules in to .CSV files, which I then converted to .XSLX files, which allowed me to enable the filtering options. A bit long winded but, this proved to be a better option than reviewing each of the 500 page PDFs.

If you ever find yourself in a similar situation, its worth looking at Tabula to help ease your pain!

**Summary**


So to round things up, we have covered the following areas:

- Documenting Firewall Rules ... ALWAYS
- Change Procedure
- Rule Review
- Removing Rules
- Log Audits
- Organising Firewall Rules
- Traffic blocking
- Firewall Updates/Upgrades
- Communication within your organisation
- Configs and Automation

Hopefully you found the above useful or a nice little refresher!

Well thats it folks… You don’t have to go home, but you cant stay here!

Thanks for reading!!

***References***

[1 - Checkpoint](https://supportcenter.checkpoint.com/supportcenter/portal?eventSubmit_doGoviewsolutiondetails=&solutionid=sk106597)
[2 - Sans FW Checklist](https://www.sans.org/media/score/checklists/FirewallChecklist.pdf)

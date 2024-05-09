---
layout: post
title: 'Protecting Your Business - Ransomware Prevention and Recovery Best Practices'
tags: [Ransomware, Tips, Best Practice]
featured_image_thumbnail: assets/images/posts/ransomware/ransomware.jpg
featured_image: assets/images/posts/ransomware/ransomware.jpg
featured: true
hidden: true
---
Photo by <a href="https://unsplash.com/@jackson_893?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Michael Geiger</a> on <a href="https://unsplash.com/photos/macbook-pro-turned-on-JJPqavJBy_k?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
  

Ransomware attacks have emerged as one of the most significant cybersecurity threats to organisations worldwide, particularly financial institutions, creating substantial challenges for data security and business continuity.

This blog post looks at protecting your business through Ransomware Prevention and Recovery Best Practices.

<!--more-->

These attacks have become a major cybersecurity threat globally, targeting hospital, medical, aviation, Telecoms, financial and professional services systems and networks to exploit vulnerabilities.
  
Lets pick out some key points, according to a **2023** report [from Sophos](https://assets.sophos.com/X24WTUEQ/at/c949g7693gsnjh9rb9gr8/sophos-state-of-ransomware-2023-wp.pdf) "The State of Ransomware":

- **76%** of those who experienced a ransomware event said that, during the most significant attack, the cybercriminals involved successfully encrypted their data.
- **46%** paid the ransom to regain access to their data. However, even after payment, only an average of 63% of the encrypted data was successfully restored.
- **30%** Of ransomware attacks where data was encrypted reported that data was also stolen.
- Emails were the root cause of 30% (approx.) of attacks: 18% started with a malicious email and **13%** with phishing.
- The **mean recovery cost** from a ransomware attack:
	- **$1.82 million** - excluding ransomware payment.
	- **$2.6 million** if paid and got data back
	- **$1.6 million** - costs drop if successfully restoration from backups can be achieved as the primary means of recovery.

As you can see, in today's digital landscape, ransomware attacks continue to pose a significant threat to businesses of all sizes. These malicious attacks encrypt critical data, rendering it inaccessible until a ransom is paid. 

To safeguard your organization against such threats and ensure quick recovery in the case of an attack, it's crucial to implement robust prevention and recovery measures.
## Lets Breakdown a 'Ransomware' Attack
*(... at a high-level)*

So before we talk about protecting your business from ransomware and recovery best practices, let first breakdown a ransomware attack. For this we'll use a well know ransomware and how the attack unfolded.
### Ransomware: WannaCry

**WannaCry** was the first ransomware to exploit the **EternalBlue** flaw in Windows systems. You can find further info about WannaCry from the [US CISA](https://www.cisa.gov/news-events/alerts/2017/05/12/indicators-associated-wannacry-ransomware) & [UK NCSC](https://www.ncsc.gov.uk/guidance/ransomware-wannacry-guidance-enterprise-administrators-1).

_**Note:** Yes, WannaCry, is a good few years old now, given that it happened in 2017; however, it is still one of the most prominent to hit organizations around the globe and caught a lot of orgs out, who thought they were prepared, but weren't._

The U.K.'s National Health Service (NHS) was one of the most prominent WannaCry victims, with multiple hospitals, general practitioners, and pharmacies affected in England and Scotland. NHS facilities were forced to delay and divert medical services.

**Financial Losses:** **£92 million** _(approximately $100 million)_ according to the [National Health Executive](https://www.nationalhealthexecutive.com/articles/wannacry-cyber-attack-cost-nhs-ps92m-after-19000-appointments-were-cancelled):

- **£20m** was lost during the attack mainly due to lost output.
- Followed by a further **£72m** from the IT support to restore data and systems.
- **Impact:** Approx. **19,000 appointment**s being cancelled across the one-week period of the attack.

This was coupled with 24hr news coverage about the attack on the NHS, leading to patient panic, loss of faith in the service, and damage to the NHS brand itself.
### Attack Breakdown

**The Key points:**

- WannaCry exploits a vulnerability in Microsoft's SMBv1 network resource-sharing protocol.
- The exploit let the threat actors (TA) transmit crafted packets to any system that accepts data from the public internet on port 445.
	- SMBv1 is a deprecated network protocol.
	- SMB Should not be exposed to the internet.
- WannaCry appears on computers as a dropper
	- This is a small helper program that delivers and installs malware.
		- Components in the dropper include:
			- An application for data encryption and decryption
			- files of encryption keys
			- A copy of Tor for command-and-control communications.
- WannaCry uses, at the time, a 0day exploit known as 'EternalBlue' to spread.
	- TA first step: search the target network for devices accepting traffic on TCP port 445, indicating the system is configured to run SMB.
	- TA then initiate an SMBv1 connection to the device.
		- Once a connection is made, a buffer overflow is used to take control of the targeted system and install the ransomware component of the attack.
- Once a system is affected, the WannaCry worm propagates itself and infects other unpatched devices
	- All without any human interaction.
- WannaCry encrypts files on the hard drives of Windows devices so users can't access them.
- Ransom payment demanded.
	- A significant flaw was noted with the release of decryption keys:
		- The TA didn't have any way to prove who paid the ransom, resulting in a completely manual process of attribution from the TA to attribute the decryption keys to the correct person/org who had paid.

**Attack Diagram:**

{% include image-caption.html imageurl="assets/images/posts/ransomware/WC-Ransomware-Breakdown.png#wide" title="Ransomware Breakdown" caption="WannaCry Attack Breakdown" %}

### Attack Breakdown Summary

WannaCry ransomware leverages vulnerabilities in Microsoft's SMBv1 network protocol to propagate across networks and encrypt files on Windows devices, demanding ransom payments for decryption.

The attack spreads via crafted packets sent to systems exposed to the internet on port 445, exploiting a buffer overflow to install the ransomware component. Once infected, WannaCry autonomously propagates across unpatched devices, encrypting files without user interaction. 

When we look at this, the UK's NHS, for instance, would have benefited from the following points, which would have ultimately aided in the prevention and/or more efficient recovery from such an attack:

- **Network Segmentation:**
    - Segment networks to prevent SMB traffic exposure to the internet, limiting access to internal systems only.
    - Use firewalls and network security measures to restrict traffic on port 445 and other vulnerable ports.
    
- **Vulnerability & Patch Management:**
    - Regularly update and patch systems to address known vulnerabilities
    - Implement a robust vulnerability & patch management program to ensure timely updates across all devices.
    
- **Disable SMBv1:**
    - Disable SMBv1 protocol on all devices as it is deprecated and prone to exploitation.
    - Use SMBv2 or SMBv3 protocols, which offer improved security features.
    
- **Endpoint Security:**
    - Deploy endpoint protection solutions with ransomware detection and prevention capabilities to detect and mitigate ransomware attacks at the endpoint level.
    - Enable behaviour-based detection to identify and block suspicious activities indicative of ransomware behaviour.
    
- **Backup and Recovery:**
    - Maintain regular backups of critical data stored offline or in secure, isolated environments.
    - Test backup restoration procedures regularly to ensure data can be recovered in the event of a ransomware attack without paying the ransom.

## **The Impact of Ransomware Attacks**

The impact of ransomware attacks on any organisation, though in particular financial and healthcare institutions, can be and is far-reaching, resulting in severe consequences *(as talked about briefly in the section above, where the impact on the UKs NHS was highlighted)*.

**Financial Losses**
Ransomware attacks can result in substantial financial losses for any effected organisation, though in particular financial institutions. Paying the ransom demanded by attackers is often costly and provides **no** guarantee of recovering the encrypted data. The costs of investigating the attack, restoring systems, and implementing enhanced security measures can also be significant.

**Regulatory Penalties**
Financial institutions in particular are subject to strict data protection and security regulations. In a ransomware attack leading to a data breach, regulators may impose severe penalties and fines for non-compliance. Moreover, reputational damage caused by non-compliance can further erode customer trust and investor confidence.

**Loss of Customer Trust / Reputation Damage**
Customers entrust organizations, such as professional services and financial institutions with sensitive financial data and personal information. A successful ransomware attack compromising this data can lose customer trust, loyalty and damage the brand irreparably. Customers may lose confidence in the compromised organizations ability to protect their data, leading to potential client/customer attrition.

**Operational Disruption**
Ransomware attacks can cause significant operational disruption for any organization, though in particular, financial institutions. Encrypting critical systems and data can render them inaccessible, resulting in delays and disruptions in financial transactions, customer services, and other essential operations. This can lead to a loss of productivity, decreased customer satisfaction, and potential financial losses.

**Legal Costs**
Ransomware attacks can also lead to legal consequences and associated costs for the effective organization. When client/customer data is compromised, affected individuals may take legal recourse for negligence in protecting their information. Legal fees, settlements, and potential damages can add to the financial impact of the attack.

**Loss of Intellectual Property**
In addition to customer data, ransomware attacks can also result in the theft or loss of valuable intellectual property. Many business and financial institutions may have proprietary software, algorithms, trading strategies, or other sensitive information that, if compromised, can lead to significant competitive disadvantages and financial losses.

**Disruption in Supply Chain**
Ransomware attacks targeting key organisations and financial institutions can also have a ripple effect on their supply chain partners. If threat actors gain access to these systems and use them as a launchpad for further attacks, it can impact other organizations connected to the compromised company, leading to a wider disruption in the business and financial ecosystem.

**Increased Insurance Premiums**
Following a ransomware attack, organizations and financial institutions may experience an increase in their cyber insurance premiums *(if applicable)*. Insurance companies may reassess the organization's risk profile and adjust premiums accordingly, further adding to the financial burden and outlay.

## **Ten Best Practices to aid Your Recovery Strategy**

With all of the above in mind, here are ten best practices to consider, which will aid your disaster recovery strategy and offset your threat model for ransomware:

1. **Backup Data**: Regularly backup all important data and ensure that backups are stored securely offsite or in the cloud. This ensures that even if your primary data is compromised, you can restore it from a secure backup. Ideally multiple instances of sensitive data should exist, providing redundancy, should your data and primary back up data be successfully targeted.
    
2. **User Training**: Educate employees about the risks of ransomware and social engineering attack vectors and provide training on how to identify phishing attempts and suspicious links or attachments.
    
3. **Email Filtering**: Implement robust email filtering solutions to block malicious emails and prevent phishing attempts from reaching employees' inboxes.
    
4. **Vulnerability & Patching Management**: Keep all software, operating systems, and applications up to date with the latest security patches to address known vulnerabilities.
    
5. **Network Security**: Utilize firewalls, intrusion detection systems, and other network security measures to protect against unauthorized access and malware infiltration.
    
6. **Incident Response Plan**: Develop a comprehensive incident response plan outlining steps to take in the event of a ransomware attack, including who to contact and how to contain the damage.
    
7. **Multi-Factor Authentication**: Implement multi-factor authentication (MFA) wherever possible to add an extra layer of security to user accounts and systems.
    
8. **Regular Testing**: Conduct regular testing and simulations of ransomware scenarios to evaluate the effectiveness of your prevention and recovery measures.
    
9. **Isolation**: Segment your network and restrict access to critical systems to minimize the impact of a ransomware infection and prevent it from spreading across the entire network.
    
10. **Data Recovery**: Establish procedures and tools for quickly recovering encrypted data from backups in the event of a ransomware attack, minimizing downtime and business disruption.
    
By implementing these best practices, businesses can significantly reduce their risk of falling victim to ransomware attacks and mitigate the impact if an attack does occur.
## In Summary ...

Remember, prevention is key, but having a robust recovery plan in place is equally important to ensure business continuity in the face of cyber threats. Stay vigilant, stay prepared, and keep your business safe from ransomware.

In general, organizations should aim to focus on the following key areas:

- **Robust vulnerability management (VM) program.** Vulnerability management is a continuous, proactive, and often automated process that keeps your computer systems, networks, and enterprise applications safe from cyberattacks, such as ransomware and data breaches. The goal of VM is to reduce the organization's overall risk exposure by mitigating as many vulnerabilities as possible.
	- Maintaining good security hygiene, including timely patching and regularly reviewing security tool configurations
- **Security tooling, people and processes** that defend against the most common attack vectors, including endpoint detection, protection and response.
- **24/7 threat detection, investigation, and response**, e.g., a security operation centre (SOC) whether delivered in-house or in partnership with a specialist Managed Detection and Response (MDR) service provider.
- **Disaster response (DR) preparation and optimization**, including making regular backups, practicing recovering data from backups,  and maintaining an up-to-date incident response plan

In today's interconnected digital world, our reliance on various online systems, platforms and communication channels makes us all, individual and organisations alike, vulnerable to malware and ransomware attacks.

Despite widespread awareness of cybersecurity threats, including phishing emails, misconfigured services, and lax perimeter defenses, users often remain trusting. This trust stems from the necessity and requirment of digital connectivity and communication for businesses, employees and customers.

Threat actors exploit this trust and these means, through identifying weaknesses and misconfigurations, aiming to establish a foothold and gain access to a corporate or individual users system on the assumptions that they will contains sensitive business information, credentials, banking information, and private data.

It's crucial for organisations and users alike, to remain vigilant and cautious to the risk of falling victim to malware and ransomware attacks.
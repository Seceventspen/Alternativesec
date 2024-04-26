---
layout: post
title: 'Top 5 Common Cloud Vulnerabilities'
tags: [Pentest, Cloud, Top5, Vulnerabilities, Best Practice]
featured_image_thumbnail: assets/images/posts/2018/2_thumbnail.jpg
featured_image: assets/images/posts/2018/2.jpg
featured: true
hidden: true
---

# The Cloud, love it, loth it; however, we’re all living it!

From streaming our favourite shows to sharing photos with friends and colleagues, cloud computing has revolutionized the way we live and work. But what exactly is the cloud, and how did it come about?

<!--more-->

Simply put, the cloud refers to a network of remote servers that store, manage, and process data over the internet, instead of on a local server or personal computer. This concept has been around since the 1960s, but it wasn't until the late 1990s and early 2000s that cloud computing became more widely available and accessible to the general public.

With the many benefits of cloud computing, such as increased flexibility, scalability, and cost-effectiveness, it's no surprise that more and more businesses and individuals are adopting cloud-based solutions. However, as with any technology, there are potential risks and vulnerabilities associated with the cloud.

In this blog post, we'll be discussing the top 5 cyber security vulnerabilities that are commonly associated with cloud computing. By understanding these risks, you can take steps to protect yourself and your data while using cloud-based services.

Ok, so before we do dive in, maybe the “Top 5 Cloud Cyber Security Vulnerabilities” isn’t exactly accurate, I would propose a more accurate title would be **“5 Common/Reoccurring Cloud Cyber Security Vulnerabilities”**, as for the most part, from our vast experience here at Lares, providing and conducting cyber security engagements in all different forms, e.g., Red Team, Insider Threat, Purple Team, Penetration Testing, Compliance etc., more often than not, these issues, regardless of engagement type, appear to be the most prevalent common and reoccurring issues that lead to exploitation or facilitate an initial foothold. So, without further ado, let's dive in!

The five most common/reoccurring Cloud Cyber Security Vulnerabilities findings (in no particular order) we come across within clients’ environments are as follows:

- Cloud Misconfigurations (e.g., IAM, S3)
- Unauthorised Access
- Insecure APIs/Services/Interfaces
- Lack of Visibility
- Unsecure third-party resources

Pssst… I’ll also discuss a more general finding/issue, towards the end of the blog post that touches every facet of cyber security, including cloud and the impact it can have.

While some of these findings carry change control, patch and risk management requirements, others often do not have a simple fix; however, several of the root causes associated with the common/reoccurring cloud security vulnerabilities can be remedied with businesses embracing a ‘best practices’ approach both in policy and technical controls. It is key to remember, that ‘best practices’, simply put means ‘things that have worked out well for the masses’ and as such should work well for you too, spoiler alert, your business still needs to carry out its’ own business risk analysis in order to fully understand the proposed best practice adoption and what it actually means for you and your user base. Blindly accepting/implementing any change, can, unfortunately, land you back in a compromising position, with even less understanding or awareness than you had before.

### Cloud Misconfigurations (e.g., IAM, S3)

This is probably the most common vulnerability an organization will face and a leading cause of why Cloud data breaches in particular occur. Misconfigurations can come in all forms and are too many to go cover within this post; however, I’ll touch on a few of the stand out items below. Interestingly, these all-too-common misconfigurations, and their associated vulnerabilities, are often caused by a lack of knowledge of good practices, rushing to stand an environment or service up, a lack of peer review from relevant teams such as, DevOps, Security Architecture or a combination of these things.

### Identity Access Management (IAM)

IAM misconfigurations are common within cloud systems, all too often they happen when, something e.g., a user or service, has been created and given access to resources that they should not be able to access or interact with.

Basically, IAM is another form of ‘Role Based Access Control’ (RBAC) system. In IAM, roles take on three primary forms:

- Users
- Roles
- Groups

IAM might sound like a daunting area; however, securing/configuring it correctly, doesn’t have to be complicated or elaborate. Here are some easy-to-follow tips to minimize this type of threat:

- IAM ‘Root’ user – DON’T USE IT FOR DAILY TASKS! Instead:
    -   Create a separate IAM user for administration and technical work.
    - Disable and delete any credential pairs the root user may have had.
- Enforce MFA, EVERYWHERE!
    - IAM users in any account should always have Multi-Factor Authentication (MFA) enabled.
- Restrict User/Service/Resource Access
    -   Enforcing the principle of least privilege, is the most effective way of achieving this! This should be done for all of your cloud resources and users; Avoid granting complete access to a user/service/resource if a they/it only needs read access or access to a subpart of the resource.
- IAM User ‘House Keeping’
    - Frequently review access and privileges. Access requirements can and will change over time.
    - Delete inactive accounts and/or suspend user accounts where that user is non-operational for prolonger periods of time. 
- Key Rotation
    - Regularly change SSH and PGP keys
    - Change KMS keys as/when needed
    - 2FA/MFA, changing keys or tokens can help can mitigate stolen keys and eliminate an attack surface

### Public Data Storage (Buckets and Public Objects)

Public Data Storage misconfigurations can have extremely damaging consequences and again, just like IAM misconfigurations, are another common vulnerability an organization will face. In particular, in recent years these have been another leading cause of why Cloud data breaches, in particular, occur.

For instance, you might need to use a ‘bucket’ for website storage or hosting static content. This inevitably means you’ll probably need to make some of, if not all of the bucket or its contents, public.

Here are some easy-to-follow tips to minimize this type of threat:

- Bucket Data Storage
    - Set to ‘Private’ by default. Not all cloud providers do this by default; however, it is detailed in each of the main cloud providers documentation on how to do so.
    - Key point to note, as of December 2022, AWS, as do Azure offer ‘private by default’ creation of their S3 buckets.
- Bucket Permissions
    - Permissions (such as GET, PUT, DELETE, LIST for HTTP methods) should be restricted to certain users
- Logging/Versioning
    - This should be enabled on all buckets
- Use cloud-native tooling to scan your infrastructure, for instance, AWS have and GPC have the Security Command Centre

_Note: irrespective of cloud provider, you should thoroughly and carefully consider, prior to choosing, the most appropriate solution for your needs. Furthermore, be aware with what is being added to any bucket you create and/or manage, as depending on the settings configured, an added item may remain public until you change it, potentially exposing sensitive data._

### Unauthorised Access

In short, unauthorized access occurs when a user/threat actor obtains access to some or all of a business’s cloud resources. Unlike a traditional ‘on-premises’ infrastructure, cloud-based deployments are outside the original concept of the ‘network perimeter’ and as such, directly accessible from the public Internet. Whilst in this digital age, the 24/7 accessibility of cloud-based infrastructure is not only an asset, but more so a necessity to employees and customers alike, it also makes it easier for a threat actor to gain unauthorized access to an organization’s cloud-based resources. This is largely in part to misconfigured or lax security controls and compromised credentials, as these can enable a threat actor to gain direct access, potentially without an organization’s knowledge.

Here are some easy-to-follow tips to minimize this type of threat:

- Enforce MFA, EVERYWHERE across your business/organization! This should be a mandatory action for any user with cloud access and/or data within cloud environments.
- Enforce a suitably robust password policy, with added complexity
    - The jury is still out whether it should be a password, a passphrase or even passwordless e.g., certificate-based authorization, Zero Trust policy driven access etc.; however, what it should be, is easy for a user to understand their obligations and deal with, though that doesn’t mean allowing users to set easily guessable password just because 2FA/MFA is in place. Always make sure safe password practices and hygiene are being followed.
- End user awareness/education
    - Whether it is employees or customers, either start or continue to build on social engineering awareness around these types of attack vectors such as phishing, vishing etc. These tactics are regularly employed by threat actors in order to gain access credentials for accounts and/or services.
    - Continuously improve email filtering to make it increasingly harder for threat actors to target your end users, along with honing detection and filtering of phishing emails.

### Insecure APIs

The TL; DR, is there is no escaping it, APIs are everywhere, they are backbone of modern software developments and environments, particularly cloud, whether it’s cloud provider APIs for their customers or APIs stood up by your organization, there’s just not getting away from them! They are used in just about anything a user can access, from microservices to applications to websites.

API’s can and often do have undocumented vulnerabilities, ranging across various misconfigurations. As such, securing APIs is critical to protect against unauthorized use, unwanted traffic and also provide overall cyber threat mitigation. 

Threat actors can and will attempt to exploit APIs in a variety of ways; however, the most commonly noted are:

- Broken Authentication / Broken Authorisation
- Security Misconfigurations e.g., unpatched flaws, common endpoints, or unprotected files and directories
- Code Injection e.g., Command injection, SQL Injection etc.

Here are some easy-to-follow tips to minimize this type of threat:

- API documentation. An API should be clearly, concisely and well documented. This documentation along with the API code base should be regularly reviewed by both automated and manual means. As this will help add in identifying any security issues.
- Web Application Firewall. Implementing a web application firewall (WAF) to filter requests by IP address or HTTP header info, and to detect code injection attacks; WAFs also let you set response quotas per user or other metrics.
- Implement an API gateway.
    - This acts as a reverse proxy, sitting between the API collection of backend services and the client; therefore, prevent unnecessary exposure of the APIs directly.
- Implement rate limiting e.g., limiting the number of API calls the client (API consumer) is able to make in a second. This can aid in also preventing ‘resource exhaustion’ and ‘DDoS’ attacks.
- Implement DDoS protection.
    - Arguably this could be a ‘common cloud vulnerability in its own right; however, so could many other things as well. That said you’ll want to consider the following for you cloud environment or when choosing your cloud provider:
        - Most cloud providers that protect against DDoS attacks, e.g., AWS Shield comes with easy integration and no additional cost. Check that your chosen provider offers this service.
        - If not by default, make sure DDoS protection on your cloud service/environment (if applicable) is always turned on.

### Lack of Visibility

As with most things in life and cloud, as we grow, we sometimes loose site of things, or in this case, have a lack of visibility and consequently lack of understanding of our cloud environment. Our cloud services grow and so does the scale of the resulting infrastructure. Clearly, losing sight or having a lack of visibility in your cloud environment is a major concern, which can impact and/or delay actions-on a threat being detected and which may also result in a data breach!

Most cloud providers offer an array of services, tooling, detection and alerting capabilities; however, a proactive approach must still be taken by the organization and people responsible for administering any environment.

Here are some easy-to-follow tips to minimize this type of threat:

- Monitor for and detect threats, with real-time alerting (where possible).
- Ensure visibility and understand of your cloud infrastructure. For example, AWS in Feb 2023 announced a new capability to ‘visualize your VPC resources’ Infrastructure monitoring employs a set of solutions and practices to ensure availability, performance, and security in your technology stack. This stack includes virtualized environments, hardware, networks, storage resources, devices, applications, and operating systems.
- Implement tools such as Cloud-native application protection; as this can minimize risk and shorten the response time in security alert, incident or breach.

### Unsecure third-party resources/components

Risks exist everywhere and the cloud, the resources and components you use are no different! How you manage them ultimately dictate how prepared you are to response and this is the same for risks related to third party resources and components. No matter how secure your own code is, whether it be an API, SaaS, PaaS, dependencies or third-party components, threat actors can exploit them, if they are not themselves secure.

A threat actor can identify the supply chain, third-party resource or component and start from here. Needing only to compromise the weak link, in order to carry out their attack against your company cloud environment.

An example of such an attack in recent times was the Node.js/NPM supply chain attack in Dec 2021. Where packages hosted on Node Package Manager (NPM), the package manager for the Node.js JavaScript platform, either being compromised directly to deliver malware or simply being created to impersonate popular, legitimate packages.

Key areas a threat actor will commonly focus on are:

- Vulnerable 3rd party open-source packages/libraries
- Vulnerable versions of application components
- Use of known vulnerable container images

Ultimately, you can prevent bugs and vulnerabilities in your code; however, you can’t prevent the same in code or products that you or your team haven’t created. Therefore, robust and well thought out controls should be implemented to help you make informed decisions about what to use and the risk it might pose.

Here are some easy-to-follow tips to minimize this type of threat:

- Conduct a business risk analysis on the things you use, particularly on third party resources. Look for the products that are officially supported. Also, consider those with compliance certifications, that openly speak about their security efforts, that have a bug bounty program, and that treat their users responsibly by reporting security issues and delivering fixes quickly.
- Track the third parties you are using. This may seem like common sense; however, its harder and more time consuming that it sounds, though this should not be used as a justification to ignore or not follow through. The more you know, the better prepared you are to respond.
- Ideally create an in-house repository/library for the things you use. This will allow you to test new versions/updates that have been release or pushed, ahead of them being actively used by your services, applications and cloud environment.
- Carry out a third-party review, whether that be periodically, bi-annually or quarterly, the main thing is that you start now, if not already doing so! Should a product, service, component, library be identified that is no longer needed, remove them, revoke any access requirements/permissions and document this. 

So, there we have it, that’s the 5 cloud security vulnerabilities. Now time for the bonus one….

### Bonus consideration affecting Cloud environments: The ‘Insider Threat’

Ok, the ‘Insider threat’, let’s face it, it’s always been a ‘thing’; however, the prominence of this attack vector and type, is now proving to be a major security headache and issue for organizations around the globe.

A malicious insider, for example, a disgruntled employee or contractor, already has authorized access to an organization’s network and some or all (depending on their privileges) of the sensitive resources that it contains. Attempts, by a threat actor, in this case, a malicious insider, to gain elevated levels of access, depending on their skill, are what reveals the presences or actions of most attackers to their target, making it hard for an unprepared organization to detect a malicious insider.

Now translating this attack vector to the cloud, detection of a malicious insider is often even more difficult. With cloud deployments, companies enter in to a shared responsibility model [1] [2] [3] with their respective Cloud provider, and as such, lack control over their underlying infrastructure. This often makes many traditional security solutions less effective. Couple the aforementioned concern, along with the fact that cloud-based infrastructure is, more often than not, directly accessible from the public Internet, in some for or other, and often suffers from security misconfigurations, makes it even more difficult to detect malicious insider.

My colleague Andrew Gill has put together a great post on the ‘Insider Threat’ attack type and the Top 5 findings that Lares come across while conducting an ‘Insider Threat’ engagement. The post can be found here {<<< link to you article 😊}

Summary

In summary, we walked through the top 5/5 most common and reoccurring cloud security vulnerabilities, along with key considerations and starting points to help prevent these issues or vulnerabilities existing within your cloud environment. 
Key takeaway’s:

- Hardened defences at the core of cloud architectures have shifted hacking, to endpoint user identity, as low-hanging fruit.
- Discrete user and application-based isolation is ultimately required to achieve a robust ‘zero trust-layer’ beyond simple authentication.
- Advanced tools are only part of the story, such as cloud infrastructure entitlement management (CIEM). Operational policies and structured risk models are also vital.
- Trust is more than giving keys and codes. It’s earned. User objects must be given risk scores that dynamically adjust as the business requires and evolves.

There are many resources available from each cloud provider, to assist with helping configure a more secure cloud environment. As a starting point, look at what your cloud provider offers and how that can be leveraged (if not already so), then look for additional resources such as Cloud-native application protection (CNAPP), along with open-source security-oriented tooling such as ‘Prowler’, ‘Scout Suite’ etc.

Here at Lares, we can offer a comprehensive Cloud Assessment tailored to you needs, due to our vast levels of experience and expertise, we regularly carry out Red Team, Insider Threat, Purple Team, Penetration Testing, Compliance against our clients’ environments.

**Links / References**
[1] AWS Shared Responsibility Model
[2] Azure Shared Responsibility in the Cloud
[3] Google Cloud Platform Shared Responsibility Model

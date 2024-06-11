---
layout: post
title: 'The Pentest Fun Police… or are we ...'
tags: [Pentest101, Tips, Best Practice]
featured_image_thumbnail: assets/images/posts/ptfp/pt-f-p1.jpeg
featured_image: assets/images/posts/ptfp/pt-f-p1.jpeg
featured: true
hidden: true
---

*... Woop-woop, that's the sound of da police ...*

During my time as a penetration tester, Adversarial Engineer, Red Teamer and security consultant, whether through the work itself or verbal interactions, one re-occurring theme always emerges above all others, and this is, that the "business" thinks that pentesters’/security are the fun police, aka, the **‘bad guys’**!

We're seen as party poopers, due the very nature of our job, more often than not, due to it being negative by its very connotation. Nobody wants to be told that the very things they’ve built/are responsible for, has issues and more so, issues that could delay or halt progress altogether or pose a security risk/impact to the business!

In this post we will dive into some of the key things that, we as penetration testers, Adversarial Engineers, red teamers, security consultant and the business, can do to revise our approaches, promote better engagement, build better rapport, bring greater value to the process, along with avoiding some of the common mistake that we've all been known to make! 

_**Image Credits:** [@_RayRT](https://twitter.com/_rayrt) \| [rayrt.gitlab.io](https://rayrt.gitlab.io/),
his skills are unreal, both technically and visually, thank you for you help as always!_


<!--more-->

# Background / Origins of this blog post

So this blog post originally started life as a **[BSides Belfast](https://bsidesbelfast.org/) 2023** talk submission, which got accepted _(yayy me ...)_, though due to work commitments, I had to pull out of the conference ... so the talk never seen the light of day _(sad face ... happy face, depending on whether you see any value in this message)_!

That said, I still feel there is value in getting the overall message of the talk, out there!

**Top Tip:** [BSides Belfast](https://bsidesbelfast.org/) is a great conference, and Belfast is an awesome city to visit! Please check out the BSides Belfast site and [Twitter](https://twitter.com/bsidesbelfast?lang=en-GB) for content and updates!

If you're interested,  [BSides Belfast](https://bsidesbelfast.org/) will return again on **Thursday, 12th September, 2024** at the Europa Hotel, in Belfast.

# Let's set the Scene ...

![scene](assets/images/posts/ptfp/pt-f-p-scene.jpeg)

Let's set the scene for this blog post, like I did/would have done for the talk, with the following premise:

In this post, we will dive into some of the critical things that we, as penetration testers/consultants and the Orgs, can do to revise our approaches, promote better engagement, build better rapport, bring greater value to the process, along with avoiding some of the common mistakes that we've all been known to make!

We can all contribute by identifying these key areas, working as one team towards a shared goal, ultimately becoming more effective and achieving better results and overall experience. In doing so, we can dispel the perception of penetration testers and security as the fun police!

With that,

**Q: Why do Penetration Testers/Testing Teams Hate us?**

- _Note: 'US' is an umbrella term for clients, vendors, development teams, network engineers, AppSec engineers, cloud teams, etc.._

**A: In short, I, we or they don't!**

- _The longer answer is, I, we, or they as a majority don't; however, this is often overlooked for various reasons, allowing for an "us V them" bias and emotion to kick in and complicate the process._

Ultimately, if before a penetration testing engagement commences, these people and teams believe this, everyone is already starting on the back foot! Just mooching around hilarious stories and posting all over Twitter and Reddit, you may even be inclined to think that without the 'Us' out there, penetration testers would be out of a job!

Some folks might say that the 'Us' folks out there need to change their perceptions of penetration testers and penetration testing engagements.

This will undoubtedly help, but the responsibility doesn't lie solely with them. As penetration testers/security professionals, it is also **our** responsibility to help reset these perceptions through our interactions, engagements, and experiences with these folks!

Effectively, as cheesy as it sounds, we, as penetration testers/security professionals, must be the change we want to see! Henry T. Ford said it best...

>"If you always do what you've always done,
>you'll always get what you've always got."
>	- Henry Ford

So, with our scene set and context given, let's dive in ...

![tvu](assets/images/posts/ptfp/pt-f-p-tvu.jpeg)

I'll say it again: penetration testers/teams test **DON'T HATE YOU**!

A key issue contributing to the complicated relationship between "security" and the "rest of the business" is that folks either feel obligated to or simply pick a side! Doing so creates ...

> Them and Us

Essentially this is a psychological state where you place yourself in one group and your perceived "foe" in an alternate group. Then you tell yourself that your group is better, and the "other" group is the one causing problems. For example, the "us against them" mentality can take on a role in work life.

In the dynamic realm of cyber security, a fascinating interplay of ’Them V’s Us’ exists between Clients, 3rd party vendors, Devs, Network teams, Cloud Teams, and penetration testers. As a penetration tester, it's imperative to understand and address the nuances of each facet to ensure holistic security assurance.

Let's unpack this intriguing relationship ...

In the realm of client-facing services, the collaboration between 'makers', e.g., developers, programmers, network engineers, cloud infrastructure folks and penetration testers, is paramount. These 'makers', craft the digital experiences that users _(whether employees or customers)_ interact with daily while penetration testers unearth vulnerabilities that could compromise these interactions. It's a symbiotic relationship that demands cooperation and mutual understanding.

Meanwhile, tensions can arise within the 'makers' teams themselves. Penetration tests require makers' time and resources, potentially diverting their focus from their day-to-day job, a metric often central to their primary duties and deliverables. This can foster a defensive mindset, hindering effective collaboration between makers and security teams.

Hence the formation of "them'uns and Us'uns" .. ok, this is a northern Irish colloquialism, but, if you haven't figured it out already, it means 'Them V's Us' ... never a good sign for a collaborative working engagement!

Furthermore, findings from penetration tests can inadvertently fuel perceptions of judgment. Makers may feel their work and the codebase are under scrutiny rather than recognizing security as an intrinsic component of software development. This defensive stance can also extend to network and cloud teams; however, a well-implemented security-driven development lifecycle framework covering development and both on-prem and cloud infrastructure and assets would solve several reoccurring issues and/or vulnerabilities noted by penetration testers.

Yet, amidst these challenges, I regularly see opportunities for collaboration and growth. Effective penetration testers aren't adversaries _(this doesn't mean red teaming in this instance, which is a wholly separate thing altogether)_; they're allies in the ever-relenting quest for robust security. By shifting the narrative from criticism to cooperation, penetration testers can bridge the gap between development, network, and cloud teams, fostering a culture of security awareness and resilience.

In summary, security is everyone's responsibility. We, penetration testers, developers, programmers, network engineers, cloud infrastructure folks, etc., should all play a pivotal role in ensuring security across multiple domains. By fostering collaboration, understanding, and open communication channels, we can all be empowered to navigate the ever-evolving cybersecurity landscape with confidence and resilience.

# Don't call my baby ugly ...

![ugly](assets/images/posts/ptfp/pt-f-p-baby.jpeg)

So, more often than not, penetration testers are met with bias and the following question:

**Q: Why is the penetration testing team testing my +INSERT_YOUR_THING_HERE+?**

- _Us monologue: We didn't ask to be tested, nor do we want it tested, nor do we have the time to let it be tested ... sigh_

**A: Hey your baby, e.g., +INSERT_YOUR_THING_HERE+, isn't ugly**

- _Ultimately, as a penetration tester/adversarial engineer/red teamer, it is our job to find any security misconfigurations, issues, vulnerabilities and exploitable components or attack vectors which threat actors may attempt to target and leverage to compromise +INSERT_YOUR_THING_HERE+!_

We want to use our skills to help you be more secure. We do this by identifying vulnerabilities which highlight a security concern and should ultimately draw attention to issues that need fixing.

We want to make **your** +INSERT_YOUR_THING_HERE+ more secure, as such, someone somewhere, whether due to regulatory obligations, a robust/effective vulnerability management program, a robust/effective secure development framework or all of the things above, has determined that **your** +INSERT_YOUR_THING_HERE+ should be prioritized and reviewed.

As to the "why and how" it's prioritized, this typically comes down to the significance of +INSERT_YOUR_THING_HERE+, data that flows through it, who uses it, and any exceptions that surround the security of +INSERT_YOUR_THING_HERE+.

The key points to note here are that:

1.	The penetration tester/test team is not personally picking on you as an individual or organization!
2.	None of the above has anything to do with anything you did or did not do.

There are many reasons that a penetration test might begin on your +INSERT_YOUR_THING_HERE+.

1.	Maybe your leadership chain wants/needs it?
2.	Maybe your in-house security team wants/needs it?
3.	Maybe your internal risk/governance/compliance team(s) want it?
4.	Maybe it is a legal obligation and requires an external auditor, e.g., a Government, PCI-DSS, or regulatory?
5.	Maybe, upon scoping a penetration testing engagement with your company, the penetration testers themselves determined that your +INSERT_YOUR_THING_HERE+ may present a risk and advised it should be tested.

In summary, I'll reiterate that security is everyone's responsibility; penetration testers, developers, programmers, network engineers, cloud infrastructure folks, etc., we all should be and must play a pivotal role in ensuring security across multiple domains.

Nobody is ever calling yours or anyone else's baby ugly, or at least I hope they aren't; makers have their job, and we penetration testers have ours; however, the very nature of penetration testing is designed to look at things from a different perspective, think like different to that of a maker and ultimately find that weakness that could or would compromise the integrity and security of +INSERT_YOUR_THING_HERE+.

This can be demoralizing, but we penetration testers understand the pressures and constraints often imposed upon makers to meet deadlines, complete sprints, and deliver features. So, allow us to assist you in ensuring **your baby** doesn't get called ugly!

By fostering collaboration, understanding, and open communication channels, we can all be empowered to navigate the ever-evolving cybersecurity landscape with confidence and resilience.

# Common 'Maker' questions and misconceptions ...

![Qs](assets/images/posts/ptfp/pt-f-p-Qs.jpeg)

Here I've listed some common questions and misconceptions that are regularly encountered.
### Q: Why is the penetration testing team giving me this finding?

- _They know we can't fix it…_

**A:** The **TL; DR** here is because we identified something that either falls outside of accepted best practices relating to the +INSERT_YOUR_THING_HERE+ and/or provides an area of unnecessary exposure and, therefore opportunity, for unintended interaction, misuse, or exploitation.

**The longer answer is**, that even if the maker's team cannot promptly address a vulnerability within the required timeframe(s), it's still crucial for penetration testers to report it. A well-implemented vulnerability management program and business risk register requires that records of vulnerabilities and their associated risks must be maintained regardless of the size of the maker's org/team.

The primary objective of penetration testing, application security, vulnerability management, or red team exercises is to identify and assess risks. Subsequently, the business and security management must evaluate these risks, considering business priorities and costs. Understanding the risks associated with vulnerabilities enables companies to make informed decisions regarding their products and services.

### Q: Why doesn't the penetration tester/testing team help me with remediation?

**A:** SO, the **TL; DR** here is, there are **2** answers:

**1. External / Consultancy penetration testers:** Generally, the are unable to assist with post engagement remediation activities, unless this is or has been pre-agreed as part of the work being carried out,; however, that said, any findings they find, should have curated recommendations, which outline remediation actions or specific points to review related to the issue at hand.

**2. Internal penetration testing teams** _(or tech savvy security teams)_**:** may be able to assist; however, this largely depends on the size of the team, their workload and their ability to directly liaise, on a regular basis, with you/your team to work through the issue, testing and readjusting.

While there are exceptions to these rules, the long and short of it is, that not all penetration testing teams assist with day-today remediation activities. Remediation responsibilities can be divided among different maker security teams to allow for specialization. For instance, an Information Security Officer can serve as both the primary security contact and provide remediation assistance.

This setup enables penetration testing teams to focus more on testing work, as remediation can be time-consuming. Conversely, a penetration testing team may offer remediation advice, leveraging their expertise in identifying vulnerabilities. It's essential to recognize that each team has its own set of responsibilities, and offering remediation assistance may detract from their primary focus on testing and securing +INSERT_YOUR_THING_HERE+.

Nevertheless, the team best able to remediate the +INSERT_YOUR_THING_HERE+ will always be the makers themselves.

### Q: Why are there 'minor' security issues being reported by the penetration testers/testing team?

- _Having to triage these prevents us from doing more important work?_

**A:** In essence, reporting minor security issues, such as low or informational findings like, missing HTTP headers, version disclosures and default pages holds value for several reasons:

**1. Assurance and Efficiency:** Version disclosures provide attackers with assurance of a specific version, potentially saving time by avoiding the need for guessing. This efficiency in attack attempts can minimize the risk of detection by security monitoring systems.

**2. Holistic Threat Landscape:** By documenting the entire threat landscape, including low-severity findings, penetration testers fulfil their responsibility to provide a comprehensive view of potential vulnerabilities. This approach ensures that the maker team(s) and the company are aware of all possible security risks.

**3. Agile Risk Management:** If the development team determines that fixing a minor issue is impractical or not a priority, they can choose to accept the associated risk _(Business risk register, vuln management program wink wink)_. Ultimately, it's up to the business to decide how to proceed, balancing the effort of remediation against the potential impact of exploitation.

In summary, while it may seem counterintuitive to invest time in reporting minor security issues, doing so contributes to a thorough understanding of the overall security posture and enables agile risk management within the organization.

### Q: Will the penetration tester/testing team set up a debrief meeting?

- _I don't understand the findings in the report…_

### Q: Why is the penetration tester/testing team setting up a debrief meeting?
- _I've read the report already..._

### Q: Why doesn't the penetration tester/testing team set up a debrief meeting?

- _I don't understand the findings in the report…_

All good penetration testing engagement should have some form 'debrief' call scheduled, after a suitable amount of time has passed to enable the makers to read and digest the report and its contents; however, the need for a meeting to discuss penetration testing reports and findings varies among companies. While some testers may automatically arrange such meetings, others prioritize generating comprehensive reports, considering them efficient records of testing outcomes.

However, meetings can be valuable for clarifying report contents, especially when makers require further explanation or context. These sessions also offer opportunities to enhance maker comprehension, and potentially leading to adjustments in severity level or even the resolution of findings.

Effective meetings enable testers to provide targeted guidance on remediation and impact analysis, benefiting teams in their risk mitigation efforts. Yet, breakdowns occur when developers request meetings without reviewing the report beforehand, resulting in inefficient use of testers' time.

It's worth keeping in mind that, meetings can be derailed when essential stakeholders are absent or when additional parties are unexpectedly required, leading to unnecessary scheduling complications. Despite these challenges, ensuring that the right individuals attend and engage in discussions can streamline the remediation process.

In essence, while meetings can facilitate understanding and collaboration, they should be conducted efficiently, with participants prepared to engage meaningfully with the report content.

![collab](assets/images/posts/ptfp/pt-f-p-collab.jpeg)

Makers, we get it, you're busy, working against deadlines, feature releases and the like, It's therefore understandable that not everyone has the time to read reports before every meeting, as they can be time-consuming; however, it's essential to recognize that penetration testers are also busy professionals with competing priorities. They may be juggling multiple tests, handling retest requests, or planning future engagements.

That said, preparing for meetings by reviewing the report and coming with questions can significantly aid the penetration tester's ability to assist you effectively, as well as showing appreciation for their effort in compiling the report demonstrates respect for their time and dedication to their role.

## Q: When do we have to carry out testing?

- _Our +INSERT_YOUR_THING_HERE+. is changing in the next few weeks. Can this testing wait till then?_

## Q: Do we have to do this testing NOW?

- _How come the penetration testing team are telling me that +INSERT_YOUR_THING_HERE+ need testing_

The timing of penetration testing in the midst of +INSERT_YOUR_THING_HERE+ changes can raise questions about prioritization; however, waiting for all changes to conclude before testing would be impractical, as +INSERT_YOUR_THING_HERE+ undergo constant evolution.

In fact, testing during periods of significant change can be advantageous, though this not the same and as +INSERT_YOUR_THING_HERE+ being "hot-fixed" during the testing period. While stability may be a concern, identifying vulnerabilities during this phase allows for easier integration of remediation efforts into the development schedule. Moreover, architectural changes required for remediation may be more seamlessly incorporated during periods of transformation.

Considering the circumstances, testing now and retesting the application upon completion of changes could be a prudent approach. This ensures that the application's security posture is assessed both during and after the transition phase, offering comprehensive protection.

As a very general rule of thumb:
1.	Test & review regularly through the build phases
2.	Test thoroughly upon production elevation/release
3.	Test upon a new feature being added
	1.	Normally, just the new feature
4.	Testing upon any major uplift, functionality or architectural change

Coinciding these with the robust implementation of a secure development lifecycle framework will pay of dividends!

### Q: I/We don't agree with the risk rating associated with this finding; can we lower the risk rating?

![meet](assets/images/posts/ptfp/pt-f-p-meet2.jpeg)

So, push back is not a bad thing and as penetration testers we should not fear or be unwilling to engage in this type of request/conversation.

Healthy dialogue between penetration testers and Makers is encouraged. Makers often possess context that may mitigate the severity of a finding, and testers should be open to reassessing ratings based on this information, prioritizing logic over ego. That said, just because a maker says they have A, B & C in place, doesn't mean they do or that it is actually effective. Makers should always be willing to provide a proof of concept or ask for the issue to be retested with the proposed changes in place.

However, it is important to note, forever one involved in this process, that requesting a lower severity rating has implications. It can lead to mean time to remediation increasing, e.g., deadline extensions, reduced attention on the issue, and potential impacts of a security nature while the issue remains unresolved.

When requesting a lower severity, Makers may focus on debating hypothetical attack likelihoods or exploit ease to reduce severity without providing genuine context. In such cases, we penetration testers should consider the company's security requirements over our individual preferences; however, ultimately it is the makers/company's responsibility to prioritize their security and remediation efforts. Whether we know or understand the risk and resulting impact better, it is ultimately out of our hands what happens after the report and findings are delivered.

Ultimately, penetration testers/testing teams are accountable for the agreed scope-of-work, which hopefully aligns with the makers/company's security objectives. While we penetration testers should consider valid mitigating factors, we must also ensure that our deadlines and requirements are upheld appropriately. Collaboration with makers should aim to facilitate effective remediation, through well documented and explained findings, which clearly set out the issue and resulting risk impact.

# So ... Are we the Pentest Fun Police???

![p2](assets/images/posts/ptfp/pt-f-p2.jpeg)

I'll say it again, penetration testers/test teams:

- DON'T HATE YOU!!
- We're not trying to rain on your parade!!
- We aren't calling your baby ugly!!

What we are is:

- A multi-faceted capability, here to help and enhance the cyber/security posture of +INSERT_YOUR_THING_HERE+

So, let's be friends and all get along eh?!

Here are some key advantages we can and will bring to the table:

1.	Identification of Weaknesses: Penetration testers excel in uncovering weaknesses in an organization's security posture. By simulating real-world cyber-attacks, we can identify vulnerabilities before malicious insiders and/or threat actors exploit them.
2.	Risk Mitigation: By pinpointing vulnerabilities, penetration testing teams enable organizations to proactively mitigate risks. This allows for targeted allocation of resources to strengthen defenses where they are most needed. Effectively a value add to a makers/company's secure development lifecycle framework and vulnerability management program.
3.	Compliance and Regulation Adherence: Many industries are subject to regulatory requirements mandating regular security assessments. Penetration testing helps organizations ensure compliance with standards such as PCI DSS, HIPAA, GDPR, etc.
4.	Enhanced Incident Response: Understanding potential attack vectors allows organizations to fine-tune their alerting & detection, along with their incident response plans. Basically, penetration testing provides valuable insights that can streamline and improve response efforts in the event of a real breach.
5.	Cultural Shift towards Security: Engaging a penetration testing team fosters a culture of security consciousness within an organization. It promotes awareness among employees about the importance of cybersecurity and encourages proactive measures to protect sensitive data.

It's crucial to dispel the idea that we are the 'fun police' and the 'Them Vs Us' mentality. Doing so will promote a more harmonious and collaborative experience between makers and penetration testers/testing teams alike. We are generally here to help and not the enemy!

>"Progress is impossible without change, and those who cannot change their minds cannot change anything."
>
>George Bernard Shaw

Now, regarding how best use of our time and skills, it's crucial to leverage penetration testing resources effectively to maximize our impact.:
1.	Targeted Testing: Prioritize testing efforts based on the criticality of systems and assets. Focus on areas with the highest potential impact on business operations or where sensitive data resides.
2.	Regular Assessments: Conduct periodic penetration tests to keep pace with evolving threats and changes in the IT environment. Regular assessments help maintain a robust security posture over time.
3.	Collaboration with IT and Security Teams: Foster collaboration between penetration testers, IT administrators, and security teams. This ensures that findings are effectively communicated, and remediation efforts are coordinated efficiently.
4.	Integration with Risk Management Processes: Integrate penetration testing findings into the organization's risk management processes. This enables informed decision-making regarding security investments and resource allocation.

By strategically deploying penetration testing resources and integrating their findings into broader risk management practices, organizations can significantly enhance their cybersecurity posture and resilience against cyber threats.

Going back to my favourite quote:

>"If you always do what you've always done, you'll always get what you've always got."
>
>Henry T. Ford

When it's all said and done, your penetration testing team doesn't hate you and we're not the fun police!

Ultimately, I think Makers/Companies and penetration testers alike can all take a breath, engage more openly and honestly, work more collaborative and shake of the age old "Them Vs Us" mentality!

Here are some things we can all do better to work towards becoming BFF's:

1. **Time:** Respect everyone's time. We are all likely involved in multiple things and using everyone's time effectively, makes everyone happy.
2. **Communication:** I cannot emphasis this enough, lack of comms, poor comms, without important/relevant information is the number one way to get folks backs up on both sides and essentially leans into the 'Them Vs Us' mentality. The more you communicate with use, the more effective we can be and the more collaborative we will be in return.
3. **Understanding**: that penetration testing is designed to identify issues in +INSERT_YOUR_THING_HERE+ before they're exploited, not shame or attack you as a maker or your company.
4. **Questioning:** Respectful, logical and responsible questioning is essential. We all need to leave our egos, emotions and personal biases at the door. Differing opinions are valuable, as long as the goal remains focused on securing +INSERT_YOUR_THING_HERE+ and not ignoring the problems.

If **WE** can do all of this, It will go a long towards making sure Makers and penetration testers/testing teams alike, never have a situation again, where the "Them Vs Us" takes precedence and gets in the way of what we're all trying to do...

Ensure +INSERT_YOUR_THING_HERE+ is safe, secure and fit for purpose! ... _(maybe ...)_

Thanks for reading!
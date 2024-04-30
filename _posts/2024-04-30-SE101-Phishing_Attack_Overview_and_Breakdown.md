---
layout: post
title: 'SE101 - Smishing Attack Overview and Breakdown'
tags: [Pentest, SE, Social Engineering]
featured_image_thumbnail: assets/images/posts/se101/phishing.jpg
featured_image: assets/images/posts/se101/phishing.jpg
featured: true
hidden: true
---

Phishing’ at its most basic level, involves sending fraudulent emails, claiming the pretence of being from a reputable or well known/trusted/familiar company or individual, with the goal of deceiving recipients into either clicking on a malicious link or downloading an infected attachment, usually to steal financial or confidential information".

<!--more-->

In short, just like [Smishing](https://www.alternativesec.xyz/SE101-Smishing_Attack_Overview_and_Breakdown), Phishing is a social engineering attack vector that leverages email based messaging to deceive individuals/groups, into taking several actions *(outlined later in the post)*.

Following on from the series created by [Ghostie](https://blog.ghostie.org/), **Social Engineering 101**, featuring blogs post by both Ghostie and I, this is the latest post in the series, which covers ‘**Phishing**’, a highly prevalent, yet more importantly, highly successful social engineering attack vector.

## What exactly is ‘Phishing’?

'**Phishing**’, at its most basic level, nvolves sending fraudulent emails claiming to be from a reputable or well-known/trusted/familiar company or individual. The goal is to deceive recipients into clicking on a malicious link or downloading an infected attachment, usually to steal financial or confidential information.

Common tactics employed in Phishing attacks include masquerading as reputable entities, such as:

- Banks
- Government agencies
- Well-known service providers e.g., Facebook, Microsoft, Netflix etc.
- Family and friends

Regardless of the entity being masqueraded in the email, these messages often contain links and files, e.g., images, documents, compressed/archived files, that when interacted with, can lead to the compromise of the recipient device, personal information and/or the installation of malware.

As such, it is imperative that we remain vigilant and educate ourselves, our colleagues, family and friends on recognizing, and avoiding such deceptive messages to safeguard our sensitive information, or in the case of business, its proprietary and customer information.

Given the prevalence of laptops, tablets, mobile devices and desktops computers in our daily lives, Phishing always has and most likely always will be a favoured tactic among cybercriminals.

## So how does ‘Phishing’ work at a high-level?

Well, this is a form/variant of a ‘phishing’ attack, in which an attacker uses a compelling narrative within the email title and message body to lure, build rapport and ultimately trick the targeted recipient(s) in to the doing any or all of the following:

- Clicking a link which will have malicious intent or consequences
- Sending the social engineer/threat actor private information
- Sending the social engineer/threat actor corporate login information
- Sending the social engineer/threat actor financial information
- Making a purchase for gift certificates/store cards _e.g. Amazon, Apple…_
- Transferring money to unknown accounts
- Downloading malicious programs/software to the device(s) which the email is being opened/read on

It is worth noting that the social engineer/threat actor, or the ‘Phisher’ as we’ll now refer to them, may use your actual name and location to address you directly. Using these details make the pretext of any message more compelling for the recipient.
## Lets Breakdown a Simple 'Phishing' Attack

So before we breakdown the attack, its worth pointing out that there are a number of common phishing email pretext/lures, that are one point of another we've all received at least one of:

1. **The fake invoice scam:** Deceptive emails posing as legitimate invoices from known companies, aiming to trick recipients into making payments to fraudulent accounts.
2. **Email account upgrade scam:** False notifications claiming to be from email service providers, urging users to upgrade their accounts by clicking on malicious links to steal login credentials.
3. **Advance-fee scam:** Fraudulent emails promising large sums of money in exchange for a small advance payment, exploiting greed and desperation.
4. **Google Docs scam:** Phishing emails disguised as Google Docs invitations, prompting recipients to grant access to their Google accounts, allowing attackers to steal personal information.
5. **PayPal Scam:** Fraudulent emails impersonating PayPal, requesting account verification or claiming unauthorized transactions, aiming to obtain login credentials and financial details.
6. **Message from HR scam** *(Corporate/Business user email)***:** Falsified emails purportedly from Human Resources departments, often containing urgent requests for sensitive employee information or login credentials.
7. **Dropbox scam:** Fake emails masquerading as notifications from Dropbox, tricking users into clicking on malicious links or attachments that install malware or steal credentials.
8. **The local government/council tax scam:** Fraudulent emails impersonating local government authorities or tax agencies, demanding immediate payment of fictitious taxes or fines, preying on fear of legal consequences.
9. **Unusual activity scam:** Suspicious emails claiming to be from online accounts or services, warning users of unusual activity and urging them to click on links to verify their identities, aiming to steal login credentials or personal information.

The following breakdown is taken from an actual ‘Phishing’ attack which, similar to our [Smishing](https://www.alternativesec.xyz/SE101-Smishing_Attack_Overview_and_Breakdown) attack premise, the phishing email we're going to review targeted an individual user, using yet again, the pre-text or ‘lure’ of **urgency** and a **reputable provider**.

**The Phishing email:**

{% include image-caption.html imageurl="assets/images/posts/se101/Phish-email.png" title="Our Phishing Email" caption="Our Phishing email using an iCloud pretext/lure" %}

**Lets breakdown the email visually:**

{% include image-caption.html imageurl="assets/images/posts/se101/Phish-email-annotated.png" title="Phishing Email Breakdown" caption="Phishing Email Tell Tale Signs" %}

1. Sense of urgency and fear, e.g., fear tactics. Folks are attached to their photos!
2. Brand imitation, sender email is attempting to imitate Apple iCloud; however, the sender email address is `noreply@icloud.robert-howe.com`.
	1. `noreply` - nothing unusual here, a lot of orgs/companies use bulk sender addresses that start with `no-reply`.
	2. `@icloud.robert-howe.com`
		1. `icloud.` - attempt to reinforce believability; however this is actually a subdomain, as some of the more eagle eyed out there may have spotted!
		2. `robert-howe.com` - this is the actual top level domain and indicates beyond doubt that this email has not come from a legitimate Apple iCloud source address.
3. Flagged as Spam, but not as an attempted phishing email; however, this should still raise your concerns that this is indeed a phishing attempt.
4. Brand imitation, use of Apple iCloud icon for increased believability, along with a failure message; however, if  you look at the grammatical structure of the failure message, it also reads off, although grammatically it is correct!
	1. From a well know and high profile brand such as Apple, I would have expected something like this, for example:
		1. *"Failed to process payment when renewing your iCloud storage subscription."*
5. Storage capacity, this looks off based on the details e.g., 48.9 out of 50GB.
	1. Would Apple really make a simple user interface / user experience error like this??
6. Font used is 'Comic Sans', which is very rarely, if ever, used in business communications from high profile brands.
	1. *Have you ever seen any legitimate business communications using Comic Sans font type to convey information?*
7. 'Full' indicator button. Again, the use of fear and urgency tactics, with the colour red. The colour red is regularly associated with stop, danger, fear, anger, which consequently induces some form of quick response/action.
8. Expiration date, again continuing to build on the sense of urgency and fear tactics. Basically attempting to convey that if you don't take action by this date you could lose everything!

One thing to note, was that, the entire email body was 'clickable', as when the mouse hovered over any part of the email body, the remote server URL was displayed at the bottom of the screen, as identified by **point 9** and the red box outline:

{% include image-caption.html imageurl="assets/images/posts/se101/Phish-email-remote-url-closeUp.png" title="Redirect URL" caption="Redirect URL to malicious remote server" %}

9. Redirect URL to remote malicious server via Google ???

Now, it is a little difficult to read; however, **point 9** and the **red box** are depicting a remote/redirect address linked to `https://storage.googleapis.com`, weird right? Why would apple be using Google? Well they aren't, this in fact is the first of 2 redirect URLs which eventually land on a fake iCloud login portal:

{% include image-caption.html imageurl="assets/images/posts/se101/Fake-iCloud-Portal.jpg" title="Fake iCloud Portal" caption="Malicious iCloud login portal and credential harvester" %}

10. Bogus URL, although it looks to have a valid SSL Cert due to the green padlock, the URL being used it not correct. The legitimate iCloud URL is: `https://www.icloud.com/`
11. Brand imitation, continuing with the façade of imitating Apple iCloud. Though this is not what the actual portal looks like at all!
12. Credential harvester, to capture users login details, which will then redirect you to a page of the threat actors choosing or the legitimate page

All in all, many of you may have flagged this as a phishing email or are wondering how folks would fall for this; however, folks still do and are! Especially folks who may not be as 'tech savvy'.

When you think about it, the actual lure itself is very emotive, I mean who would want to potentially lose access to all there photos, backups and files right? This feeling of fear and impending loss is enough to make some folks do something they know they shouldn't e.g., click the link and submit their iCloud login details, which could ultimately result in the compromise of their account, if the targeted user doesn't have MFA enabled..

Lets end the breakdown with a little bit of fun! Would you be able to identify and spot any of the following emails as phishing emails:

{% include image-caption.html imageurl="assets/images/posts/se101/CHASE-phish.jpg" title="Chase Email" caption="Financial Phish: CHASE Bank" %}

{% include image-caption.html imageurl="assets/images/posts/se101/CapOne-Phish.jpg" title="CapitalOne Email" caption="Financial Phish: Capital One Credit Card" %}

{% include image-caption.html imageurl="assets/images/posts/se101/NetFlix-Phish.jpg" title="Netflix Email" caption="Streaming Service Phish: Netflix" %}

{% include image-caption.html imageurl="assets/images/posts/se101/AWS-ShippingConf.png" title="Amazon Shipping Email" caption="Online Shopping Phish: Amazon Shipping Notification" %}

*Note: this above Amazon email, in this instances, was/is indeed a phishing email, with the malicious links subtlety disguised as the 'Order #' and the 'tax and seller information*
## So, how can we Protect Ourselves from Phishing Attacks?

We all know and have heard about email phishing, the dangers of it and what to look for, and that if it ultimately feels ‘off’ we call it out; however, a lot of folks out there still don't for one reason or another!

So, it is important that we continue to promote phishing awareness and protecting ourselves from 'Phishing' attacks. Depending on the targeted user’s ability to identify a phishing attack and ignore or report the message, here are some simple steps, as an individual, to be mindful of:

- **Check** the Sender email; Look to ascertain or verify that the email is coming from the actual domain/business the email is implying.
- **Check** the message, grammar, spelling and structure
- **Don’t** click on any links which you are unsure of the origin or validity
	- Use your mouse to **hover over, but not click** the email body and/or links within the email. This usually, but not in all instances, provides an insight in the remote URL.
	- In phishing emails, these more often than not, point to a HTTP unencrypted website and/or login portal. As such, looking up site information can be difficult or obfuscated by layers of proxies and redirects.
	- more sophisticated threat actors may use HTTPS and have valid SSL certificates; so keep this in mind, a general rule of thumb is, **if in doubt, chuck it out!**
- **Don’t** send anyone private information via email
- **Don’t** send anyone financial information via email
- **Don’t** make and bank or financial transfers. Always check with the actual organisation or vendor first using their legitimate service, app or contact details.
- Don't make any purchases for gift certificates/store cards _e.g. Amazon, Apple…_
- **Don’t** download malicious programs/software to a smartphone or other hardware devices if asked to do so via email.

A note for **Corporate Users**: If you work within a corporate environment, your current organization may have security awareness programs, which covers topics such as Phishing and Social engineering. As such this would be a great place for corporate/business users to seek help and understanding.

In addition to the above point, there are several technological solutions which can also prevent, or act as defence in depth:

- **Email Filtering:** Many email services and providers now provide ‘Email filtering’ options to identify and block, or flag suspicious email’s. This can be based on the email content, links, files, originator email address, domain or all of the above.

- **Multifactor Authentication (MFA):** Utilizing MFA is an additional protective layer, will serve as an additional layer of defence and can prevent a threat actor from using credentials obtained through a ‘Phishing’ attack.
## Closing Points

Anyone with a device, such as a computer, laptop, smartphone or tablet, can receive email messages, from anywhere in the world, via any the inbuilt email platform or specific vendor apps e.g., Outlook, Gmail, along with various other supported applications.

Many users are already aware of the dangers of clicking a link in email messages; however, users/people, still fall foul of this attack vector.
### How to Spot a Phishing Email

In the past, identifying phishing emails was relatively simple. They often arrived with obvious red flags, such as requests from a "insert_your_prince_here" seeking financial assistance in exchange for promised wealth.

Nowadays, cybercriminals have evolved their tactics, investing considerable effort into crafting convincing emails that appear legitimate, often mimicking communication from friends or trusted institutions like banks. These sophisticated attackers may even conduct research on their targets, incorporating personal details into their messages to increase the likelihood of successful deception and prompting recipients to click on malicious links or attachments.

The following steps can be taken to help spot a phishing email:

- **Sender Email Address Inspection**:
	- Examine the sender's email address closely; however, ensuring that you do not inadvertently click on any other links within the email whilst doing so. Inspecting the the sender address can reveal whether the sender is legitimate.
	- Cybercriminals often use public email services like gmail.com, outlook.com and others. Legitimate emails from banks or companies typically come from company email accounts bearing the company's name.
		- Note that the displayed email address may differ from the actual sender's address; to verify, hover over/click on the sender's email name at the top of the email.
	
- **Request for Secret Information Verification**:
    - Exercise caution where an email requests details or verification of details, such as personal information, bank details or passwords.
    - Legitimate organizations will never solicit such information via email; any email doing so is likely a phishing attempt.

- **Suspicious Attachments**:
    - Avoid opening unexpected emails or attachments from unknown or unsolicited senders, as they may contain malware capable of compromising your computer and stealing personal data.
    - As a side note, always ensure your devices anti-virus and threat detection software/services are up-to-date and enabled. As they should provide another layer of security and apply a defense in-depth principle toward you and your device.
    
- **Creation of Urgency**:
    - Phishing emails often induce urgency by claiming suspicious activity on your account or impersonating someone in need of urgent financial assistance. Beware of such tactics and verify the authenticity of the sender through established contact details or official websites.

- **Unrecognized Website Links**:
    - Be cautious of clicking links within emails, as phishing emails may redirect you to fraudulent websites and login portals.
    - Hover over the link to reveal the **true** URL, which may be misspelled or entirely different from what you expect.
    - Always verify before clicking.

- **Poor Spelling and Grammar**:
    - Phishing emails often exhibit poor writing quality, including spelling mistakes and grammatical errors.
    - Take note of any deviations from the sender's usual writing style, as these can be indicators of a fraudulent/phishing email.
### General Awareness

The following general steps can be taken to help prevent being exploit:

- **Ignore:** If it looks too good to be true and/or the message is unsolicited, ignore, report and delete.  For example, Email messages offering quick money from winning prizes or collecting cash after entering information.

- **Remember:** Financial institutions will never send an email asking for credentials or a money transfer. Never send credit card numbers, ATM PINs, or banking information to someone via email messages.

- **Avoid:** avoid responding to a emails that you don’t recognize or, at the very least, if received on a work device, contact your IT security team and forward them email to them to asses. Also see the point below.

- **Awareness:** Make an effort to stay up to date with current phishing tactics and threats. Awareness can be your first line of defense. As an individual this maybe seem like a daunting task; however, your current organization may have security awareness program which covers topics such as this, as such this would be a great place to seek help and understanding. Alternatively, seeking knowledge online from reputable providers can also be another great option.

As users, in an interconnected digital age, we are inherently trusting of email, despite the news about cyber attacks originating from a phishing email, as this is normally the main means of communications between, businesses, colleagues and in some cases where family and friends are geographically displaced, so ‘Phishing’ is often lucrative to attackers seeking to build rapport and obtain credentials, banking information and private data.
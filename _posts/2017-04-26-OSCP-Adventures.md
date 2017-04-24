---
layout:     post
title:      OSCP Adventures
date:       2017-02-16
author:     SecEventsPen
summary:    OSCP write-up.
categories: AlternativeSec
thumbnail:  info-circle
tags:
 - 2017
 - OSCP
 - Offensive Security
 - write-up
 - Exam
 - Alternativesec
 - New
---

![Hacker](/images/OSCP/Hacker-pic.jpg)

I'll start by saying that, unfortunately, I didn't receive my Offensive Security Certified Professional (OSCP) certification on this occasion.

![Oops](/images/OSCP/Mistake.jpg)

The build up, lab time, trials and tribulations are almost like a 'right of passage' to obtain the OSCP certification. My decision based  to take the exam was based on improving my abilities as a tester and I can say that this is a professional education experience unlike anything most will have ever undertaken.

Okay, so a quick heads up as to what you get when you sign up (this has been covered many times before, so I'll not reinvent the wheel):

- The OSCP certification is the culmination of a course called Pen-testing with Kali (PwK).

What you get when you register/sign-up for the course:

- A Pen Testing with Kali Lab guide. This weighs in at around 350+ page PDF document.
- A wealth of media files that go hand in hand with the PDF lab guide.
- Access to the OSCP student forums.

The coursework outlined in the PDF guide is self paced and includes exercises at the end of most of the sections. The lab guide covers all aspects of a penetration test from information gathering to post-exploitation, complete with some tools and processes that can be used in each of the stages of a penetration test.

OK so that's that....

**The OffSec labs and certification...**

The course, lab challenges and exam are known to require a lot of out of the box thinking to overcome obstacles and I can definitely testify to this! If you're thinking of signing up to be a student of this course, you will need to make a commitment to put the work in, scheduling at least a couple of hours each day in the evenings and weekends. Being able to make this commitment voluntarily will ensure you have a higher chance of success! If you're used to being self-taught, using self paced courses over instructor led training and interaction then this should come easily to you.

On a whole there is very little structure or guidance for making your way through the labs and completing this course. This underpins and illustrates that you really DO have to take ownership of this course, no else is going to do it for you, put the pieces of the puzzle together and really think like a penetration test .. cough 'hacker'... to be successful in gaining certification through the Offensive Security OSCP.

If any of the above sounds like a bad thing, the OSCP is probably not for you. As penetration tester I had to have a long think about things before signing up. I have a family, like most folks do, and have to make time for everything that entails, as well as work. Factoring OSCP in the equation, means ultimately sacrificing time elsewhere ... that’s just life unfortunately! It is very important to be honest with yourself and really assess whether you can make this commitment so that you do not waste your time (which is precious enough as it is) and money that will ultimately end in disappointment with what is an incredible course.

You may not see this now, but the lack of guidance throughout the labs is a right of passage of the OSCP experience, everyone goes through it and this forces you to figure things out of your own! In the real world, a hacker, shady bad guy or someone who's just down right malicious would be figuring out the target environment on their own.

**Try Harder.... This phrase will plague you, but in a good way!**

If you ask anyone, or are familiar with Offsec, then you're probably already aware of the infamous motto (some may say troll) of the Offsec forum, IRC channel and its support staff is "Try Harder.". Most requests for help are met with this reply. While the OSCP forum is an avenue to allow student to raise questions and possible receive a "helpful" nudge along the way for almost every machine in the lab, most of the post are either people are venting frustrations and troll like jokes than actual hints! In just about every case, as like so many before me, the 'penny' only drops regarding the hint after completing that specific machine.

One of the unique aspects about the OSCP course and lab environment is that, student's are not just taught how to use a tool! A student is expected to know what it does, how it does it and then have you apply that tool to enumerate/interact with or exploit a box. If you don’t know something, you're expected to take it upon yourself to learn it and then apply it! This really trains you to think differently about a problem and put yourself in an evil doers/hacker's shoes so that you can assess the environment. If you only apply the tools depicted in the lab documents and video training, opportunities to excel in the lab will be painful and slow. That said, working with a defined set of tools to achieve an objective shows hard work and commitment in its own right!

The course promotes and teaches you from the outset how to leverage a way of thinking outside the box, this ultimately leads to compromising and rooting most of the boxes in the lab and a rewarding sense of achievement! I did spend a very large percentage of my time, when not working in the labs, using our old faithful friend Google to try to gather details and information that related to a machine I was trying to break into! The Internet is a gold mine of information which you will definitely need to use to obtain information on some aspect of a machine, configuration of service.

***TOP TIP 1: Enumerate, Enumerate, Enumerate !!! In fact this has become my second motto of this course (unofficially of course).***

***TOP TIP 2: Keep detailed and accurate notes as you go! It’s worth noting things that you tried but that didn’t not work. This will be helpful in the future, trust me!***

***TOP TIP 3: If you can, write up you lab report as you go along or a frequent intervals. You'll thank me for this!***

**The Exam....**

When I decided to schedule my exam, it was just after my lab time had come to an end. Before I decided to buy more lab time I thought I would give it a shot. I preformed pretty well in the labs and exploited and rooted a number of boxes with various scenarios. This maybe wasn't the best approach, though it's what I decided to go for!

The exam is a 24-hour practical application examination where you are given IP addresses, a few pointers on what you need to collect from each target and that's about it for direction. The goal being to compromise and gain access to each of the target hosts to recover a trophy or trophy files, depending on the target. Each host is given a numerical points value and just like of old, the higher the points means generally the more steps involved or harder the target is. When you receive the information at the start the exam, you're told how many points you need to pass.

What was new to me was that you are actually given 23 hours and 45 minutes. Make sure you keep an eye on you time!

Once the exam itself is completed, you have a further 24 hours to complete a written report that details a handful of machines that were rooted in the lab, your coursework exercises (optional, but worth it if you took heed of TOP TIP's 2 & 3. Its an extra 5 pts if you do) and, of course, the machines that were compromised in the exam.

**Exam Preparation....**

General tips for exam preparation:

Identify your weaknesses in the labs and really reinforce those principles. Buffer overflows and the more advanced web app attack vectors were the biggest things I worked on during my break between lab times. Sort out anything you think you'll need the day before i.e. additional files, common exploits and bookmark useful info then centralise it, making it easily accessible.

- With any exam make sure you get enough rest the night before. You'll have picked your allotted started date and time, don’t lose track of that. The exam times and available slots vary and can start at odd times.

- Sort your prep out the day before, a decent playlist is a must, and have water and snacks readily available too! The exam is intense and staying hydrated and nourished can be harder than it sounds if you are like you become like 'a dog with a bone' for the task at hand. .

- Schedule breaks. Easier said than done and I fell foul off my own rule by not sticking to it! Even if you find you are stuck or you have almost popped a box, that next breakthrough might be another hour or two away. You can really benefit from stepping away and clearing your mind, especially if you are struggling (and you will, everyone does).

- Don’t fixate/rabbit holes - Do not spend a large number of hours on working on your first box (like me). By now you should have your own methodology and what the course teaches you is to follow a methodology. If something just is not working, move to something else and come back later on.

- Enumerate, Enumerate, Enumerate!!! Then enumerate some more! All to often I made the statement "I've enumerated as much as I can!" (You’ll say this to!) And in all honestly, I always found something else by changing my search term or approach!

**Build up and Exam attempt....**

I bought a total of 60 lab days. The majority of my lab time was carried out in the evenings, weekends and holiday periods etc., all while juggling work and family life (work pays the bills and no-one likes to disappoint the wife and kids!). Most week day evenings I would spent on average 3-4 hours per night, at least 3 nights a week. Weekend lab time was juggled around family life, though generally I would average about 10hrs over the weekend.

I started off pretty slow, taking the first 5 days of lab time going through the lab PDF and carrying out the lab exercises. After that I jumped straight into the main labs. I decided to adopt the approach and idea of not using Metasploit's pre-built attack modules to automate the compromise/privilege escalation of a host.

***TOP TIP 4: You can only use Metasploit once in the exam, no point relying on it early from the get go!***

This led to a good few days of enumeration and research before I popped my first box! Though when I did, I understood the method, the exploit, how the code worked and why it worked! This gave me a great sense of achievement! Once into the manual exploitation swing of things, compromising hosts became quicker!

I made decent head way through the lab over the first 30 days, rooting a variety of hosts. The last 30 days though proved more difficult with progress slowing down dramatically due to work, family life and the difficulty level on the remaining hosts. I re-read the course material and just could not find a foothold in any of the machines.

If like me, you bought one of the packages (or are going to) i.e. 30, 60, 90 days, then your first exam attempt is included. Due to some long standing commitments I had to book my exam for a date several weeks after my lab time ended but I scheduled and took an exam to see just how at what level I was at and potentially how far off I was.

I managed to successfully complete 2 out of the 5 exam questions I was given, gaining an initial shell and subsequent root level privilege to get the max points for those questions. After that I spent the remaining exam time trying to figure out how to gain a foothold or low privilege shell on the remaining hosts to gather more points.

Ultimately I didn't score enough points to pass on this occasion and I chose not to submit any reports.

![Sad](/images/OSCP/Sad-box.jpg)

Not passing is a little disappointing but, realistically it was great learning experience, one I have come away from with a lot of valuable information. This information will enable me to progress and work towards my next attempt, though more importantly a better all-rounded pen tester!

**What now...**

I'll be have a few days away from labs, Vulnhub and studying, as in the last few months I've sat and passed other exams and I fancy a little down time. Though in anticipation, I have blown the dust of the following books and listed one other that I intend to purchase:

Nmap Network Scanning by Gordon Fyodor Lyon

Network Security Assessment by Chris McNab (3rd Edition highly recommended)

The Web Application Hackers Handbook by Dafydd Stuttard and Marcus Pinto (also a great book)

The Hackers Playbook 2 by Peter Kim

Gray Hat Hacking: The Ethical Hackers Handbook by Daniel Regalado

Black Hat Python by Justin Seitz - Purchasing this

I will also be getting more interactive with my peers aby continuing to volunteer for security conference such as Bsides, 44Con, SteelCon.

**Wrapping things up...**

As much as I want to give pointed advice above instead of only a review and general tips, I believe I am carrying on a long tradition of helping those that are really interested in earning their OSCP in "Trying Harder." The important thing to remember is that many others have actually gotten the certification before you and it is possible. The course is going to be easier if you have been a penetration tester for five years already. If you are like me, you just have to keep trying harder and failing and training yourself until it "clicks." Do not be ashamed to try an exam and fail. The course is purposely very difficult.

The OSCP is so difficult because it has an uncompromising bar that you have to surpass to obtain it.  You can only lean on friends and colleagues so much, for advice and information, there are study groups etc. Neither can you just memorise your way through this type of exam. What you do have to do, of your own free will and accord, is reach a certain level and apply that knowledge in an exam environment that changes every time just like the real world. You must demonstrate these abilities and everything you have learnt/know at every step of the way to pass. I am just not at that stage right now and neither am I ashamed or embarrassed to say it either!

Overall, I would highly recommend this certification to anyone looking to further their career in penetration testing and the broader cyber security field. What you learn from the OSCP labs and exam is invaluable! In addition,

I would just like to thank all the folks who put up with me over that last 3 months, for all the questions asked, gentle nudges in the right direction, my wife, family and finally Offensive Security, for an incredible, frustrating, educational experience that is the road to obtaining the OSCP Certification!

I'll be coming back OffSec and I’ll be trying harder!

![Try](/images/OSCP/Try-Harder.jpg)

Further information on the Offensive Security PWK course can be found [HERE.](https://www.offensive-security.com/information-security-training/penetration-testing-training-kali-linux/) 

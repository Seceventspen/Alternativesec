---
layout: post
title: 'Dir-Generator: An aid to bring order to chaos'
tags: [Pentest, tool]
featured_image_thumbnail: assets/images/posts/dir-gen/order-chaos.jpg
featured_image: assets/images/posts/dir-gen/order-chaos.jpg
featured: true
hidden: true
---

Dir-Generator: An aid to bring order to what can be the chaos of organising your engagement data.

This short blog post will talk through a small penetration testing aid I wrote in Python, **Dir-Generator**, which automates the creation of a pentest engagement folder and series of complimentary sub folders, to aid in the organization and storage of engagement related data, images, logs, payloads, etc. gathered throughout the engagement.

<!--more-->

Keeping notes is one of the key aspects of penetration testing, keeping notes that are logical, organized, easily referenceable and can be used by others with no prior knowledge or uplift, is a skill. As such, over my years of testing, I've opted to prioritize organization and structure.

I used to create things as I went, a folder for this, a note for that, which don't get me wrong, isn't a bad or incorrect way of doing things, it's just not the most efficient way of doing it, though it's better to do this this way rather than not at all.

So, I got tired of doing the same thing over and over, and decided to make my life easier, sorry, more efficient, and automate the task of something I would do regularly _(much like my reason for [automating Kali EC2 builds using AWS Cloudformation](https://www.alternativesec.xyz/Kali_in_the_cloud))_.

Hence the creation of [DirGenerator.py](https://github.com/Seceventspen/Dir-Generator) which can be found on my GitHub.

![dg-logo](assets/images/posts/dir-gen/dir-gen-logo.png)

Dir-Generator is written in Python and is a simple script cross-platform script, which works on both Linux and Windows. I've not tested on Mac/OS X, but its' Python code, so should work as long as the code is amended to match the output directory on OS X _(see noted below)_

_Note: Line 57 of the code has a hardcoded Windows path on for: `C:\\Pentests\\Engagements\\`. Though you can adjust this to anywhere you wish before running the script and your output directory will be created there instead._

Dir-Generator is designed to facilitate the creation of testing directories for penetration testing engagements, providing a structured approach to organizing your work. The following commands demonstrate the outcome based on user supplied command flags:

- **Windows**: `python.exe dir_generator.py -n ACME -m Admin,Reporting,Ext_Inf,Int_Inf`

- **Linux**: `python3 dir_generator.py -n ACME -m Admin,Reporting,Ext_Inf,Int_Inf`

Here's a breakdown of the flags used:

`-n`: Specifies the engagement name. This argument is required.

In our exmaple case, we've provided the value `acme`.

`-m`: Allows you to specify methodologies for the engagement. Methodologies should be provided as a comma-separated list of options. If not specified, the script defaults to using all available methodologies.

In our example we've opted for: `Admin`,`Reporting`,`Ext_Inf` and `Int_Inf`.

Other options which can be selected are: `OSINT`, `Web` and `API` _(note: I've kept things modular, so that additional options can be added to the accompanying dictionary file to extend the capability of the script)._

![usage](assets/images/posts/dir-gen/dir-gen.png)

The script also has some logic built in to check for an existing folder with the same name.
For example, if we try to create the same client folder again, e.g., `acme`, we'll get the following response:

![usage](assets/images/posts/dir-gen/dir-gen-dup-chk.png)

Organized and structured data is important, because it can be a valuable point of reference when it comes to report writing, retesting or retrospective lookups, say if a client queries something done further down the line.

Just because something isn’t relevant today, doesn’t mean it won’t be at some point, so starting out with a logical, organized and structured approach is setting yourself up for success. You'll also save a lot of stress!

Whether you're a Penetration Tester, Red/Blue Teamer, Security analyst, or simply organizing your projects, this script streamlines the process of setting up directories for different methodologies within an engagement and in truth could be forked and used for your own purposes outside of penetration testing, with a little tweaking of the code.

"Dir-Generator" isn't groundbreaking granted, but hopefully you might find it useful to automate this task or see your own use for the code and tweak it accordingly.

Thanks for reading!
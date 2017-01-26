---
layout:     post
title:      RDP Sec Check Tool
date:       2017-01-26
author:     SecEventsPen
summary:    New RDP/NLA verification tool.
categories: Tools
thumbnail:  wrench
tags:
- How to
- Remote Desktop Services
- Portcullis
- RDP
- 2017
---

Following on from my previous blog post on **[NLA](https://www.alternativesec.xyz/pentesting/2017/01/02/NLA-How-to/)**, a tool to help with RDP enumeration has been suggested to me to explore. The tools name is ‘rdp-sec-check’ by Portcullis Labs.

Having surfed over to the Protcullis website to check out this tool I found a handy introduction to it. As expected it covers basically what the tool is and how it goes about its business. Obviously the name gives it away, ‘rdp-sec-check’, it's another tool for checking the RDP security configuration of a target host.
Some folks might already be saying, big deal, tools such as Nmap and its NSE script for checking RDP:

```nohighlight
nmap -p 3389 --script rdp-enum-encryption <Target-host>
```

and the likes of [XRDP](http://www.xrdp.org) etc can do this already and your initial thoughts you would be right; however, the Portcullis rdp-sec-check tool is not intended to replace the likes of this Nmap script or any type of manual verification, on the contrary, it is there to augment the testing of this service by providing additional context and continuity of any testing that is already underway or that has taken place.

Ok so here’s what Portcullis have to say about ‘rdp-sec-check’:

```nohighlight
rdp-sec-check is a Perl script to enumerate security settings of an RDP Service (AKA Terminal Services)

It does not require authentication, only network connectivity to TCP port 3389.
It can determine many (though not quite all) of the security settings from the RDP-Tcp Properties | General tab:
•	Check which security layers are supported by the service: Standard RDP Security, TLSv1.0, CredSSP.
•	For Standard RDP Security it detects the level of encryption supported: 40-bit, 56-bit, 128-bit, FIPS.
The following potential security issues are flagged if present:
•	The service supports Standard RDP Security – this is known to be vulnerable to an active “Man-In-The-Middle” attack.
•	The service supports weak encryption (40-bit or 56-bit).
•	The service does not mandate Network Level Authentication (NLA) - NLA can help to prevent certain types of Denial of Service attack.
•	The service supports FIPS encryption but doesn’t mandate it – may only be interesting for jurisdictions where FIPS is required.
```

So now we know about the tool and what it does, I guess it’s time to install it!

Not so fast for me ... It seems the tool has a dependency to ensure it works correctly. The Portcullis info mentions CPAN and BER module. What's CPAN and what's an Encoding::BER when you're at home???

**CPAN**

Before we can jump straight into using the tool, it seems we need to update/install an encoding module from the Comprehensive Perl Archive Network or CPAN as its commonly known! Now, if like me, you’re not to sure what CPAN is here’s a bite sized summary:

Cpan is a repository of more that 250,000 software modules and accompanying documentation for Perl.

The CPAN's main purpose is to help programmers locate modules and programs not included in the Perl standard distribution with the majority of CPAN being free and open source software.

More information can be found here **[CPAN-WIKI](https://en.wikipedia.org/wiki/CPAN)** and here **[CPAN-Website](http://search.cpan.org/faq.html)**

**Encoding::BER module**

So, what is this ‘Encoding::BER’ module you speak of? Ok, I’ll admit I had no idea what this was and other than what the information I’ve read over tells me, I still don't know much more than this:

*“The Encoding::BER - Perl module is used for encoding/decoding data using ASN.1 Basic Encoding Rules (BER)”*

So, basically to me (and possibly you), it allows us to take advantage of this perl module to encode/decode data. Plus, it makes the Portcullis rdp-sec-check tool work (which is really the main bit we care about at present!).

More information on the CPAN Encoding::BER module can be found here **[CPAN-Encoding::BER](http://search.cpan.org/~jaw/Encoding-BER-1.02/lib/Encoding/BER.pm)**

**Installing the module**

So not having worked much with Perl before (don’t hate me) or the CPAN repo, I’ll admit I was like ‘erm, I’m not really 100% on what or how to do this!’ So breaking it down lets sort the Cpan dependancy first. Fire up a terminal (depending on OS, you might need to sudo this command and the screen output may vary. I‘ve installed on both, a Kali rolling instance and Ubuntu 16.04 Lts and the process/screen output differed slightly) and type:

```nohighlight
$ sudo cpan
```

This new line should appear:

```nohighlight
cpan[1]>
```

After ‘cpan[1]>’ type 'install Encoding::BER:' like so:

```nohighlight
cpan[1]> install Encoding::BER
```

This will now begin to check and run through the install of the module. As mentioned above depending on system and whether you have carried out cpan updates before, the screen output and time to install may vary, though in the end you should see something along these lines:

```nohighlight
/usr/bin/make install  -- OK

cpan[2]>
```

OR

```nohighlight
DONE
cpan[2]>
```

Once we see this and assuming no errors popped up during the install, all we need to do now is exit the cpan service. This can be achieved by typing ‘exit’ after ‘cpan[2]>’ like so:

```nohighlight
cpan[2]>exit
```

You should be greeted with the following output or similar:

```nohighlight
cpan[2]> exit
Lockfile removed.
```

Now thats the CPAN dependency is taken care of, we can now move on to getting the rdp-sec-check tool. At the time of writing this blog post 26th January 2017, the most recent version of the tool is:

```nohighlight
rdp-sec-check-0.9.tgz
```

After searching Github and the Portcullis website, this is the most recent version available that I could find. The tool itself can be obtained in a few methods:

```
wget https://labs.portcullis.co.uk/download/rdp-sec-check-0.9.tgz

git clone https://github.com/portcullislabs/rdp-sec-check.git
```

Or by visiting *[HERE](https://labs.portcullis.co.uk/downloads/)* and browsing through the Portcullis download page.

I used the *'wget'* method and the file saved to my downloads location:

```nohighlight
:~$ wget https://labs.portcullis.co.uk/download/rdp-sec-check-0.9.tgz
--2017-01-26 10:22:29--  https://labs.portcullis.co.uk/download/rdp-sec-check-0.9.tgz
Resolving labs.portcullis.co.uk (labs.portcullis.co.uk)... 77.75.105.66
Connecting to labs.portcullis.co.uk (labs.portcullis.co.uk)|77.75.105.66|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13065 (13K) [application/x-gzip]
Saving to: ‘rdp-sec-check-0.9.tgz’

rdp-sec-check-0.9.tgz             100%[===========================================================>]  12.76K  --.-KB/s    in 0.005s  

2017-01-26 10:22:29 (2.63 MB/s) - ‘rdp-sec-check-0.9.tgz’ saved [13065/13065]
```

Next we need to extract the contents. If you’re following along with the install process and are not already in the same location where the file was downloaded to, change to that location now and then run:

```nohighlight
:~$ tar xvfz rdp-sec-check-0.9.tgz
rdp-sec-check-0.9/
rdp-sec-check-0.9/rdp-sec-check.pl
rdp-sec-check-0.9/COPYING.GPL
rdp-sec-check-0.9/COPYING.RDP-SEC-CHECK
```

Thats us pretty much ready to go; however, my OCD kicks in as I like all my tools all in the same location. So I move the new ‘rdp-sec-check-0.9’ directory to my /opt directory (though this is personal preference and not required). I’m sure you all already know how to do this anyway!

```nohighlight
$ sudo mv rdp-sec-check-0.9 /opt
```

Within the /opt directory should now be the your newly moved ‘rdp-sec-check-0.9’ directory!

From here its just a matter of running the tool:

```nohighlight
$ cd /opt/rdp-sec-check-0.9
$ ls
COPYING.GPL  COPYING.RDP-SEC-CHECK  rdp-sec-check.pl
```

Run the tool:

``nohighlight
$ ./rdp-sec-check.pl
Starting rdp-sec-check v0.9-beta ( http://labs.portcullis.co.uk/application/rdp-sec-check/ )
Copyright (C) 2014 Mark Lowe (mrl@portcullis-security.com)

./rdp-sec-check.pl [ options ]  ( --file hosts.txt | host | host:port )

options are:

  --file hosts.txt	targets, one ip:port per line
  --outfile out.log	output logfile
  --timeout sec		receive timeout (default 10s)
  --retries times	number of retries after timeout
  --verbose				
  --debug
  --help

Example:
         ./rdp-sec-check.pl 192.168.1.1
         ./rdp-sec-check.pl --file hosts.txt --timeout 15 --retries 3
         ./rdp-sec-check.pl --outfile rdp.log 192.168.69.69:3389
         ./rdp-sec-check.pl --file hosts.txt --outfile rdp.log –verbose
```

Here’s some sample output from the tool when used on an engagement against hosts which had active remote desktop services:

```nohighlight
Starting rdp-sec-check v0.9-beta ( http://labs.portcullis.co.uk/application/rdp-sec-check/ ) at Mon Jan 16 14:16:37 2017

[+] Scanning 31 hosts

Target:    10.1.1.131
IP:        10.1.1.131
Port:      3389

[+] Checking supported protocols

[-] Checking if RDP Security (PROTOCOL_RDP) is supported...Supported
[-] Checking if TLS Security (PROTOCOL_SSL) is supported...Supported
[-] Checking if CredSSP Security (PROTOCOL_HYBRID) is supported [uses NLA]...Supported

[+] Checking RDP Security Layer

[-] Checking RDP Security Layer with encryption ENCRYPTION_METHOD_NONE...Not supported
[-] Checking RDP Security Layer with encryption ENCRYPTION_METHOD_40BIT...Supported.  Server encryption level: ENCRYPTION_LEVEL_CLIENT_COMPATIBLE
[-] Checking RDP Security Layer with encryption ENCRYPTION_METHOD_128BIT...Supported.  Server encryption level: ENCRYPTION_LEVEL_CLIENT_COMPATIBLE
[-] Checking RDP Security Layer with encryption ENCRYPTION_METHOD_56BIT...Supported.  Server encryption level: ENCRYPTION_LEVEL_CLIENT_COMPATIBLE
[-] Checking RDP Security Layer with encryption ENCRYPTION_METHOD_FIPS...Supported.  Server encryption level: ENCRYPTION_LEVEL_CLIENT_COMPATIBLE

[+] Summary of protocol support

[-] 10.1.1.131:3389 supports PROTOCOL_HYBRID: TRUE
[-] 10.1.1.131:3389 supports PROTOCOL_RDP   : TRUE
[-] 10.1.1.131:3389 supports PROTOCOL_SSL   : TRUE

[+] Summary of RDP encryption support

[-] 10.1.1.131:3389 has encryption level: ENCRYPTION_LEVEL_CLIENT_COMPATIBLE
[-] 10.1.1.131:3389 supports ENCRYPTION_METHOD_NONE   : FALSE
[-] 10.1.1.131:3389 supports ENCRYPTION_METHOD_40BIT  : TRUE
[-] 10.1.1.131:3389 supports ENCRYPTION_METHOD_128BIT : TRUE
[-] 10.1.1.131:3389 supports ENCRYPTION_METHOD_56BIT  : TRUE
[-] 10.1.1.131:3389 supports ENCRYPTION_METHOD_FIPS   : TRUE

[+] Summary of security issues

[-] 10.1.1.131:3389 has issue SSL_SUPPORTED_BUT_NOT_MANDATED_MITM
[-] 10.1.1.131:3389 has issue WEAK_RDP_ENCRYPTION_SUPPORTED
[-] 10.1.1.131:3389 has issue FIPS_SUPPORTED_BUT_NOT_MANDATED
[-] 10.1.1.131:3389 has issue NLA_SUPPORTED_BUT_NOT_MANDATED_DOS
```

*NB: The above IP address and any identifying information has been removed/altered to protect the integrity of the client tested.*

Well thats about it folks, I hope you enjoyed the read and or found this article useful! I plan to make regular use of this tool, maybe you will too!

Thanks for reading and if you have any comments you can get me here on [Twitter](https://twitter.com/SecEventsPen) or via *[email](mailto:seceventspen@alternativesec.xyz)*

If you want the more official line on the Portcullis 'rdp-sec-check' tool if can be found here:

[Portcullis rdp-sec-check](https://labs.portcullis.co.uk/tools/rdp-sec-check/)

If you find it useful, don’t forget to show them some love for their awesome work!

Thanks for reading!

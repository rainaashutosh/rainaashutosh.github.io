---
layout:                     single
title:                      "Rekall Memory Forensics Suite Installation"
categories:                 [Memory Forensics,Rekall]
header:
    excerpt:                "Memory Forensics & Rekall"
    teaser:                 https://n00bt0l33t.files.wordpress.com/2017/10/rekall-logo-stacked.png
---

# Rekall Memory Forensics Suite Installation – Windows
This is my first post in Memory Forensics category. In this blog post I ll cover what is Memory Forensics and how to start using [Rekall](http://www.rekall-forensic.com/).

Memory Forensics is the art of using memory dump/image to determine the overall state of the computer (like the list of running processes, threads , loaded libraries etc..). Its mainly used in cyber security incident response analysis or to diagnose operating system/process crashes.

Memory forensics is useful when analyzing criminal activity such as hackers or insider threats. Through the practice of memory forensics, experts are supplied with run time system activity, such as open network connections or recently executed commands &processes. Before programs are executed on the computer, they are loaded into the memory making the use of memory forensics of high importance. Each program or data which is created, examined, or deleted is stored in the RAM. This includes images, all web-browsing activity, encryption keys, network connections, or injected code fragments. In many instances, certain artifacts can only be found in the RAM, such as open network connections present during the time of the crash. Attackers can develop malware which only resides in the memory, rather than the disk, making it virtually invisible to standard computer forensic methods. This makes the need of memory forensics tools in high demand.

Prior to 2004, generic tools such as strings and grep were used to perform memory forensics (which was clearly very hard to use and was ineffective too).  In 2004, Michael Ford first used the term ‘memory forensics’ and described memory forensics through the use of a rootkit. As attacks have evolved and become more complex, the need for memory forensic tools has increased. The common methods of firewalls and anti-virus tools do not have the ability to detect malware or critical data through the RAM. The best and complex tools have the ability to identify malware, rootkits, and zero days in the RAM. [The Volatility Framework](https://code.google.com/archive/p/volatility/) is one of the commonly known tools used by the industry experts. It is a Python based, open source collection of tools that allows the examination of volatile data in the computer’s memory dump. This framework offers new techniques and procedures for experts to use when extracting digital data.

By this time you must be wondering why have I chosen Rekall framework over Volatility.

Rekall Forensics Framework is maintained by Google and this project was forked from volatility.

I personally feel that Rekall is better than Volatality because:
1. It can be used to do live memory analysis and can analyze Advance Forensics File Fomat 4 (aff4) dumps.
2. Much faster and modular as compared to volatility.
3. Most of the basic functionality of volatility is already present in rekall.
4. It has inbuilt Memory Acquisition module
5. Rekall’s approach to memory analysis is unique – Rekall leverages exact debugging information provided by the operating system vendors to precisely locate significant kernel data structures. While other tools rely on heuristics and signatures, Rekall aims to be the most stable and reliable memory analysis framework.
6. Rekall maintains the largest [public profile repository](https://github.com/google/rekall-profiles) for many operating system versions.

Following are the steps to configure rekall on windows/linux machine . Upon installation you can either to live memory analysis or do analysis on memory dumps. You can use any version of python with Rekall , but ideally it is suggested that you use Python 3.7. For the simplicity, all the steps shall remain same for any version of python installed.

1. Install Python 3.7(or 2.7) on your endpoint.
2. Install virtualenv from pip.
3. Create a new virtual environment and activate it.
```bash
#installs virtualenv package
pip install virtualenv
#Create a virtual Environment
python -m virtualenv RekallDevelopment
#Activate virtual environment
RekallDevelopment\\Scripts\\activate
```
4. In Linux, virtual enviroment is activated by RekallDevelopment/bin/activate
5. Now run the command : `pip install rekall`
6. To start rekall in live memory mode run the command [As elevated user]: `rekall --live Memory`
7. You should see a console like this. Run commands like pslist, dlllist to see running processes and loaded assemblies.<br>![RekallConsole](https://n00bt0l33t.files.wordpress.com/2017/10/rekall-demo-e1508511920599.png?w=700)

In my next post in Memory Forensics I ll go through basic Memory analysis of some malicious memory dumps.
# Intel ME: Evil Inside

## TLDR

- Intel ME is a piece of software installed inside every Intel Chipset since around 2008. It is in charge of various tasks, the most known one is remote out-of-band management through AMT.
- Intel ME is a very powerfull software that can potentially have full access to the computer and therefore your data.
- Intel ME is known to have various vulnerabilities and is suspected to be a backdoor.
- Intel ME cannot be fully uninstalled.

If you're deeply concerned about privacy, vulnerabilities in your CPU and you are willing to risk bricking your computer, maybe you'd like to disable some of Intel ME's features using me_cleaner.

## Introduction: Intel's All Powerfull Piece of Software

The Intel Management Engine is a piece of firmware stored inside every Intel processor since around 2008. It operates as the backbone of many other features, one of them is the Active Management Technology or AMT. There are a few important parts to understand about the Intel ME. 

First, it is closed source. That means, not really much is known about it. As a matter of fact, we didn't really care much about it until recently that it was found out it runs on MINIX 3. This created concern in the community because the fact that it runs on a full fledged (not actively supported) OS means there's vulnerabilities to be exploited. The fact that it closed source also means it could be a backdoor. This was the first theory by many, but it hasn't been proved yet.

Second, it has full control over your computer. It runs under any layer of protection you may have. It runs under the BIOS/UEFI and under your OS. So whatever operations Intel ME is doing, are not only unknown, but they are also all powerfull. Hence the reason Google wants it out of their servers. It can turn computers on and off. It has a web server and a TCP/IP stack. It has 3G technology to send information even when there's no internet access. Scared yet?

Third, it has plenty of vulnerabilities. Ever since the discovery of MINIX 3 inside the Intel ME, there's been a big effort in finding vulnerabilities. In my experience, usually finding a vulnerability for any type of software like this (say for example, the OS that runs inside a videogame console), is big news. Intel ME's vulnerabilities would be even bigger news, if it wasn't for the fact that it's plagued with them. A simple search will clarify this statement way better than 100 reference links below.

On a personal side-note, my favorite vulnerability is this one: [Reverse-engineering the Intel Management Engine’s ROMP module](https://puri.sm/posts/reverse-engineering-the-intel-management-engine-romp-module/) A vulnerability found just by reverse engineering it. Woao.

## Disabling Intel ME... partially

You cannot remove Intel ME. Attempting to do so can have several effects. The CPU either recognizes something is wrong and gives the user 30 minutes before shutting down the computer, or just bricks the CPU. 

## References
1. Garrett, Matthew. Intel's Remote AMT Vulnerability. Dreamwidth. [Online] https://mjg59.dreamwidth.org/48429.html. 
2. Sklyarov, Dmitry. Intel ME: The Way of Static Analysis. Positive Technologies. [Online] http://blog.ptsecurity.com/2017/04/intel-me-way-ofstatic-analysis.html. 
3. Intel. What is Intel Management Engine? Intel. [Online] https://www.intel.com/content/www/us/en/support/articles/000008927/softwar e/chipset-software.html. 
4. Portnoy, Erica and Eckersley, Peter. Intel's Management Engine is a security hazard, and users need a way to disable it. Electronic Frontier Foundation. [Online] https://www.eff.org/deeplinks/2017/05/intelsmanagement-engine-security-hazard-and-users-need-way-disable-it. 
5. Linux Foundation. Program Schedule. Linux Foundation Events 2017. [Online] http://events17.linuxfoundation.org/events/embedded-linuxconference-europe/program/schedule. 
6. Chan, Leon. Google Working To Remove MINIX-Based ME From Intel Platforms. Tom's Hardware. [Online] https://www.tomshardware.com/news/google-removing-minix-managementengine-intel,35876.html. 
7. Intel. Intel Active Management technology. Intel Software Developer Zone. [Online] https://software.intel.com/en-us/amt-sdk. 
8. Libreboot. Libreboot: Frequently Asked Questions. Libreboot. [Online] https://libreboot.org/faq.html#intel. 
9. Minnich, Ronald. Replace Your Exploit-Ridden Firmware with Linux. YouTube. [Online] https://www.youtube.com/watch?v=iffTJ1vPCSo. 
10. Corna, Nicola. me_cleaner. Github. [Online] https://github.com/corna/me_cleaner. 
11. Williams, Chris. How to remote hijack computers using Intel's insecure chips: Just use an empty login string. The Register. [Online] https://www.theregister.co.uk/2017/05/05/intel_amt_remote_exploit/. 
12. Tereshkin, Alexander and Wojtczuk, Rafal. Ring -3 Rookits. Black Hat Conference 2009. [Online] https://invisiblethingslab.com/resources/bh09usa/Ring%20-3%20Rootkits.pdf.
13. Alaoui, Youness. Reverse-engineering the Intel Management Engine’s ROMP module. Purism. [Online] https://puri.sm/posts/reverse-engineering-the-intel-management-engine-romp-module/. 
14. Ermolov, Mark and Goryachy, Maxim. Disabling Intel ME 11 via undocumented mode. Positive Research. [Online] http://blog.ptsecurity.com/2017/08/disabling-intel-me.html. 
15. Corna, Nicola. HAP AltMeDisable bit. me_cleaner @ Github. [Online] https://github.com/corna/me_cleaner/wiki/HAP-AltMeDisable-bit.
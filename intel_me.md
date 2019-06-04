# Intel ME: Evil Inside

## TLDR

- Intel ME is a piece of software installed inside every Intel Chipset since around 2008. It is in charge of various tasks, the most known one is remote out-of-band management through AMT.
- Intel ME is a very powerfull software that can potentially have full access to the computer and therefore your data.
- Intel ME is known to have various vulnerabilities and is suspected to be a backdoor.
- Intel ME cannot be fully uninstalled in modern computers.

If you're deeply concerned about privacy, vulnerabilities in your CPU and you are willing to risk bricking your computer, maybe you'd like to disable Intel ME's features using me_cleaner.

## Introduction: Intel's All Powerfull Piece of Software

The Intel Management Engine is a piece of firmware stored inside every Intel processor since around 2008. It operates as the backbone of many other features, one of them is the Active Management Technology or AMT. There are a few important parts to understand about the Intel ME. 

First, it is closed source. That means, not really much is known about it. As a matter of fact, we didn't really care much about it until recently that it was found out it runs on MINIX 3. This created concern in the community because the fact that it runs on a full fledged (not actively supported) OS means there's vulnerabilities to be exploited. The fact that it closed source also means it could be a backdoor. This was the first theory by many, but it hasn't been proved yet.

Second, it has full control over your computer. It runs under any layer of protection you may have. It runs under the BIOS/UEFI and under your OS. So whatever operations Intel ME is doing, are not only unknown, but they are also all powerfull. Hence the reason Google wants it out of their servers. It can turn computers on and off. It has a web server and a TCP/IP stack. It has 3G technology to send information even when there's no internet access. Scared yet? A more complete list of Intel ME's capabilities can be found [here](https://libreboot.org/faq.html#intel).

Third, it has plenty of vulnerabilities. Ever since the discovery of MINIX 3 inside the Intel ME, there's been a big effort in finding vulnerabilities. In my experience, usually finding a vulnerability for any type of software like this (say for example, the OS that runs inside a videogame console), is big news. Intel ME's vulnerabilities would be even bigger news, if it wasn't for the fact that it's plagued with them. A simple search will clarify this statement way better than 100 reference links below.

## Partial Disable of Intel ME

**Disclaimer: You can brick your PC doing this.**

You cannot remove Intel ME completely in modern computers (anything after Intel ME 6.0, which can be disabled entirely). Attempting to do so can have several effects. The CPU either recognizes something is wrong and gives the user 30 minutes before shutting down the computer, or just bricks the CPU. However, disabling it partially is possible with the help of [me_cleaner](https://github.com/corna/me_cleaner).

If you have Intel ME version 6.0 or below, you can disable Intel ME by installing LibreBoot. Some of the computers using this are the Thinkpad X200 and T400. More information on how to disable it using LibreBoot [here](https://libreboot.org/faq.html#intel)

Considering you have something above version 6.0, there are 2 ways of disabling Intel ME using me_cleaner. First of all, you need to set it up, [here](https://github.com/corna/me_cleaner/wiki/How-to-apply-me_cleaner) is the official guide, [here](https://www.youtube.com/watch?v=aRUxfxp9dJ8) is a video teaching how to do it and [here](https://hardenedlinux.github.io/firmware/2016/11/17/neutralize_ME_firmware_on_sandybridge_and_ivybridge.html) is another link with information.

Again, updated steps on using me_cleaner can be found [here](https://github.com/corna/me_cleaner), the official repo.

### The Rough One

The rough method works as follows: Intel ME is divided in multiple partitions, or known also as modules. Some of these modules are not fundamental, therefore can be deleted. Some of these are the network stack, a scheduler, API's, and nowadays also the ROMP module (the one with vulnerabilities one I mentioned above).

### The Soft One

There is a built-in functionality called High Assurance Platform (HAP) to disable Intel ME after it has loaded. This is officially stated by Intel as a feature requested by the NSA. Disabling it requires changing 2 bits in the configuration. Once the computer boots and the ME does the initial process, it gets turned off. This disables Intel ME, but once it has already loaded.

## Personal Conclussions

Intel ME is a very powerful tool, for those who want to get into someone else's information. It proves of little to no use to the average end-user, and it definitely poses a risk to those who care about their privacy and security. Disabling it comes at a great risk, since it can brick your computer.

On a personal side-note, my favorite vulnerability is this one: [Reverse-engineering the Intel Management Engine’s ROMP module](https://puri.sm/posts/reverse-engineering-the-intel-management-engine-romp-module/) 

A vulnerability found just by reverse engineering it. Woao.

## References
1. Garrett, Matthew. Intel's Remote AMT Vulnerability. Dreamwidth. [Online](https://mjg59.dreamwidth.org/48429.html). 
2. Sklyarov, Dmitry. Intel ME: The Way of Static Analysis. Positive Technologies. [Online](http://blog.ptsecurity.com/2017/04/intel-me-way-ofstatic-analysis.html). 
3. Intel. What is Intel Management Engine? Intel. [Online](https://www.intel.com/content/www/us/en/support/articles/000008927/software/chipset-software.html). 
4. Portnoy, Erica and Eckersley, Peter. Intel's Management Engine is a security hazard, and users need a way to disable it. Electronic Frontier Foundation. [Online](https://www.eff.org/deeplinks/2017/05/intelsmanagement-engine-security-hazard-and-users-need-way-disable-it). 
5. Linux Foundation. Program Schedule. Linux Foundation Events 2017. [Online](http://events17.linuxfoundation.org/events/embedded-linuxconference-europe/program/schedule). 
6. Chan, Leon. Google Working To Remove MINIX-Based ME From Intel Platforms. Tom's Hardware. [Online](https://www.tomshardware.com/news/google-removing-minix-managementengine-intel,35876.html). 
7. Intel. Intel Active Management technology. Intel Software Developer Zone. [Online](https://software.intel.com/en-us/amt-sdk). 
8. Libreboot. Libreboot: Frequently Asked Questions. Libreboot. [Online](https://libreboot.org/faq.html#intel). 
9. Minnich, Ronald. Replace Your Exploit-Ridden Firmware with Linux. YouTube. [Online](https://www.youtube.com/watch?v=iffTJ1vPCSo). 
10. Corna, Nicola. me_cleaner. Github. [Online](https://github.com/corna/me_cleaner). 
11. Williams, Chris. How to remote hijack computers using Intel's insecure chips: Just use an empty login string. The Register. [Online](https://www.theregister.co.uk/2017/05/05/intel_amt_remote_exploit/). 
12. Tereshkin, Alexander and Wojtczuk, Rafal. Ring -3 Rookits. Black Hat Conference 2009. [Online](https://invisiblethingslab.com/resources/bh09usa/Ring%20-3%20Rootkits.pdf).
13. Alaoui, Youness. Reverse-engineering the Intel Management Engine’s ROMP module. Purism. [Online](https://puri.sm/posts/reverse-engineering-the-intel-management-engine-romp-module/). 
14. Ermolov, Mark and Goryachy, Maxim. Disabling Intel ME 11 via undocumented mode. Positive Research. [Online](http://blog.ptsecurity.com/2017/08/disabling-intel-me.html). 
15. Corna, Nicola. HAP AltMeDisable bit. me_cleaner @ Github. [Online](https://github.com/corna/me_cleaner/wiki/HAP-AltMeDisable-bit).

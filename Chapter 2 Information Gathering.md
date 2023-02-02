
## Chapter 2 : Information Gatheing Tools

![photo](https://1.bp.blogspot.com/-E2VHLDdqkQc/XeDIKDLN-iI/AAAAAAAABZw/V16HyA_x4YoVSxJ-IJv5x3NgdpRIfvUtACLcBGAsYHQ/s1600/Kinghacker0.jpg)



# Information Gatheing Tools 


There is a saying that goes “The more information you have about the target, the more is the
chance of successful exploitation.” Information gathering is the first phase of hacking. In this
phase, we gather as much information as possible regarding the target’s online presence, which
in turn reveal useful information about the target itself. The required information will depend
on whether we are doing a network pentest or a web application pentest. In the case of a network
pentest, our main goal would be to gather information on the network. The same applies to web
application pentests. In this module, we will discuss numerous methods of real-world information
intelligence.

In general, all information gathering techniques can be classified into two main categories:

1. Active information gathering
2. Passive information gathering

# Active Information Gathering

In active information gathering, we would directly engage with the target, for example, gathering
information about what ports are open on a particular target, what services they are running, and
what operating system they are using. However, the techniques involving active information gath-
ering would be very noisy at the other end. As they are easily detected by IDS, IPS, and firewalls
and generate a log of their presence, and hence are not recommended sometimes.

# Passive Information Gathering

In passive information gathering, we do not directly engage with the target. Instead, we use search
engines, social media, and other websites to gather information about the target. This method
is recommended, since it does not generate any log of presence on the target system. A common
example would be to use LinkedIn, Facebook, and other social networks to gather information
about the employees and their interests. This would be very useful when we perform phishing,
keylogging, browser exploitation, and other client side attacks on the employees.

Sources of Information Gathering
There are many sources of information; the most important ones are as follows:
Social media website
Search engines
Forums
Press releases
People search
Job sites
So let’s discuss some of these sources in detail along with some tools of the trade

# Information Gathering with Whois

![photo](https://lh3.googleusercontent.com/AUcQ8TogoE0yGkfGdq_D9EGDe5bBTTsGLNswhADlChtBjCktuxpAV5grf3imIaEZATri_Nss3Ny1nMqqYvw07JqJog=w640-h400-e365-rj-sc0x00ffffff)


As I have mentioned earlier, our goal in the information gathering and enumeration phase is to
gather as much information as possible about the target. Whois holds a huge database that con-
tains information regarding almost every website that is on the web, most common information
are “who owns the website” and “the e-mail of the owner,” which can be used to perform social
engineering attacks.
Whois database is accessible on whois.domaintools.com. It’s also available in BackTrack. but
you would need to issue the following command from BackTrack to enable it:
apt-get install whois
In order to perform a Whois search on a website, you would need to type Whois <domainname>

from the command line:
whois www.techlotips.com
ou can see that it has revealed some interesting information such as the e-mail of the owner
(which I have set to private b/w) and the name servers, which shows that hostagtor.com is hosting
this website. We will learn some effective methods to determine name servers later in this section,
when we will talk about DNS enumeration

[Whois Lookups Website](https://who.is/)

# Tracing the Location
![photo](https://repository-images.githubusercontent.com/240892897/c6aed900-694c-11ea-9130-12dcbbace4bd)

You would need to know the IP address of the webserver in order to trace the exact location. There
are several methods to figure it out. We will use the simplest one, that is, the ping command. Ping
command sends icmp echo requests to check if the website is up. It’s used for network trouble-
shooting purposes.
From your command line, type the following: ping www.techlotips.com
So we now know that the IP address of our target is 50.22.81.62. After determining the web-
server’s IP, we can use some online tools to track the exact location of the webserver. One such tool
is IPTracer that is available at http://www.ip-adress.com/ip_tracer/yourip
Just replace your IP with your target’s IP, and it will show you the exact location of the web-
server via Google Maps.

[Ip Tacking Website](https://www.opentracker.net/feature/ip-tracker/)

# Traceroute
![photo](https://www.solarwinds.com/-/media/solarwinds/swdc/traceroute_bw_1222016.ashx?rev=d40699c755da4b1f8adc3409e29d81ca&h=745&w=1250&la=en&hash=6275E71BC3F542D22BDFCCC6EDD97EF8)

Traceroute is a very popular utility available in both Windows and Linux. It is used for network
orientation. By network orientation I don’t mean scanning a host for open ports or scanning for
services running on a port. It means to figure out how the network topology, firewalls, load bal-
ancers, and control points, etc. are implemented on the network.
58 ◾ Ethical Hacking and Penetration Testing Guide
A traceroute uses a TTL (time to live) field from the IP header, and it increments the IP packet
in order to determine where the system is. The time to live value decreases every time it reaches a
hop on the network (i.e. router to server is one hop).

There are three different types of traceroutes:

  1. ICMP traceroute (which is used in Windows by default)
  2. TCP traceroute
  3. UDP traceroute

# ICMP Traceroute
Microsoft Windows by default uses ICMP traceroute; however, after a few hops, you will get a
timeout, which indicates that there might be a device like IDS or firewall that is blocking ICMP
echo requests.

# TCP Traceroute
Many devices are configured to block ICMP traceroutes. This is where we try TCP or UDP trac-
eroutes, also known as layer 4 traceroutes. TCP traceroute is by default available in BackTrack. If
you can’t find it, just use the following command:
apt-get install tcptraceroute

Usage
From the command line, you would need to issue the following command:
tcptraceroute www.google.com

# UDP Traceroute
Linux also has a traceroute utility, but unlike Windows, it uses UDP protocol for the traceroute.
In Windows, the command for traceroute is “tracrt”. In, Linux, it’s “tracroute”.

Usage:
traceroute www.target.com

# WhatWeb
Our active information gathering section will not be complete without introducing a tool from
BackTrack. WhatWeb is an all-an-one package for performing active footprinting on a website.
It has more than 900 plug-ins capable of identifying server version, e-mail addresses, and SQL
errors. The tool is available in BackTrack by default in the /pentest/enumeration/web/whatweb
directory.
The usage is pretty simple: you need to type ./whatweb followed by the website name. You can
also scan multiple websites at a time.

[What web Website](https://www.kali.org/tools/whatweb/)

Command:
./whatweb slashdot.org reddit.com

# Netcraft
![photo](https://news.netcraft.com/images/2017/11/firefox-blocked-url.png)

Netcraft contains a huge online database with useful information on websites and can be
used for passive reconnaissance against the target. It is also capable of fingerprinting the
webservers.

# Google Hacking:
![photo](https://assets.website-files.com/5ff66329429d880392f6cba2/61a0aa0c05f4dc326921fde7_google%20dorks.png)

Google searches can be more than a treasure for a pentester, if he uses them effectively. With
Google searches, an attacker may be able to gather some very interesting information, includ-
ing passwords, on the target. Google has developed a few search parameters in order to
improve targeted search. However, they are abused by hackers to search for sensitive informa-
tion via Google.

# Google Hacking Database

![photo](https://d1ka0itfguscri.cloudfront.net/Q5tU/2021/10/03/13/59/cr6eIRV6WHj/preview.jpg)

Google hacking database is set up by the offensive security guys, the ones behind the famous
BackTrack distro. Google hacking database has a list of many Google dorks that could be used to
find usernames, passwords, e-mail list, password hashes, and other important information.
So let’s just ask the website to filter out all the Google dorks related to files that contain pass-
words. From the drop-down menu, select the option “Files containing passwords.” Now, you
would see a list of all the dorks that could be used to find passwords. Let’s try one of them.
Out of all other dorks, filetype:sql inurl:wp-content/backup-* seemed to be really interesting
to me, so I gave it a try on Google. Since MySQL passwords are also backed up with other files,
due to the incorrect permissions, it may reveal some interesting information.
What the above query is asking to SQL files with URL pattern wp-content/backup. Fortunately,
with a little bit of searching. I was able to find a “Wordpress mysql database” of a website exposed
to the public.

[ Google Hacking Database Website](https://www.exploit-db.com/google-hacking-database)

# Nslookup
Nslookup is available in both Windows and Linux OS. Let’s say that we want the DNS servers to
return all the mail server records of an organization. We would do the following:
Step 1—Issue the nslookup command from the command prompt.
Step 2—Issue the following command:
set type = mx
Step 3—Next, we would enter the domain.
www.msn.com
The query returned mail servers for msn.com.
We can also ask for all the DNS servers for that domain by using the set type = ns command.

[Nslookup website](https://www.nslookup.io/)

# What steps should you take when your email has been pwned?

![photo](https://i0.wp.com/9to5mac.com/wp-content/uploads/sites/6/2021/05/Have-I-Been-Pwned.jpg?w=2000&quality=82&strip=all&ssl=1)

4 steps to take if your email has been pwned

If your email has been pwned your personal information is in danger. This article guides you on what to do next. (PLUS! 5 tips on how to avoid getting pwned in the first place.)
What does being pwned mean?

Being pwned means that someone has taken control of your email address, or a user profile that has been created with it. And hacking an account is possibly the first step of identity theft, with online accounts often containing sensitive personal information, such as your credit card number, phone number, home address, and full name.

Identity theft can cause financial damage, intense personal stress, and a plethora of legal problems. And if your email account and password end up in the wrong hands, criminals can access your personal details and purchase goods in your name. Things can get even worse, though. Because if you have reused the same password and email on other accounts, criminals can access these profiles as well, increasing the risk of identity theft exponentially.
How does your email get pwned?

Your login credentials can be stolen in a – and there’s a significant data breach almost every week. So, it’s a good idea to regularly check if your information has been stolen in a data breach with F-Secure’s free Identity Theft Checker. But it doesn’t stop at data breaches. As your accounts can also be hacked through malware attacks, or through phishing scams.

But there’s no need to panic. If your account has been pwned, here are four things you can do to mitigate the risk:
1. Make sure your antivirus and operating system are up to date

Viruses and spyware can steal personal information and login credentials. Having up-to-date antivirus and operating systems on your devices is important in protecting your accounts from being pwned. The majority of core software that we use is regularly updated by vendors to prevent hackers from utilizing flaws and vulnerabilities. And so turn on automatic updates, which can save you from a lot of trouble if you do not yet have them enabled.
2. Scan your device for malware

If there is malware on your device, changing your account password isn’t enough. That’s because the attacker can steal your newly created password using malware. So, before you change any passwords, run a virus scan. If the scan detects an infection, deal with it first. If you already changed passwords, change them again. Because they might have already been compromised.
3. Now, change your passwords

Changing your password is the most important thing to do if your account has been pwned. If you have reused your password on other accounts, you should change passwords for those accounts as well.

Criminals will try to access accounts with payment details and other valuable data. But if the attacker has already changed your password to in a hacked account, don’t panic. You may still be able to restore your account through the “forgot your password” function.
4. Check your email settings

If your email account has been pwned, criminals can set it to automatically forward your messages to the attacker and to send malware, phishing scams, or spam. So check your settings and see if you find anything alarming.

You might also want to send an email to your contacts or post on social media that your email has been pwned, to warn against opening any attachments sent by you. This can save your contacts from being infected by malware.
How can you protect your email from being pwned?

Dealing with a compromised email address is possible, but the best course of action is to never let it happen in the first place. And you can cut that risk significantly by following these simple steps:

1. Pay attention to the sender addresses of emails and SMS messages; don’t fall for phishing or smishing

2. Be cautious when you open files, links, or install programs. Your bank or authorities don’t ask you to authenticate information online. Most likely you didn’t win a lottery prize either, and the “hot singles in your area” would probably use other methods to contact you

3. Enabling two-factor authentication is essential in protecting your online accounts. That’s why many banks and service providers use it. Follow their example when possible

4. Set your email address under 24/7 breach monitoring, and you’ll get alerts when a data breach including your personal information has occurred. This gives you time to change the password before anyone can get into your account

5. And finally, always use unique passwords.

You can create unique passwords for free with F-Secure Strong Password Generator. Get a password manager, and you can then save all these passwords securely. This way they are always with you, and you can copy paste or autofill them when needed. It’s easier, safer, and faster.
F-Secure TOTAL – Full online protection

F-Secure TOTAL online security package helps you protect your online accounts. It blocks viruses and phishing sites, makes your browsing secure and private with a VPN, and includes a password manager. It also alerts you of new data breaches that threaten your security.

[have i been pwned Website](https://haveibeenpwned.com/)
## Authors

- [@freecouse098](https://github.com/freecouse098/freecouse098)


## Contact Me

Contact Me Email : abhishekaswal777@gmail.com


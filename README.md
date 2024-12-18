# Security incident report

> [!NOTE]
> This exercise is a component of the [Google Cybersecurity Professional Certificate](https://www.coursera.org/professional-certificates/google-cybersecurity) program. It's designed as a simulated scenario to solidify my understanding of Network Analysis.

## Activity Overview

In this activity, you will take on the role of a cybersecurity analyst working for a company that hosts the cooking website, yummyrecipesforme.com. Visitors to the website experience a security issue when loading the main webpage. Your job is to investigate, identify, document, and recommend a solution to the security problem. 

When investigating the security event, you will review a tcpdump log. You will need to identify the network protocols used to establish the connection between the user and the website. Network protocols are the communication rules and standards networked devices use to transmit data. Unfortunately, malicious actors can also use network protocols to invade and attack private networks. Knowing how to identify the protocols commonly used in attacks will help you protect your organization’s network against these types of security events.

To complete the assignment, you will also need to document what occurred during the security incident. Then, you will recommend one security measure to implement to prevent similar security problems in the future.

## Scenario

You are a cybersecurity analyst for yummyrecipesforme.com, a website that sells recipes and cookbooks. A former employee has decided to lure users to a fake website with malware. 

The former employee/ hacker executed a brute force attack to gain access to the web host. They repeatedly entered several known default passwords for the administrative account until they correctly guessed the right one. After they obtained the login credentials, they were able to access the admin panel and change the website’s source code. They embedded a javascript function in the source code that prompted visitors to download and run a file upon visiting the website. After embedding the malware, the hacker changed the password to the administrative account. When customers download the file, they are redirected to a fake version of the website that contains the malware. 

Several hours after the attack, multiple customers emailed yummyrecipesforme’s helpdesk. They complained that the company’s website had prompted them to download a file to access free recipes. The customers claimed that, after running the file, the address of the website changed and their personal computers began running more slowly. 

In response to this incident, the website owner tries to log in to the admin panel but is unable to, so they reach out to the website hosting provider. You and other cybersecurity analysts are tasked with investigating this security event.

To address the incident, you create a sandbox environment to observe the suspicious website behavior. You run the network protocol analyzer tcpdump, then type in the URL for the website, yummyrecipesforme.com. As soon as the website loads, you are prompted to download an executable file to update your browser. You accept the download and allow the file to run. You then observe that your browser redirects you to a different URL, greatrecipesforme.com, which contains the malware.  

The logs show the following process:

1. The browser initiates a DNS request: It requests the IP address of the yummyrecipesforme.com URL from the DNS server.

2. The DNS replies with the correct IP address. 

3. The browser initiates an HTTP request: It requests the yummyrecipesforme.com webpage using the IP address sent by the DNS server.

4. The browser initiates the download of the malware.

5. The browser initiates a DNS request for greatrecipesforme.com.

6. The DNS server responds with the IP address for greatrecipesforme.com.

7. The browser initiates an HTTP request to the IP address for greatrecipesforme.com.

A senior analyst confirms that the website was compromised. The analyst checks the source code for the website. They notice that javascript code had been added to prompt website visitors to download an executable file. Analysis of the downloaded file found a script that redirects the visitors’ browsers from yummyrecipesforme.com to greatrecipesforme.com. 

The cybersecurity team reports that the web server was impacted by a brute force attack. The disgruntled hacker was able to guess the password easily because the admin password was still set to the default password. Additionally, there were no controls in place to prevent a brute force attack. 

Your job is to document the incident in detail, including identifying the network protocols used to establish the connection between the user and the website.  You should also recommend a security action to take to prevent brute force attacks in the future.

# Security incident report

|Section 1: Identify the network protocol involved in the incident|
|------------------------------------------------------------------|
|The incident involved the Hypertext Transfer Protocol (HTTP). Since the issue was related to accessing the web server for yummyrecipesforme.com, it is clear that HTTP traffic was used for the web page requests. Running tcpdump while visiting the website confirmed the use of HTTP in the communication. The malicious file was delivered to users' computers through HTTP at the application layer.|

|Section 2: Document the incident|
|--------------------------------|
|A former employee exploited a vulnerability in the website yummyrecipesforme.com through a brute force attack on the admin account, which still used a default password. After gaining access, the attacker embedded malicious JavaScript into the website’s source code. This script prompted visitors to download and execute a file that redirected them to a fake site, greatrecipesforme.com, which contained malware. The attacker then changed the admin password to maintain control.
Several users contacted the yummyrecipesforme’s helpdesk, reporting an unusual website behavior, including prompts to download files and performance issues on their computers after executing the file. The website owner, unable to log into the admin panel, contacted the hosting provider, leading to an investigation by cybersecurity analysts.
Using a sandbox environment and tcpdump, analysts confirmed that the malicious file was delivered via HTTP and redirected users to the fake site. Logs showed a sequence of DNS and HTTP requests that aligned with the attack's operation. Analysis of the compromised website’s source code revealed the embedded malicious JavaScript and its role in delivering the malware.|

|Section 3: Recommend one remediation for brute force attacks|
|------------------------------------------------------------|
|The administrative password must be changed immediately, implementing strong password policies, requiring a minimum length, complexity, and regular password changes. Additional measures, such as enabling two-factor authentication, would provide an extra layer of protection by requiring a second verification step during login. Furthermore, limiting the number of login attempts will help prevent brute force attacks by locking accounts after a set number of failed attempts. Monitoring login activity for unusual patterns and implementing IP-based restrictions can also enhance the overall security of the admin account.|





















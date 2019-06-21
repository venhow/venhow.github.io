---
layout: post
title: Unable to RDP to Virtual Machine: CredSSP Encryption Oracle Remediation
date: 2018-05-14 09:26
author: venhow
comments: true
categories: [IT资讯]
---
<header class="entry-header single">

<hr />

</header>

<div class="entry-content single">

<strong>Overview</strong>

With the release of the March 2018 Security bulletin, there was a fix that addressed a CredSSP, “Remote Code Execution” vulnerability (CVE-2018-0886) which could impact RDP connections. The vulnerability was discovered to which the exploits observed were:
<ul type="disc">
    <li>Targets receive a malicious RTF Microsoft Office document</li>
    <li>After being opened, the malicious document causes the second stage of the exploit to be downloaded in the form of an HTML page with malicious code</li>
    <li>The malicious code triggers the use-after-free memory-corruption bug</li>
    <li>Accompanying shellcode then downloads and executes a malicious payload</li>
</ul>
A total of 68 security bulletins were released as part of a monthly patch release to address this issue. 21 were rated critical, 45 were rated important and 2 were rated low severity.

<strong>Symptoms</strong>

1.       The VM screenshot shows the OS fully loaded and waiting for the credentials

2.       If you try to RDP the VM either internally or externally, you'll get the message:

An authentication error has occurred.

The function requested is not supported.

&nbsp;

This could be due to CredSSP encryption oracle remediation.

For more information, see <a href="https://go.microsoft.com/fwlink/?linkid=866660">https://go.microsoft.com/fwlink/?linkid=866660</a>

<img src="https://social.msdn.microsoft.com/Forums/getfile/1269889" alt="" />

<strong>Root Cause Analysis</strong>

To resolve a vulnerability issue with Credential Security Support Provider protocol (CredSSP), a monthly Windows update in May was applied which does two things:

<em>1.       </em><em>Correct how Credential Security Support Provider protocol (CredSSP) validates requests during the authentication process</em>

<em>2.       </em><em>Change the group policy Encryption Oracle Remediation default setting from Vulnerable to Mitigated.</em>

This RDP authentication issue can occur if the local client and the remote host have differing <em>Encryption Oracle Remediation</em> settings that define how to build an RDP session with CredSSP. If the server or client have different expectations on the establishment of a secure RDP session the connection could be blocked. There is the possibility that the current default setting could change from the tentative update and therefore impact the expected secure session requirement.

Below is the matrix for each possible situation for RDP result:

<img width="6" height="1" border="0" /><img src="https://social.msdn.microsoft.com/Forums/getfile/1269890" alt="" />

&nbsp;

<strong>Examples:</strong>

1.       If the client is updated and you try to RDP to an Azure VM that was not updated, then it will be blocked and see the error message.

2.       If the client is not patched while server is updated, RDP can still work. But the session will be exposed to the attack.

3.       If both client &amp; server are patched with default setting (Mitigated), RDP will work in a secure way.

<strong>References:</strong>
<ul type="disc">
    <li><a href="https://support.microsoft.com/en-us/help/4093492/credssp-updates-for-cve-2018-0886-march-13-2018" target="_blank" rel="noopener">CredSSP updates for CVE-2018-0886</a></li>
    <li><a href="https://blogs.technet.microsoft.com/yongrhee/2018/05/09/after-may-2018-security-update-rdp-an-%20authentication-error-occurred-this-could-be-due-to-credssp-encryption-oracle-remediation/">https://blogs.technet.microsoft.com/yongrhee/2018/05/09/after-may-2018-security-update-rdp-an- authentication-error-occurred-this-could-be-due-to-credssp-encryption-oracle-remediation/</a></li>
    <li><a href="https://blogs.technet.microsoft.com/askpfeplat/2018/05/07/credssp-rdp-and-raven/">https://blogs.technet.microsoft.com/askpfeplat/2018/05/07/credssp-rdp-and-raven/</a></li>
</ul>
<strong>Resolution/ Fix</strong>

Ensure both client &amp; server side have latest patch installed so that RDP can be established in a secure way.

You can find the list of the corresponding KB number for each operating system here: <a href="https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2018-0886" target="_blank" rel="noopener">https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2018-0886</a>

&nbsp;

<strong>Alternative Work-arounds</strong>

<strong>Mitigation 1</strong>

If you cannot RDP to a lot of VMs from your patched client, we can consider changing the policy settings <strong>on the client</strong> to temporarily gain RDP access to the servers. You can change the settings in Local Group Policy Editor. Execute <strong>gpedit.msc</strong> and browse to <strong>Computer Configuration / Administrative Templates / System / Credentials Delegation</strong> in the left pane:

<img width="6" height="3" border="0" /><img src="https://social.msdn.microsoft.com/Forums/getfile/1269891" alt="" />

Change the <strong>Encryption Oracle Remediation</strong> policy to <strong>Enabled</strong>, and <strong>Protection Level</strong> to <strong>Vulnerable</strong>:

<img width="6" height="2" border="0" /><img src="https://social.msdn.microsoft.com/Forums/getfile/1269892" alt="" />

&nbsp;

<strong>Mitigation 2</strong>

If it is not possible to access to Local Group Policy Editor on the client (i.e. Windows Home versions), same change can be done through the registry:

REG  ADD HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\CredSSP\Parameters\ /v AllowEncryptionOracle /t REG_DWORD /d 2
After that, whether the established RDP session is secure or not depends on whether server is patched. Remember to un-do this when all the servers are patched.

https://blogs.technet.microsoft.com/mckittrick/unable-to-rdp-to-virtual-machine-credssp-encryption-oracle-remediation/

</div>

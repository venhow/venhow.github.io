---
layout: post
title: Install SSL Certificates for SNI on Microsoft IIS 8 / 8.5
date: 2018-04-12 11:23
author: venhow
comments: true
categories: [IT资讯]
---
首先，你得开启防火墙端口，然后继续做如下操作：

This article shows you how to install multiple SSL certificates for Server Name Indication, using the Management Console on Windows 2012 Server. If you wish to install a single certificate on IIS 8, please refer to the <a href="https://www.kinamo.be/en/kb/microsoft-iis-8-install-ssl-certificate">IIS 8 SSL Installation Instructions</a>.

If you didn't generate a certificate request (CSR) yet, and didn't order a certificate, please see <a href="https://www.kinamo.be/en/kb/microsoft-iis-8-install-ssl-certificate">IIS 8 SSL Certificate Request Instructions</a>.

<h3 class="nav-enabled">How do I install multiple SSL certificate on Microsoft IIS 8?</h3>

<ol>
    <li>Save the certificate you received to the desktop of your Windows 2012 Server.</li>
    <li>Open the IIS console by clicking <strong>Start</strong>, then opening <strong>Administrative Tools</strong>, then <strong>Internet Information Services (IIS) Manager</strong>.</li>
    <li>Click on your server's name in the left pane.</li>
    <li>In the center pane, double-click <strong>Server Certificates</strong> in the IIS section.

<img src="https://www.kinamo.be/upload/web/image/FAQ/en/iis8/iis8-generate-ssl-csr-1.png" alt="" /></li>
    <li>In the Actions menu in the right pane, click on <strong>Complete Certificate Request</strong><strong>...</strong> to open the Complete Certificate Request Wizard.

<img src="https://www.kinamo.be/upload/web/image/FAQ/en/iis8/iis8-install-ssl-2.png" alt="" /></li>
    <li>Browse for the certificate file you just saved to your desktop. Enter a friendly name to identify the certificate with. This name will not be part of the certificate, but serves to identify the certificate for the server administrator. Use the same domain name you used when requesting your certificate. Select the <strong>Web Hosting</strong> certificate store. Click OK to store the certificate on the server.

<img src="https://www.kinamo.be/upload/web/image/FAQ/en/iis8/iis8-install-ssl-sni-3.png" alt="" />

You may encounter a known issue on IIS 8 if you receive the message "Failed to remove the certificate". In that case, click <strong>Cancel</strong> to exit the dialog, and refresh the server certificates list by pressing F5. If your certificate appears in the list, it installed correctly. However, you may want to check that it was saved to the correct Web Hosting store. If your certificate doesn't appear, you will need to re-issue your certificate with a new CSR.</li>
    <li>The certificate is now installed on the server, but must be assigned to a web site in IIS. Click on your server name in the left pane to browse the sites, and select the site you wish to assign the certificate to. In the Actions menu in the right pane, click <strong>Bindings...</strong> to add a binding.

<img src="https://www.kinamo.be/upload/web/image/FAQ/en/iis8/iis8-install-ssl-4.png" alt="" /></li>
    <li>In the Site Bindings window, click <strong>Add...</strong> to open the Add Site Binding window.

<img src="https://www.kinamo.be/upload/web/image/FAQ/en/iis8/iis8-install-ssl-5.png" alt="" /></li>
    <li>Select <strong>https</strong> as type. The IP address should be the one your website is listening on. Alternatively, you can leave the dropdown to <strong>All Unassigned</strong>. Leave the TCP port to 443, and select the correct certificate from the dropdown.

<img src="https://www.kinamo.be/upload/web/image/FAQ/en/iis8/iis8-install-ssl-6.png" alt="" /></li>
    <li>Your first SSL certificate is now installed, and the main website is ready to accept SSL connections.

<img src="https://www.kinamo.be/upload/web/image/FAQ/en/iis8/iis8-install-ssl-7.png" alt="" /></li>
    <li>Repeat all previous steps for installing your second certificate, up to step 9. In the Add Site Binding window, you should now check the box <strong>Require Server Name Indication</strong>. This is not required for the first certificate, which is the server's main certificate, but it is for the second and any additional certificates installed.

<img src="https://www.kinamo.be/upload/web/image/FAQ/en/iis8/iis8-install-ssl-sni-8.png" alt="" /></li>
    <li>Repeat the steps above for your third and any additional certificates you wish to install.</li>
</ol>

https://www.kinamo.be/en/support/faq/microsoft-iis-8-configure-server-name-indication-sni

https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-server-name-indication-sni-ssl-scalability

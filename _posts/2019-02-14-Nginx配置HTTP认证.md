---
layout: post
title: Nginx配置HTTP认证
date: 2019-02-14 11:03
author: venhow
comments: true
categories: [IT资讯]
---
<article>
<div id="page_content">
<div id="restricting-access-with-http-basic-authentication" class="section"><section id="introduction" class="section">
<h2>Introduction</h2>
You can restrict access to your website or some parts of it by implementing a username/password authentication. Usernames and passwords are taken from a file created and populated by a password file creation tool, for example, <code><span class="pre">apache2-utils</span></code>.

HTTP Basic authentication can also be combined with other access restriction methods, for example restricting access by <a class="reference internal" href="https://docs.nginx.com/nginx/admin-guide/security-controls/blacklisting-ip-addresses/"><span class="doc">IP address</span></a> or <a class="reference internal" href="https://docs.nginx.com/nginx/admin-guide/security-controls/controlling-access-by-geoip/"><span class="doc">geographical location</span></a>.

</section><section id="prerequisites" class="section"><span id="prerequisites_nginx"></span>
<h2>Prerequisites</h2>
<ul class="simple">
    <li>NGINX Plus or NGINX Open Source</li>
    <li>Password file creation utility such as <code><span class="pre">apache2-utils</span></code> (Debian, Ubuntu) or <code><span class="pre">httpd-tools</span></code> (RHEL/CentOS/Oracle Linux).</li>
</ul>
</section><section id="creating-a-password-file" class="section"><span id="creating-a-password-file_nginx"></span>
<h2>Creating a Password File</h2>
To create username-password pairs, use a password file creation utility, for example, <code><span class="pre">apache2-utils</span></code> or <code><span class="pre">httpd-tools</span></code>
<ol>
    <li>
<p class="first">Verify that <code><span class="pre">apache2-utils</span></code> (Debian, Ubuntu) or <code><span class="pre">httpd-tools</span></code> (RHEL/CentOS/Oracle Linux) is installed.</p>
</li>
    <li>
<p class="first">Create a password file and a first user. Run the <code><span class="pre">htpasswd</span></code> utility with the <code><span class="pre">-c</span></code> flag (to create a new file), the file pathname as the first argument, and the username as the second argument:</p>

<div class="highlight-none">
<div class="highlight">
<pre>$ sudo htpasswd -c /etc/apache2/.htpasswd user1
</pre>
</div>
</div>
Press Enter and type the password for <strong>user1</strong> at the prompts.</li>
    <li>
<p class="first">Create additional user-password pairs. Omit the <code><span class="pre">-c</span></code> flag because the file already exists:</p>

<div class="highlight-none">
<div class="highlight">
<pre>$ sudo htpasswd /etc/apache2/.htpasswd user2
</pre>
</div>
</div></li>
    <li>
<p class="first">You can confirm that the file contains paired usernames and encrypted passwords:</p>

<div class="highlight-none">
<div class="highlight">
<pre>$ cat /etc/apache2/.htpasswd
user1:$apr1$/woC1jnP$KAh0SsVn5qeSMjTtn0E9Q0
user2:$apr1$QdR8fNLT$vbCEEzDj7LyqCMyNpSoBh/
user3:$apr1$Mr5A0e.U$0j39Hp5FfxRkneklXaMrr/
</pre>
</div>
</div></li>
</ol>
</section><section id="configuring-nginx-and-nginx-plus-for-http-basic-authentication" class="section"><span id="configuring-nginx-and-nginx-plus-for-http-basic-authentication_nginx"></span>
<h2>Configuring NGINX and NGINX Plus for HTTP Basic Authentication</h2>
<ol>
    <li>
<p class="first">Inside a location that you are going to protect, specify the <a class="reference external" href="https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html#auth_basic" target="_blank" rel="noopener noreferrer"><code><span class="pre">auth_basic</span></code></a> directive and give a name to the password-protected area. The name of the area will be shown in the username/password dialog window when asking for credentials:</p>

<div class="highlight-nginx">
<div class="highlight">
<pre><span class="k">location</span> <span class="s">/api</span> <span class="p">{</span>
    <span class="kn">auth_basic</span> <span class="s">“Administrator’s</span> <span class="s">Area”</span><span class="p">;</span>
    <span class="c1">#...</span>
<span class="p">}</span>
</pre>
</div>
</div></li>
    <li>
<p class="first">Specify the <a class="reference external" href="https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html#auth_basic_user_file" target="_blank" rel="noopener noreferrer"><code><span class="pre">auth_basic_user_file</span></code></a> directive with a path to the <em>.htpasswd</em> file that contain user/password pairs:</p>

<div class="highlight-nginx">
<div class="highlight">
<pre><span class="k">location</span> <span class="s">/api</span> <span class="p">{</span>
    <span class="kn">auth_basic</span>           <span class="s">“Administrator’s</span> <span class="s">Area”</span><span class="p">;</span>
    <span class="kn">auth_basic_user_file</span> <span class="s">/etc/apache2/.htpasswd</span><span class="p">;</span> 
<span class="p">}</span>
</pre>
</div>
</div></li>
</ol>
Alternatively, you you can limit access to the whole website with basic authentication but still make some website areas public. In this case, specify the <code><span class="pre">off</span></code> parameter of the <a class="reference external" href="https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html#auth_basic" target="_blank" rel="noopener noreferrer"><code><span class="pre">auth_basic</span></code></a> directive that cancels inheritance from upper configuration levels:
<div class="highlight-nginx">
<div class="highlight">
<pre><span class="k">server</span> <span class="p">{</span>
    <span class="kn">...</span>
    <span class="s">auth_basic</span>           <span class="s">"Administrator’s</span> <span class="s">Area"</span><span class="p">;</span>
    <span class="kn">auth_basic_user_file</span> <span class="s">conf/htpasswd</span><span class="p">;</span>

    <span class="kn">location</span> <span class="s">/public/</span> <span class="p">{</span>
        <span class="kn">auth_basic</span> <span class="no">off</span><span class="p">;</span>
    <span class="p">}</span>
<span class="p">}</span>
</pre>
</div>
</div>
</section><section id="combining-basic-authentication-with-access-restriction-by-ip-address" class="section"><span id="combining-basic-authentication-with-access-restriction-by-ip-address_nginx"></span>
<h2>Combining Basic Authentication with Access Restriction by IP Address</h2>
HTTP basic authentication can be effectively combined with access restriction by IP address. You can implement at least two scenarios:
<ul class="simple">
    <li>a user must be both authenticated and have a valid IP address</li>
    <li>a user must be either authenticated, or have a valid IP address</li>
</ul>
<ol>
    <li>
<p class="first">Allow or deny access from particular IP addresses with the <a class="reference external" href="https://nginx.org/en/docs/http/ngx_http_access_module.html#allow" target="_blank" rel="noopener noreferrer"><code><span class="pre">allow</span></code></a> and <a class="reference external" href="https://nginx.org/en/docs/http/ngx_http_access_module.html#deny" target="_blank" rel="noopener noreferrer"><code><span class="pre">deny</span></code></a> directives:</p>

<div class="highlight-nginx">
<div class="highlight">
<pre><span class="k">location</span> <span class="s">/api</span> <span class="p">{</span>
    <span class="c1">#...</span>
    <span class="kn">deny</span>  <span class="mi">192</span><span class="s">.168.1.2</span><span class="p">;</span>
    <span class="kn">allow</span> <span class="mi">192</span><span class="s">.168.1.1/24</span><span class="p">;</span>
    <span class="kn">allow</span> <span class="mi">127</span><span class="s">.0.0.1</span><span class="p">;</span>
    <span class="kn">deny</span>  <span class="s">all</span><span class="p">;</span>
<span class="p">}</span>
</pre>
</div>
</div>
Access will be granted only for the <code><span class="pre">192.168.1.1/24</span></code> network excluding the <code><span class="pre">192.168.1.2</span></code> address. Note that the <code><span class="pre">allow</span></code> and <code><span class="pre">deny</span></code> directives will be applied in the order they are defined.</li>
    <li>
<p class="first">Combine restriction by IP and HTTP authentication with the <a class="reference external" href="https://nginx.org/en/docs/http/ngx_http_core_module.html#satisfy" target="_blank" rel="noopener noreferrer"><code><span class="pre">satisfy</span></code></a> directive. If you set the directive to to <code><span class="pre">all</span></code>, access is granted if a client satisfies both conditions. If you set the directive to <code><span class="pre">any</span></code>, access is granted if if a client satisfies at least one condition:</p>

<div class="highlight-nginx">
<div class="highlight">
<pre><span class="k">location</span> <span class="s">/api</span> <span class="p">{</span>
    <span class="c1">#...</span>
    <span class="kn">satisfy</span> <span class="s">all</span><span class="p">;</span>    

    <span class="kn">deny</span>  <span class="mi">192</span><span class="s">.168.1.2</span><span class="p">;</span>
    <span class="kn">allow</span> <span class="mi">192</span><span class="s">.168.1.1/24</span><span class="p">;</span>
    <span class="kn">allow</span> <span class="mi">127</span><span class="s">.0.0.1</span><span class="p">;</span>
    <span class="kn">deny</span>  <span class="s">all</span><span class="p">;</span>

    <span class="kn">auth_basic</span>           <span class="s">"Administrator’s</span> <span class="s">Area"</span><span class="p">;</span>
    <span class="kn">auth_basic_user_file</span> <span class="s">conf/htpasswd</span><span class="p">;</span>
<span class="p">}</span>
</pre>
</div>
</div></li>
</ol>
</section><section id="complete-example" class="section"><span id="complete-example_nginx"></span>
<h2>Complete Example</h2>
The example shows how to protect your status area with simple authentication combined with access restriction by IP address:
<div class="highlight-nginx">
<div class="highlight">
<pre><span class="k">http</span> <span class="p">{</span>
    <span class="kn">server</span> <span class="p">{</span>
        <span class="kn">listen</span> <span class="n">192.168.1.23</span><span class="p">:</span><span class="mi">8080</span><span class="p">;</span>
        <span class="kn">root</span>   <span class="s">/usr/share/nginx/html</span><span class="p">;</span>

        <span class="kn">location</span> <span class="s">/api</span> <span class="p">{</span>
            <span class="kn">api</span><span class="p">;</span>
            <span class="kn">satisfy</span> <span class="s">all</span><span class="p">;</span>

            <span class="kn">deny</span>  <span class="mi">192</span><span class="s">.168.1.2</span><span class="p">;</span>
            <span class="kn">allow</span> <span class="mi">192</span><span class="s">.168.1.1/24</span><span class="p">;</span>
            <span class="kn">allow</span> <span class="mi">127</span><span class="s">.0.0.1</span><span class="p">;</span>
            <span class="kn">deny</span>  <span class="s">all</span><span class="p">;</span>

            <span class="kn">auth_basic</span>           <span class="s">“Administrator’s</span> <span class="s">area</span><span class="p">;</span>
            <span class="kn">auth_basic_user_file</span> <span class="s">/etc/apache2/.htpasswd</span><span class="p">;</span> 
        <span class="p">}</span>
    <span class="p">}</span>
<span class="p">}</span>
</pre>
</div>
</div>
When you access your status page, you are prompted to log in:

<a class="reference external" href="https://cdn.wp.nginx.com/wp-content/uploads/2016/10/auth_required.png" target="_blank" rel="noopener noreferrer"><img src="https://cdn.wp.nginx.com/wp-content/uploads/2016/10/auth_required.png" alt="auth_required" /></a>

If the provided name and password do not match the password file, you get the <code><span class="pre">401</span> <span class="pre">(Authorization</span> <span class="pre">Required)</span></code> error.

取消HTTP验证则把auth_basic和auth_basic_user_file注销掉，运行命令nginx -s reload重启nginx服务即可。

</section></div>
</div>
</article>

<div class="prev-block"></div>

官方文档：https://docs.nginx.com/nginx/admin-guide/security-controls/configuring-http-basic-authentication/

---
layout: post
title: Why Shibboleth is a Great Alternative to Active Directory Federation Service
date: 2018-04-27 14:56
author: venhow
comments: true
categories: [IT资讯]
---
<div>If you are currently using Active Directory Federation Services (ADFS), you might want to consider implementing Shibboleth instead. Shibboleth was specifically designed with higher education in mind. Both Shibboleth and ADFS were designed for enterprise application, but ADFS was designed with higher education as an afterthought.</div>

Shibboleth is open source, meaning that there are no license fees, it is more flexible, and it is easier to customize. Shibboleth can also run on Windows, but can be and often is run on Linux (making it more affordable than buying a Windows license that each ADFS node requires).

Shibboleth provides federated authentication across or within organizational boundaries. Shibboleth supports Active Directory, and unlike ADFS it supports many other LDAP types. Shibboleth also upholds SQL Server as an attribute store, plus many other database types. Shibboleth supports most if not all of the SAML 1.1 and SAML 2.0 profiles, so more client application integrations are supported. In contrast to Shibboleth, ADFS does not natively support federated metadata files required by popular higher education federations like the InCommon Federation.

For all of these reasons, Shibboleth is a great alternative to ADFS. Shibboleth can meet the identity and access management needs of both higher education institutions and organizations, helping to maximize the open source investment.
Whatever the goal of the Shibboleth deployment, Unicon provides the expertise required to give the confidence that comes with a professional implementation. To read more about Unicon’s services for Shibboleth, visit <a href="https://www.unicon.net/opensource/shibboleth">www.unicon.net/opensource/shibboleth</a>.

<em>Testimonial:</em>
“Before I knew of Shibboleth, I ran ADFS at a university in the state of Washington for several years. We mostly set it up for use with Office 365, but eventually tried to make it work with InCommon. I was kind of successful in getting it to work with InCommon, but it was a hack. It got harder and harder to maintain as we created partnerships with more third-party apps (that supported InCommon). Shortly before I left I was making plans to gut the ADFS infrastructure replacing most of it with Shibboleth. The plan was to integrate ADFS as a Shibboleth client only to support Office 365.”

<em>~ Former IAM Architect at a university in the state of Washington</em>

<strong>About Shibboleth</strong>
Shibboleth Federated Single Sign-On Authentication Service is a standards based, open source software package for web single sign-on across or within organizational boundaries. Shibboleth, a project of the Shibboleth Consortium, allows institutions to make authorization decisions for individual access of protected online resources. The Shibboleth software implements widely used federated identity standards, principally OASIS' Security Assertion Markup Language (SAML), to provide a federated single sign-on and attribute exchange framework. Using Shibboleth-enabled access simplifies management of identity and permissions for organizations supporting users and applications. Shibboleth is developed in an open and participatory environment, is freely available, and is released under the Apache Software License. Learn more at <a class="ext" href="http://shibboleth.net/" target="_blank" rel="noopener">http://shibboleth.net<span class="ext"><span class="element-invisible">(link is external)</span></span></a>.

https://www.unicon.net/about/articles/why-shibboleth-great-alternative-active-directory-federation-service

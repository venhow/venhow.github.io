---
layout: post
title: Gitlab Server 搭建配置
date: 2018-12-27 17:18
author: venhow
comments: true
categories: [IT资讯]
---
腾讯企业邮箱出现错误：501 mail from address must be same as authorization user

https://docs.gitlab.com.cn/omnibus/settings/smtp.html#qq-exmail

sudo /etc/gitlab/gitlab.rb：

gitlab_rails['smtp_enable'] = true
gitlab_rails['smtp_address'] = "smtp.exmail.qq.com"
gitlab_rails['smtp_port'] = 465
gitlab_rails['smtp_user_name'] = "xxxx@xx.com"
gitlab_rails['smtp_password'] = "password"
gitlab_rails['smtp_authentication'] = "login"
gitlab_rails['smtp_ssl'] = true
gitlab_rails['smtp_enable_starttls_auto'] = true
gitlab_rails['smtp_tls'] = true
gitlab_rails['gitlab_email_from'] = 'xxxx@xx.com'
gitlab_rails['gitlab_email_reply_to'] = 'xxxx@xx.com'
gitlab_rails['smtp_domain'] = "exmail.qq.com"

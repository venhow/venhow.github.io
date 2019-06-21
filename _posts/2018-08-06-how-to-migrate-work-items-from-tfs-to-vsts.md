---
layout: post
title: How to migrate work items from TFS to VSTS
date: 2018-08-06 11:13
author: venhow
comments: true
categories: [IT资讯]
---
<ul>
    <li><a href="https://docs.microsoft.com/en-us/vsts/articles/migration-import?view=vsts" rel="nofollow noreferrer">TFS to VSTS migration</a> - The official import option which will import 1 project collection into 1 VSTS account. It automatically imports everything stored in the backup. At the point of writing this, the TFS must be upgraded to TFS 2018 and some work item template customizations must be removed (there are a few well documented features unavailable on VSTS).</li>
    <li><a href="https://github.com/nkdAgility/vsts-sync-migration" rel="nofollow noreferrer">VSTS Sync Migrator</a> - Marting Hinshelwood, the uncrowned king of TFS and VSTS migrations, has built his own little tool that can migrate work items from one server/account to another. It can even do migrations from one Team Project to another and while doing it switch between process templates.</li>
    <li><a href="https://github.com/Microsoft/vsts-work-item-migrator" rel="nofollow noreferrer">VSTS Work Item Migrator</a> - Microsoft has also open sourced a project that they used internally to migrate work items. It's less powerful, but it was made by Microsoft.</li>
</ul>

https://stackoverflow.com/questions/37446325/how-to-migrate-work-items-from-tfs-to-visual-studio-team-services

---
layout: post
title: Restore Configuration From PRTG's Auto-Backup
date: 2018-07-23 16:54
author: venhow
comments: true
categories: [IT资讯]
---
PRTG automatically saves a daily backup of its configuration file in the <strong>\Configuration Auto-Backups</strong>sub folder of the <a href="https://kb.paessler.com/en/topic/463">data folder</a>.

In order to restore a previous configuration from PRTG's auto-backup please follow these steps.

<ol>
    <li>Stop both PRTG services:
<ol>
    <li>Open the <a href="https://www.paessler.com/manuals/prtg/prtg_server_administrator.htm" target="_blank" rel="noopener">PRTG Administration Tool</a> on your PRTG core server system.</li>
    <li>Open the <strong>Service Start/Stop</strong> tab.</li>
    <li>Click on <strong>Stop Core Server</strong> and <strong>Stop Probe Service</strong>
<ul>
    <li><em>Note:</em> In PRTG versions previous to 14.4.12, you have to use the PRTG Probe Administrator and PRTG Server Administrator programs to stop both services.</li>
</ul>
</li>
</ol>
</li>
    <li>Open the PRTG data folder
<ul>
    <li>For more information on where to find this please see <a href="https://kb.paessler.com/en/topic/463">How and where does PRTG store its data?</a></li>
</ul>
</li>
    <li>Your current configuration file's name is <strong>PRTG Configuration.dat</strong>. Please rename it.</li>
    <li>In the <strong>Configuration Auto-Backups</strong> sub folder, locate the ZIP file with the configuration you want to restore. Unzip and copy it to the data folder to replace your current configuration.</li>
    <li>Restart both PRTG services:
<ol>
    <li>Open the <a href="https://www.paessler.com/manuals/prtg/prtg_server_administrator.htm" target="_blank" rel="noopener">PRTG Administration Tool</a> on your PRTG core server system.</li>
    <li>Open the <strong>Service Start/Stop</strong> tab.</li>
    <li>Click on <strong>Start Core Server</strong> and <strong>Start Probe Service</strong>
<ul>
    <li><em>Note:</em> In PRTG versions previous to 14.4.12, you have to use the PRTG Probe Administrator and PRTG Server Administrator programs to start both services.</li>
</ul>
</li>
</ol>
</li>
</ol>

Done. PRTG is now running with the new configuration.

<em>Note:</em> If you're looking for the last working configuration (e.g. after a crash), repeat the steps above and go back date by date until you obtain a valid configuration again.

https://kb.paessler.com/en/topic/12313-how-do-i-restore-a-previous-configuration-of-prtg-from-automated-backup-zips#reply-34593

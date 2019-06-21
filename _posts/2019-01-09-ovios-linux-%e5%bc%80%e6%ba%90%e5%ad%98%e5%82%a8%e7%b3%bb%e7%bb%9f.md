---
layout: post
title: OviOS Linux - 开源存储系统
date: 2019-01-09 10:01
author: venhow
comments: true
categories: [IT资讯]
---
<div>
<div>
<div>OviOS is an open source storage OS based on the Linux kernel and includes opensource software needed to create a fully functional, high performance storage server, compiled especially for high load servers, using the new blk_mq multi-queue block layer.

Click <a href="http://events.linuxfoundation.org/sites/events/files/slides/scsi.pdf" target="_blank" rel="noopener">here </a>for more information on this feature.</div>
<div></div>
</div>
</div>

<div>
<div>
<div>
<div>It supports iSCSI, NFS and SMB versions 1,2 and 3. It also supports AD integration, and NIS authentication.</div>
</div>
</div>
<div>
<div>
<div></div>
</div>
</div>
<div>
<div>
<div>As a software defined storage operating system, OviOS Linux can be installed on commodity hardware, with support for x86_64 CPUs. We recommend a minimum of 4GB of RAM for a small server, with no high performance requirements. The OS itself requires about 100MB memory to run, but for storage services the more the better.</div>
</div>
</div>
<div>
<div>
<div>It can be installed on a small SSD or HDD (recommended size 8GB).</div>
</div>
<div>
<div>Once booted into the live CD , type setup to start the installer. The installation process is very simple, one needs to set the time, choose the device on which to install, and run the installer.</div>
</div>
</div>
<div>
<div>
<div></div>
</div>
</div>
<div>
<div>
<div><b>Main features:</b></div>
</div>
<div>
<div></div>
</div>
<div>
<div><b>HA Clustering</b></div>
</div>
<div>
<div>OviOS can be configured as an HA cluster using 2 or 3 OviOS nodes, with corosync and pacemaker.</div>
</div>
<div>
<div>For automatic failover and scsi fencing, the required setup is 3 nodes.</div>
</div>
<div>
<div></div>
</div>
<div>
<div><b>Replication</b></div>
</div>
<div>
<div>Install a second OviOS Linux server and set up replication from the production server to the backup server. Your data will be available at all times on the backup server for disaster recovery scenarios.</div>
</div>
<div>
<div></div>
</div>
<div>
<div><b>Snapshots</b></div>
</div>
<div>The ability to snapshot LUNs, volumes and / or pools without disrupting data traffic. Snapshots can be scheduled or taken manually, In case of accidental data deletion, a volume or LUN can be reverted to a last known good snapshot.</div>
<div>
<div></div>
</div>
<div>
<div><b>ZFS Storage File System</b></div>
</div>
<div>OviOS uses the ZFS file system for it's storage pools.</div>
<b>Virtualization.</b>
<div>
<div>OviOS Linux can be virtualized or installed on physical hardware.</div>
</div>
<div>
<div><b>
</b><b>Run from a USB.</b></div>
</div>
<div></div>
<div>OviOS Linux can be installed on a USB drive.</div>
</div>
</div>

<div>
<div>
<div>
<div><b>iSCSI, NFS and SMB server features by default.</b></div>
</div>
</div>
<div>
<div>
<div>Once installed the system can be immediately used as an iSCSI, NFS and SMB server. The default configuration has been tested and optimized to achieve best performance with VMWare, Linux and Windows clients for iSCSI, VMWare and Linux as NFS clients and Windows as SMB clients. OviOS supports SMB protocol versions 1 (also known as NT1 or CIFS) ,SMBv2 and SMBv3.</div>
</div>
<div>
<div><b>
</b><b>Software RAID</b></div>
</div>
<div>
<div>
RAID0 or stripped pools. This configuration provides no data protection in case of a drive failure, it does provide checksumming to prevent silent data corruption.</div>
</div>
<div>
<div></div>
</div>
<div>
<div>RAID1 or mirrored pools. Create storage pools using mirrors of disks. It can protect against a large amount of failed drives, but has impact on the storage capacity.</div>
</div>
<div>
<div></div>
</div>
<div>
<div>RAID10 or stripped mirrored storage pools. Creates pairs of stripped mirrors which provide the best random read writes performances but reduces the available storage capacity by 50%.</div>
</div>
<div>
<div></div>
</div>
<div>
<div>RAID5 uses dynamic stripe width, which gives better performance then traditional RAID5 configurations. Allows for one disk failure.</div>
</div>
<div>
<div></div>
</div>
<div>
<div>RAID6 same as RAID5 but allows for 2 disk failures without data loss. Or RAID6+ which allows for 3 disk failures without data loss.</div>
</div>
<div>
<div><b>Data compression</b></div>
</div>
<div></div>
<div>Data compression which saves space on compressible data and improves performance.
<div><b>OviOS Live </b></div>
<div></div>
<div>OviOS Linux can run and fully function as a storage system from the Live CD (or USB).</div>
<div>See the documentation page for more details bout the OviOS Live method.</div>
</div>
<div>
<div><b>Remote backup</b></div>
</div>
<div>
<div>Configure OviOS as a backup server for your most important data. The ZFS filesystem's advanced data integrity check features protect against data corruption.</div>
</div>
</div>
</div>

+++
title = "Service Status"
description = ""
author = "RC Staff"
images = [
  "/2016/10/image.jpg",
]
categories = [
  "service", "status"
]
date = "2024-02-16T08:55:21-05:00"
tags = [
  "service",
  "status",
  "storage",
]
draft = false

+++

# Project Storage Data Migration

The storage hardware serving the Research Project Storage file system has been experiencing intermittent disruptions since October 2023. In response, we acquired and installed new, upgraded hardware offering faster, more reliable access and capacity.  

However, because an Active File Management (AFM) connection between the old and new systems was used to facilitate automatic file transfers, the new system’s performance is being negatively impacted by the old hardware and causing accessibility issues for some users.  

To mitigate these issues, Research Computing engineers are switching to an alternate backend migration process on February 26, 2024, at 9:00 a.m. 

**IMPORTANT:** This action will make data that have not yet been transferred appear to have vanished from the new Project storage file system. **Please be assured that all data will remain secure and intact throughout the migration process.** Rivanna and RC’s other storage services, Scratch and Research Standard, continue to operate normally. 

{{% callout %}}
## Key Points:

- An alternate method of transferring data from old Research Project storage to new Research Project storage will be implemented on 2/26/24 at 9:00 a.m. EST.
- All data on old Research Project and new Research Project are secure and intact.
- Starting February 26, data will be transferred by RC staff to a new **read-only** share <nobr>`/stagedproject`</nobr> on the new storage system. Files that have already been migrated to <nobr> `/project`</nobr> remain intact. 
- Though the new Project storage system is operating with expected performance, the transfer of all data from the old storage system will take several months. The severe performance degradation of the old storage system will remain a bottleneck regardless of the change in data transfer method.
- Rivanna and RC’s other storage services, Scratch and Research Standard, continue to operate normally.

**2024-02-19:** A total of 1.7 PB out of 4.3 PB have been copied from old to new Project storage (40%).
{{% /callout %}}

## Incident Response 

Research Computing will reach out to all known users of this storage system with instructions for accessing data before and after February 26, and for assistance prioritizing files for transfer.  

{{% accordion-group title="Group" %}}

{{% accordion-item title="Email communications" id="one" %}}

**2024-02-16**

Dear Colleagues,  
 
As previously shared, efforts are still underway to transfer data in the Project Storage file system from the legacy GPFS hardware to the new, upgraded hardware. To date, we have successfully transferred about 35% of Project Storage files. These files were transferred because they were either needed for a scheduled research project, or they had been recently accessed. However, now we are finding that the Active File Management (AFM) connection being used to transfer files is causing too great of a system load for the legacy hardware, as the old system continues to degrade. This is causing additional disruptions and file access issues. Although there are issues with access, rest assured that **all files remain safe and secure**, and will be transferred to the new system by fall.  
 
**What we are doing now**  

**On Monday, 2/26, we will move from the AFM connection to a new, manual process to transfer the remaining data.** As part of this manual process, we have launched a high priority transfer request for files actively needed for your research.  As part of this manual process, we are prioritizing files identified as actively needed for current research projects. If you need to access files on the legacy system for active project work, **please indicate which directories or files should be prioritized for transfer using our data transfer request form.** You can also use this form to request a list of your files that remain on the old system.  Please note that we cannot guarantee a timeline for transferring prioritized files due to the uncertainty of the old hardware. Prioritized file transfer may still take weeks to months to complete. 
 
If you have already reached out to prioritize file transfer or do not anticipate immediate use of these files, no further action is required.  
 
**What you may experience now until the transfer is complete** 

Today, when you log in to Project Storage, you will see your complete file list in your directory. Although the file list is complete, it is possible that some files in your directory have already been migrated to the new hardware and are readily available for use, while others remain on the old cluster. Accessing files that remain on the old cluster will likely result in excessively slow access speeds or a “file not found” error. This “file not found” error only indicates that your file has not yet been transferred.   
 
On 2/26, we will move to the new, manual file transfer process. Because this process is manual and no longer based on the file connection method, file names of files not yet transferred to the new system will be removed from your /Project storage directory. These file names will automatically repopulate in your directory under a new /stagedproject folder as they are transferred to the new hardware.   
 
**Additional information about the file transfer efforts and system status is available on our new Data Migration status page (this page).** We will provide ongoing updates at this location.
 
I understand the impact these disruptions may have had on your work, and I share in your frustrations. Our mission is to provide excellent service and support for a seamless research computing experience.   
 
We are committed to working diligently until data transfer is complete and the legacy system is decommissioned. Our help desk and technical support teams will continue to be available to you to address any concerns.  
 
Thank you for your continued patience and partnership.  
 
With regards,  

Joshua Baller, PhD<br>
Associate Vice President for Research Computing<br>
Information Technology Services<br>
University of Virginia

{{% /accordion-item %}}

{{% /accordion-group %}}

## What to expect on February 26

Before February 26, your <nobr>`/project`</nobr> folder contains a mix of files, including those that have already been transferred and those that still reside physically on the old Project storage system. Files that are still on the old system appear as empty "stub files" in the new system. Because the old and new systems are still connected, if you try to access a file that is still on the old system, the empty stub file is replaced by the original file as it is transferred on-demand to the new system.  

On February 26, the old and new Project storage systems will be disconnected. Researchers will not have any direct access to the old Project storage. The current <nobr>`/project`</nobr> folder on the new storage system should perform optimally without the tether to the old storage system. We will begin deleting the empty stub files on <nobr>`/project`</nobr>. These are empty files and are not needed for the new migration process. **The original files are still intact and secure on the old system.** 

A new filesystem <nobr>`/stagedproject`</nobr> will be mounted read-only on <a href="/userinfo/rivanna/login/#secure-shell-access-ssh" target="_blank">Rivanna login nodes</a> and the <a href="/userinfo/globus/#transferring-files" target="_blank">UVA Standard Security Storage</a> data transfer node (DTN). This folder will not be available on compute nodes. This folder will be used as a target to stage your data as it is being transferred from the old system to the new system. Setting up a new destination for the not yet transferred files prevents potential interference with your active work in <nobr>`/project`</nobr>. 

**Your Project storage folders on February 26:**

* `/project/MY_SHARE`: This is located on the new storage system. It contains files that have already been transferred since Fall 2023 as well as newly-created files. 

* `/stagedproject/MY_SHARE`: This is a new share set up on the new storage system. It will be empty initially. Files will begin to appear here as they are transferred, starting Feb 26.  

    <small>“MY_SHARE” refers to your personal project name</small>

**Note: The `/stagedproject/MY_SHARE` folder will only be created for you if you have folders/files on the old storage system that still need to be migrated.** 

## FAQ

{{% accordion-group title="Group" %}}

{{% accordion-item title="How should I prepare for the changes coming on February 26?" id="ten" %}}
If you have already reached out to us to prioritize transfer of a specific subset of your folders or files, no further action is required. These files will be copied to same-named folder in your active <nobr>`/project`</nobr> share on the new Project storage system.  

If you have not yet contacted us with a list of priority folders or files to transfer, or if there are additional folders and files that you urgently need for your active work, please <a href="/form/support-request/?category=Storage&request_title=Project%20storage%20data%20migration&description=Please%20indicate%20as%20precisely%20as%20possible%20which%20directories%20or%20files%20should%20be%20transferred%20first:" target="_blank">reach out to RC</a> with a specific list of those folders/files and we will add them to the file transfer queue. See *"How can I get help with migration of my data?"* for details. 

Questions about the data migration process should be directed to our <a href="/form/support-request/?category=Storage&request_title=Project%20storage%20data%20migration" class="card-link" target="_blank">user services team</a>. 
{{% /accordion-item %}}

{{% accordion-item title="Some of my Project storage files disappeared. Where did they go?" id="one" %}}
Until February 26, all files are shown in the new Project storage system, including those that have already been transferred and those that are still on the old Project storage system. Files that are still on the old system present as empty stub files in the new system. When accessed for the first time, the empty stub file is replaced by the original file as it is transferred on-demand from the old system to the new system. 

On February 26, the empty stub files will be deleted from the new system as they are not needed for the new migration process. This is a gradual process that may take a few weeks to complete, so you may see different files, depending on when you access the new system. **However, the original files behind the stub files still exist and are secure on the Old Project system.** 

See *"How do I find out what files are on the old Project storage system?"*
{{% /accordion-item %}}

{{% accordion-item title="Where are you copying my files?" id="two" %}}
Until February 26, files that you have already requested be transferred will be copied to the same-named directories in your active <nobr>`/project`</nobr> share on the new Project storage system. 

Beginning February 26, all your files, including files that are still on the old system and files that have already been transferred to the new system, will start being copied to the same-named directories in a new <nobr>`/stagedproject`</nobr> share. The <nobr>`/stagedproject`</nobr> share was created for your to-be-migrated files to prevent potential interference with your active work in <nobr>`/project`</nobr>. **Note:** Your folder in <nobr>`/stagedproject`</nobr> will be empty on February 26, but will gradually fill with your files as they are copied over.  
{{% /accordion-item %}}

{{% accordion-item title="How do I access the new /stagedproject folder?"  id="eight" %}}
On February 26, a new <nobr>`/stagedproject`</nobr> folder will become available in **read-only** mode on the <a href="/userinfo/rivanna/login/#secure-shell-access-ssh" target="_blank">Rivanna login nodes</a> and the <a href="/userinfo/globus/#transferring-files" target="_blank">UVA Standard Security Storage</a> data transfer node (DTN). It will not be available on compute nodes. This folder will be used as destination to stage data transferred from your old Project storage to the new storage system. 
{{% /accordion-item %}}

{{% accordion-item title="How can I work with the files that have been transferred into my /stagedproject folder?"  id="nine" %}}
On Feb 26, your folder in <nobr>`/stagedproject`</nobr> is set up as **read-only** on the <a href="/userinfo/rivanna/login/#secure-shell-access-ssh" target="_blank">Rivanna login nodes</a> and the <a href="/userinfo/globus/#transferring-files" target="_blank">UVA Standard Security Storage</a> data transfer node (DTN). It is *not* available on any  compute nodes. 

<img src="/images/service/StorageOverview.png" alt="Project storage" width="100%"/>
<small>&#42;AFM: Active File Management</small>

For compute jobs, you should copy files from <nobr>`/stagedproject`</nobr> into your <nobr>`/project`</nobr> or <nobr>`/scratch`</nobr> folder. Then launch compute jobs reading and writing files using the <nobr>`/project`</nobr> or <nobr>`/scratch`</nobr> folders as you usually do. You could copy files to your <nobr>`/home`</nobr> folder as well, but be aware of the limited 50GB per user quota which makes this impractical.
{{% /accordion-item %}}

{{% accordion-item title="Why can't I access the old Project storage system directly to copy my own files?" id="three" %}}
Performance of the old Project storage system is severely degraded. Any exploratory search for folders or file listings by users would create additional strain on the system, which would further reduce the already limited data transfer rates from the old to new Project storage system.

Because of these performance issues, RC set up a managed process that transfers all files from the old Project storage system to a new <nobr>`/stagedproject`</nobr> folder for you in the new system. See *“How do I access the new <nobr>/stagedproject</nobr> folder?”*.

You can reach out to RC to <a href="/form/support-request/?category=Storage&request_title=Old%20Project%20Storage:%20File%20List%20Request&description=Please%20send%20me%20a%20list%20of%20my%20files%20on%20old%20Project%20storage" taregt="_blank">request a list</a> of your files on the old Project storage system. See *"How do I find out what files are on the old Project storage system?"*

RC will work with you to prioritize the list of your files so that those files most urgently needed for your active work can be transferred first. See *"How can I get help with the migration process?"*
{{% /accordion-item %}}

{{% accordion-item title="How do I find out what files are on the old Project storage system?" id="four" %}}
After February 26, you will not be able to connect to the old Project storage system. See *"Why can't I access the old Project storage system directly to copy my own files?"*

However, you can reach out to RC to <a href="/form/support-request/?category=Storage&request_title=Old%20Project%20Storage:%20File%20List%20Request&description=Please%20send%20me%20a%20list%20of%20my%20files%20on%20old%20Project%20storage" taregt="_blank">request a list</a> of your files on the old Project storage system. We will place a txt file containing that file list in the top-level folder of your new share on <nobr>`/stagedproject`</nobr>.
{{% /accordion-item %}}

{{% accordion-item title="Are all files being transferred to the new Project storage system at once?"  id="six" %}}
No. We are prioritizing transfer of files that you actively need for your research. You may <a href="/form/support-request/?category=Storage&request_title=Project%20storage%20data%20migration&description=Please%20indicate%20as%20precisely%20as%20possible%20which%20directories%20or%20files%20should%20be%20transferred%20first:" target="blank_">reach out to us</a> to provide a specific list of your high priority, essential folders and files. 

The severe performance degradation of the old storage system will remain a bottleneck regardless of the change in data transfer method. **However, the more selective this list, the better we can help you with this transition.** See *“Can I pick which of my files are transferred first?"* for details. 

Once the transfer process has been stabilized, engineers will begin transferring any remaining files that users did not explicitly request to be moved.
{{% /accordion-item %}}

{{% accordion-item title="Can I pick which of my files are transferred first?"  id="eleven" %}}
Yes. Please complete this <a href="/form/support-request/?category=Storage&request_title=Project%20storage%20data%20migration&description=Please%20indicate%20as%20precisely%20as%20possible%20which%20directories%20or%20files%20should%20be%20transferred%20first:" target="_blank">web form</a> to provide us with a list of specific, high priority folders and files for migration. **Please indicate as precisely as possible which folders or files should be transferred first so our storage engineers can prioritize these items.** The more selective this list, the better we can help you with the transition.  

If you need help with your file prioritization, you may reach out to RC to <a href="/form/support-request/?category=Storage&request_title=Old%20Project%20Storage:%20File%20List%20Request&description=Please%20send%20me%20a%20list%20of%20my%20files%20on%20old%20Project%20storage." target="_blank">request a list of files</a> that you still have on the old Project storage system. 
{{% /accordion-item %}}

{{% accordion-item title="How can I get an estimate of when my files will be transferred?"  id="seven" %}}
Though the new Project storage system provides vastly improved performance, the overall transfer of files is limited by the degraded performance of the old system. This issue with the old storage system will remain a bottleneck regardless of the change in data transfer method. 

**However, you can facilitate the data transfer process by providing us with a narrowed down list of files that you need for your research over the next few months. This will allow us to deprioritize less urgently needed files.** 

See *“Can I pick which of my files are transferred first?"* for details.

All data will be migrated eventually, but this process is expected to take several months to complete. We will post weekly progress of data migration on this page. 

We will notify the PI of the storage allocation when all their folders have been copied over. **We will not purge any files on the old Project storage system until the PI has had an opportunity to verify that their files have been migrated to the new Project storage system.** 
{{% /accordion-item %}}

{{% accordion-item title="Why is the transfer of folders to the new Project storage system taking longer than expected?"  id="thirteen" %}}
The old Project storage hardware (GPFS) is in a degraded state. Due to this state, transferring data from the system is unusually slow even in otherwise ideal conditions. With a wide range of researchers and research workflows attempting to simultaneously access the system, the system becomes overloaded resulting in the “IO Error” and similar errors that researchers have been experiencing. As the system gets overloaded the transfer rates drop even further.  

By having RC manage the data transfer from the old to the new system we will be able to limit the load on the system and keep it closer to ideal conditions in order to maximize the transfer rate going forward. 
{{% /accordion-item %}}

{{% accordion-item title="What caused this issue with the old Project storage file system?"  id="fourteen" %}}
The old GPFS hardware was beyond its expected end-of-life and due to historical sporadic financial investment in RC the hardware was not replaced. That changed recently with substantial University investments in RC and replacement hardware was immediately purchased. Unfortunately, we were not able to get the new GPFS hardware up and running before we started to experience failures on the old GPFS hardware. Given that the hardware was already end-of-life, we prioritized completing installation of the new hardware quickly and transferring from the old hardware to the new. Because the old GPFS hardware is still experiencing failure, these transfers have been slow with ~35% of the data transferred to-date. 
{{% /accordion-item %}}

{{% accordion-item title="What is RC doing to ensure increased reliability and improved service?"  id="fifteen" %}}
With recent University investments in Research Computing we have planned annual purchases of new hardware with a model that allows for the seamless addition of new hardware and decommissioning of old hardware as it reaches its end-of-life. This will reduce the need for downtimes and manual data migrations as we ensure the integrity of our infrastructure. 

Research Computing is also working to improve its approach to user communications. If a major disruption occurs to an RC system, we will be using pages like this one to make sure there is a single location researchers can go to see both the current status and the history of the incident. 

Looking forward, Research Computing’s service roadmap includes filling in some services currently missing from our portfolio. Critically, there should be options available for researchers to elect for redundant access to their key datasets.  This means not only additional levels of protection in case of a disaster but also an alternate location where data can be retrieved. 
{{% /accordion-item %}}

{{% accordion-item title="How were files prioritized for transfer for the new system?"  id="sixteen" %}}
At this time, about 35% of files have been successfully migrated. These files were moved as part of prioritized research datasets or were transferred over by AFM when accessed by a researcher.  

The prioritized datasets were known to be actively used and were prime candidates to transfer when extra transfer capacity was available. 
{{% /accordion-item %}}

{{% accordion-item title="How can I get help with the data migration process?"  id="five" %}}
Researchers with an urgent need to access files that have not been migrated to the new Project storage system yet may submit a support request through our <a href="/form/support-request/?category=Storage&request_title=Project%20storage%20data%20migration&description=Please%20indicate%20as%20precisely%20as%20possible%20which%20directories%20or%20files%20should%20be%20transferred%20first:" target="_blank">webform</a>. **Please indicate as precisely as possible which folders or files should be transferred first so we can prioritize these items.**

If you need help with your file prioritization, you may reach out to RC to <a href="/form/support-request/?category=Storage&request_title=Old%20Project%20Storage:%20File%20List%20Request&description=Please%20send%20me%20a%20list%20of%20my%20files%20on%20old%20Project%20storage." class="card-link" target="_blank">request a list of files</a> that you still have on the old Project storage system.

All files will be transferred eventually. Questions about the data migration process should be directed to our <a href="/form/support-request/?category=Storage&request_title=Project%20storage%20data%20migration" class="card-link" target="_blank">user services team</a>.
{{% /accordion-item %}}

{{% /accordion-group %}}

## Technical Details

On February 26, RC engineers will disconnect the Active File Management (AFM) tether, remount the old Project storage system (GPFS) separately, and purge all "stub files" (files that are staged on new storage system and appear in a directory listing, but have not yet been transferred from old Project). This will allow a clear differentiation between transferred and un-transferred data. Data already transferred to the new Project storage system are expected to perform optimally without any issues, while un-transferred data on the old system will need to be manually transferred by RC staff. Staff will continue to respond to data transfer requests on a first come, first serve basis. Once the transfer process has been stabilized, engineers will begin transferring any remaining files that users did not explicitly request to be moved.

# Incident Status Log

{{% scrollable height="500px" %}}

- **2024-02-19, 02:00 PM**
Project storage is currently unavailable on Open OnDemand. On 26 February at 9:00 am EST, RC engineers will switch to an alternate data transfer mechanism between the legacy Research Project Storage filesystem and the new Project Storage system. As a result, users will no longer have direct access to the legacy system. Files will be staged to an intermediate location for users to copy. To facilitate the migration process, please indicate which directories or files should be prioritized for transfer using our data transfer request form. Additional information about the file transfer efforts and Project Storage system status is available on our Data Migration status page. 

- **2024-02-16, 01:22 PM**
On 26 February at 9:00 am EST, RC engineers will switch to an alternate data transfer mechanism between the legacy Research Project Storage filesystem and the new Project Storage system. As a result, users will no longer have direct access to the legacy system. Files will be staged to an intermediate location for users to copy. To facilitate the migration process, please indicate which directories or files should be prioritized for transfer using our data transfer request form. Additional information about the file transfer efforts and Project Storage system status is available on our Data Migration status page. 

- **2024-02-09, 06:22 PM**
SMB/NFS exports have been enabled for new Project storage. Data migration from old Project storage to new Project storage is ongoing. First-time access of old files and old directory listings is significantly slower than normal. Users may encounter on occasion “OSError: [Errno 5] Input/output errors” which should be reported through our support webform https://www.rc.virginia.edu/form/support-request/. For their ongoing work users should create new Project storage directories that are as close to the top level directory of their storage share as possible. Directory listings and traversals in these new top level directories is expected to show better performance. 

- **2024-02-08, 08:05 AM**
Rivanna is back in service following maintenance. Data migration from old Project storage to new Project storage is ongoing. First-time access of old files and old directory listings is significantly slower than normal. Users may encounter on occasion “OSError: [Errno 5] Input/output errors” which should be reported through our support webform https://www.rc.virginia.edu/form/support-request/. For their ongoing work users should create new Project storage directories that are as close to the top level directory of their storage share as possible. Directory listings and traversals in these new top level directories is expected to show better performance.

- **2024-02-07, 06:00 AM**
Rivanna, Research Project storage, and Research Standard storage will be down for maintenance on Tuesday, February 6 beginning at 6 a.m. All systems are expected to return to service by 6 a.m. on Wednesday, February 7.

- **2024-02-05, 07:55 AM**
Data migration from old Project storage to new Project storage is ongoing. First-time access of old files and old directory listings is currently significantly slower than normal. For their ongoing work users should create new Project storage directories that are as close to the top level directory of their storage share as feasible. Directory listings and traversals in these new top level directories is expected to show better performance. NFS and SMB mounts for new Project storage will be enabled on February 6. new Project storage will be made available through the Open OnDemand file browser at the same time.

{{% /scrollable %}}

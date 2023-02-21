Personal Time Tracking
======================

A basic tool for tracking time.  Useful for knowing how time is spent.  Ideally able to generate totals for use in other tools, like invoices and bug tracking systems.

------------
Requirements
------------

- Easy to use command line interface
- Keep track of what was being worked on, plus some general note
- Compute totals
    - Daily
    - Daily per category
    - Weekly
    - Weekly per category
    - Total over specified time range
    - Total over time range per category
- Compute totals by activity as well

-------------
Nice to haves
-------------

- Operates offline, does not require network connection
- Can sync between multiple devices to keep work from desktop and laptop synchronized between work sessions in different locations
- Can extract details for expor to other systems

----
Data
----

| Field | Type | Description |
| ----- | ---- | ----------- |
| Start | Timestamp | Start time for the entry |
| End   | Timestamp | End time for the entry |
| Category | Text | Name of the category |
| activity | Text | Activity within the category |
| Notes | Text | Freeform notes |

-----
Usage
-----

Ideal usage of the tool

> tc projectA activity working on result format
> tc projectB maintenance server free drive space
> tcdone
> tctotal
> tctotal projectA
> tctotal projectB
> tctotal -w
> tctotal -r 2021/01/01,2021/02/01

For syncing, between devices or when reconnecting to the network, any file syncing tool can be used.  This could be git, or rsync, or sftp.  Because this is a personal time tracking tool it is not envisioned for multiple people to be using it simultaneously.  No need to merge files.  The file being used, whichever device is the current workstation, is always the most current.

Also, issuing two start commands sequentially will automatically add a stop entry for the previous entry.


--------------
Implementation
--------------
A local file is the storage.  It can be copied to other devices for backup or for working offline.

Format will be human readable text.  Easy to make a change if needed, like forgetting to stop when done for the day.  The file can also be processed by separate tools as well, beyond the time tracker scripts

Should this be one script with command line arguments or multiple scripts each doing one specific part of the features.  Keeping the reporting separate from the data entry would let data entry be focused on editing the file and reporting focused on processing the file.

----------
References
----------
inspired by:  https://labs.tomasino.org/time-tracker-in-bash/

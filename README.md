# Choosing a sync service for dotfiles, scripts and more under Linux
###### by Stein Bakkeby, July 2019

I happen to be one of those guys that have more than one computer, let alone more than one operating systems. Having certain configuration, scripts, documents and files synchronised across machines have become an integral part of my workflow over the years.

Take web-browsing for example; With both Firefox and Google Chrome it is possible to keep bookmarks and extensions synchronised such that the browsing experience is the same regardless of where you are using it from. I use Linux almost exclusively and my preference is to have a similar consistency across Linux installations; the same .bashrc, aliases, scripts, tools, configuration, notes, etc. on every box. I want to be able to work on a project on my laptop and then switch over to resume working on my stationary desktop. If I add a new script or make a configuration change then I want that to be available on other installations as well.

I first started this back when Dropbox was new; I discovered the simple idea of having a ~/Dropbox/Desktop folder, then replacing ~/Desktop with a symlink to the one in the Dropbox directory. This allowed me to have the same desktop across installations; messy, but consistent. Needless to say things escalated after that.

After having used Dropbox like this for many years a three-device limit was introduced on free accounts in March 2019 which meant that it was no longer going to be viable in the long run for me. Of course I _could_ have just subscribed to Dropbox Plus for an annual fee of €120, but I don't really need 2 TB of cloud space and it seemed like a steep price to pay just to enable more devices.

So I started what would prove to become a long and arduous quest to find a suitable Dropbox replacement. It turned out to be a lot harder than I ever thought it would be.

In hindsight I concluded that it might be worth documenting my experience and thoughts on the various sync services I looked at and my reason for ultimately rejecting them, hence this writeup. This is not meant to be a thorough review of each of the various services, but more of a what worked and what did not work for me. I hope it might be useful to someone.

## Definition of sync

There are three principles of sync solutions:

> :left_right_arrow: A two-way (bi-directional) sync; files are kept in sync and identical across multiple machines
>
> :arrow_right: A one-way (upload) sync; this is essentially a _backup_ solution
>
> :arrow_left: A one-way (download) sync; the machine is a passive consumer of sync updates

For my intensive purposes I need a two-way sync to keep files in sync across multiple installations, ideally identical down to file permissions and timestamps.

## Requirements

Features and special requirements I have when considering a sync service. Mind you these were not all defined up-front; most of them only became apparent when experiencing flaws and shortcomings of various sync services.

  - Linux support
  - Two-way sync
  - Continuous sync (files are kept in sync automatically and continuously, rather than manually or at set intervals)
  - Support for synchronisation of symbolic links (symlinks) in a non-dereferencing manner (i.e. don't follow symlinks)
  - Offline access to sync files
  - Retention of file permissions (files should be identical across systems, including file permissions)
  - Selective sync (depending on the machine I may not need everything synced)
  - Performance (a sync operation should preferably not take ages to complete)
  - Initial setup time (when I set up a new VM or a new installation, how long does it take to get it up-to-speed with the sync service?)
  - Conflict resolution (how does the system handle conflicts? I prefer to keep most recently changed files)
  - Security (I don't consider anything on the internet to be truly secure, but the service should have at least some security measures in place)
  - Reliability (Consistent speed, predictable availability and the assurance that files are persisted correctly)
  - No device-count limit
  - Possibility to exclude certain file types (e.g. temporary files)

Nice to have:

  - Privacy (most cloud services require read access to files in order to provide additional services, as such others may have access to your files)
  - Encryption (some services offer file encryption for security reasons, not a must for me and I can always roll my own encryption if need be)
  - Versioning, i.e. the option to be able to view and revert to earlier versions of files
  - Free and Open Source Software (FOSS)
  - Possibility to sync more than one directory
  - LAN sync

There are often a myriad of additonal services offered by cloud solutions. Features such as file sharing, collaboration, etc. is not something that I have taken into account as they are irrelevant to what I want to achieve here.

## Sync services

Below is the list of sync services looked at and considered. Many of these I didn't even get around to trying out due to obvious issues conflicting with my requirements, for example no Linux support at the time of review. The order here is more or less the order in which I reviewed options.

### [![OneDrive](icons/onedrive.png)](https://onedrive.live.com/about/en-US/) [Microsoft OneDrive](https://onedrive.live.com/about/en-US/) (formerly SkyDrive)

> :x: No Linux support

### [![Google Drive](icons/google_drive.png)](https://www.google.com/drive/) [Google Drive](https://www.google.com/drive/)

> :x: No Linux support
>
> :information_source: There is an unofficial Linux client available called ODrive. While this might give remote access to files stored in Google Drive it does not provide the functionality to sync files locally. This means online access only.

### [![Jottacloud](icons/jottacloud.png)](https://www.jottacloud.com) [Jottacloud](https://www.jottacloud.com)

> :x: No Linux support

### [![Sync](icons/sync.png)](https://www.sync.com/) [sync.com](https://www.sync.com/)

> :x: No Linux support
>
> :heavy_check_mark: Offline access
>
> :heavy_plus_sign: Claimed security
>
> :heavy_plus_sign: Claimed privacy through encryption

### [![Zoho Docs](icons/zoho.png)](https://www.zoho.com/docs/) [Zoho Docs](https://www.zoho.com/docs/)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Offline access
>
> :heavy_check_mark: Selective sync
>
> :warning: Limited to five devices on the free version
>
> :heavy_check_mark: Fairly reasonably priced
>
> :heavy_plus_sign: Claimed security
>
> :x: No symlink support (just ignores them)

Zoho Docs comes across as fairly basic with very little configuration options.

### [![Box](icons/box.png)](https://www.box.com/) [Box](https://www.box.com/)

> :warning: Max file size of 250M
>
> :x: No Linux support

### [![Strongspace](icons/strongspace.png)](https://strongspace.com/) [Strongspace](https://strongspace.com/)

> :x: No Linux support

### [![iCloud](icons/icloud.png)](https://www.icloud.com/) [iCloud](https://www.icloud.com/)

> :x: No Linux support

### [![GoodSync](icons/goodsync.png)](https://www.goodsync.com/) [GoodSync](https://www.goodsync.com/)

> :x: No Linux support

### [![Syncplicity](icons/syncplicity.png)](https://www.syncplicity.com/) [Syncplicity](https://www.syncplicity.com/)

> :x: No Linux support

### [![MediaFire](icons/mediafire.png)](https://www.mediafire.com/) [Mediafire](https://www.mediafire.com/)

> :x: Turned out to be just a cloud storage with a web front end
>
> :x: No sync options
>
> :information_source: They used to have a (windows presumably) desktop client which was discontinued back in July 2016

### [![Workzone](icons/workzone.png)](https://www.workzone.com/) [Workzone](https://www.workzone.com/)

> :x: Although it has some file storage options, it turned out to be largely focused on project management for businesses
>
> :x: No single user option

### [![SparkleShare](icons/sparkleshare.png)](https://www.sparkleshare.org/) [SparkleShare](https://www.sparkleshare.org/)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: On premise solution (i.e. host your own)
>
> :heavy_check_mark: Free and Open Source Software (FOSS)
>
> :x: git based

SparkleShare is a git based solution where synced files are preserved in a git repository (for versioning and consistency purposes) and changes are pushed to other sync endpoints. Admittedly this work rather well for dotfiles and scripts, but the main reason why this does not work for me is that being git based it does not support syncing other git based repositories. I have certain projects that I want to keep in sync.

### [![Ubuntu One](icons/ubuntuone.png)](https://login.ubuntu.com/) [Ubuntu One](https://login.ubuntu.com/)

> :x: The service was shut down years ago :)
>
> :heavy_plus_sign: This is just to say that I miss you
>
> :heavy_plus_sign: Potentially it would have been a good candidate
>
> :x: No symlink support
>
> :information_source: The underlying software was released as [open source](https://launchpad.net/filesync-server)

### [![SugarSync](icons/sugarsync.png)](https://www.sugarsync.com/) [SugarSync](https://www.sugarsync.com/)

> :x: No Linux support

### [![Cozy Drive](icons/cozydrive.png)](https://cozy.io/) [Cozy Drive](https://cozy.io/)

> :heavy_check_mark: Linux support
>
> :x: Dereferences symlinks

### [![Syncthing](icons/syncthing.png)](https://syncthing.net/) [Syncthing](https://syncthing.net/)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Support for symlinks in a non-dereferencing manner
>
> :heavy_check_mark: Two-way sync
>
> :heavy_minus_sign: Some manual installation / setup / configuration required
>
> :heavy_check_mark: Possible to perform actions via the command line
>
> :heavy_check_mark: Free and Open Source Software (FOSS)
>
> :heavy_check_mark: LAN sync
>
> :information_source: No cloud solution (peer-to-peer only)
>
> :information_source: You have to set up both sides to connect two devices

Syncthing actually looks rather interesting. It is a peer-to-peer only two-way sync solution meaning no cloud is involved. Instead files are synced when computers are up. I don't always have more than one machine on so if I would take something like this then I would likely end up installing this on a NAS as well to have that "cloud" functionality.

I did not actually get around to try Syncthing out as I had some initial installation issues and I had concerns that this might potentially be time-consuming to set up for new installations (e.g. let's say I set up a quick virtual machine). The fact that I need both or multiple computers running for sync to work was also a slight turnoff, but can be addressed by installing it on a NAS. Syncthing is clearly a power user kind of option and my reason for not going with this is the assumed setup complexity when adding new (and maybe short-lived) devices / sync endpoints.

### [![Syncany](icons/syncany.png)](https://www.syncany.org/) [Syncany](https://www.syncany.org/)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Free and Open Source Software (FOSS)
>
> :heavy_minus_sign: The project has more or less been abandoned by the original developers

### [![CloudUp](icons/cloudup.png)](https://cloudup.com/) [CloudUp](https://cloudup.com/)

> :x: No sync options
>
> :x: It is a cloud service focused in file sharing
>
> :x: Public signups were disabled so was unable to get an account

### [![TeamDrive](icons/teamdrive.png)](https://teamdrive.com) [TeamDrive](https://teamdrive.com)

> :heavy_check_mark: Linux support
>
> :heavy_minus_sign: Only 2GB of free cloud storage for private use
>
> :heavy_plus_sign: Option to run a TeamDrive Personal Server for free, but limited to 10GB of data

This is clearly something that is more suited for business use to share files between teams. As a private user it does not make much sense buying into this, and the limited storage options for a free private account made it not worth it for me to look further into this solution.

### [![Mega](icons/mega.png)](https://mega.nz/) [Mega](https://mega.nz/)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Generous amount of storage space for a free account
>
> :heavy_check_mark: Possibility to sync more than one directory
>
> :heavy_check_mark: Selective sync
>
> :heavy_check_mark: Possibility to exclude certain file types
>
> :heavy_minus_sign: There is a transfer quota (per day presumably), not really an issue for my purposes
>
> :x: Dereferences symlinks
>
> :x: De-duplication process deletes files, which can be a disaster when combined with dereferencing symlinks

### [![SpiderOak](icons/spideroak.png)](https://spideroak.com/) [SpiderOak](https://spideroak.com/)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Two-way sync
>
> :heavy_check_mark: Selective sync
>
> :heavy_check_mark: Continuous sync (or optionally at specific intervals)
>
> :heavy_check_mark: Possibility to sync more than one directory
>
> :heavy_check_mark: Possible to perform actions via the command line (as long as the application is not already running in the background)
>
> :heavy_check_mark: No limit on the number of devices (though they recommend staying below ten)
>
> :heavy_check_mark: Excellent security (and they accurately state that logging in via mobile or your browser poses a security risk)
>
> :heavy_check_mark: Privacy through zero knowledge encryption
>
> :heavy_check_mark: Versioning
>
> :heavy_check_mark: LAN sync
>
> :heavy_check_mark: Possibility to exclude certain file types
>
> :heavy_minus_sign: Initial setup time
>
> :x: No symlink support (just ignores them)
>
> :x: Performance

SpiderOak ticks a _lot_ of boxes for me in terms of what their services offer and I have used SpiderOak for years, but for backup purposes only. I figured since I already had a subscription I would try using their sync service as well. Their sync directory is called "SpiderOak Hive" and the name is hardcoded as such (why did it have to contain a space?), but on the other hand you can disable that and set up multiple other directories to sync instead (e.g. ~/bin, ~/Desktop, etc.). One complication with this is that setting up a new sync is kind of backwards; first you need to add the directory that you want to sync as a _backup_ on each and every box that you are going to sync to. Only then can you create a new sync and select what backup folder you want synced to what backup folder on other devices. An additional annoyance is that although you can do a lot from the command line, you can't as far as I could tell create or update these sync settings that way, you have to do it via the GUI front end.

What turned out to be a major blocker for me was performance. Granted it will inevitably take more time to do things properly (secure, encrypted, zero knowledge) and I don't need my syncs to be blazingly fast. The problem was that I had used SpiderOak as a backup service for years and had ended up using something like 5TB of storage space. This means that if I wanted to set up SpiderOak on a new installation I had to go through a two-hour syndication process. In terms of sync it could take 5-10 minutes for a new or changed file to be updated on other sync endpoints. The syndication process also resulted in it being very time consuming to delete / purge data in a desperate attempt to try to free up disk space and improve performance.

In the end my impression is that SpiderOak was designed with backup in mind and that the sync service was more of an afterthought. The performance issues that I encountered are exceptional and should not be a deterrent for trying this service out. I have a lot of respect for what they have accomplished in terms of security and privacy. My only recommendation in hindsight is that it would be better use SpiderOak either as a dedicated backup or as a dedicated sync service. In my opinion they could very well have made two different applications / services out of it rather than having two in one.

While there is no symlink support at the very least the service just ignores them, which is something that I could live with.

### [![CloudMe](icons/cloudme.png)](https://www.cloudme.com) [CloudMe](https://www.cloudme.com)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Selective sync
>
> :heavy_check_mark: Offers three modes: two way sync (bidirectional), upload only (backup) and download only
>
> :heavy_minus_sign: Free account limited to 3GB of storage space and a maximum file size of 150M
>
> :heavy_check_mark: Possibility to sync more than one directory
>
> :heavy_minus_sign: Very few configuration options
>
> :x: No symlink support (just ignores them)

### [![Egnyte](icons/egnyte.png)](https://www.egnyte.com/) [Egnyte](https://www.egnyte.com/)

> :x: Sync option requires a business plan
>
> :warning: No free offering
>
> :warning: No individual offering (team / business only)

### [![Tresorit](icons/tresorit.png)](https://tresorit.com/) [Tresorit](https://tresorit.com/)

> :heavy_check_mark: Linux support
>
> :x: No symlink support (just ignores them)
>
> :heavy_minus_sign: No free offering, but there is a 14 day free trial period

### [![git](icons/git.png)](https://www.youtube.com/watch?v=dQw4w9WgXcQ) Rolling my own

I must admit that with so many lacklustre cloud storage services out there I started considering the option of rolling my own, possibly using git. I figured that I would have to use a git server, then have clients automatically pulling, commiting and pushing at regular intervals. In the end I gave up on these ideas as I wouldn't be able to use something like this for syncing directories containing git repositories, so I might as well just have used SparkleShare.

### [![Amazon Drive](icons/amazondrive.png)](https://www.amazon.com/b?ie=UTF8&node=15547130011) [Amazon Drive](https://www.amazon.com/b?ie=UTF8&node=15547130011)

> :x: No Linux support

### [![Resilio](icons/resilio.png)](https://www.resilio.com/) [Resilio](https://www.resilio.com/) (formerly BitTorrent Sync)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Selective sync
>
> :heavy_check_mark: Support for symlinks in a non-dereferencing manner
>
> :information_source: Torrent based peer-to-peer sync solution

Resilio sounds interesting and has many similarities to Syncthing. Being a peer-to-peer solution means that your computers need to be on for sync to work, unless you also install it on a NAS. While the setup of Resilio is supposed to be less complex than that of Syncthing my impression was that the latter had more clear and detail documentation on how it works. Overall I was not entirely convinced that a peer-to-peer sync solution was the right choice for me.

### [![Flickr](icons/flickr.png)](https://www.flickr.com/) [Flickr](https://www.flickr.com/)

> :x: No sync options

Just including this as it offers some cloud storage and is sometimes referred to as a "Dropbox alternative".

### [![Yandex Disk](icons/yandexdisk.png)](https://disk.yandex.com/) [Yandex Disk](https://disk.yandex.com/)

> :heavy_check_mark: Linux support
>
> :warning: On Linux there is no front end gui, only command line options (this can be a huge plus or a huge minus depending on your preferences)
>
> :heavy_minus_sign: Only syncs one folder
>
> :heavy_check_mark: Support for symlinks in a non-dereferencing manner

Yandex Disk might be OK, but it lacked a bit on the feature side for my needs.

### [![eFileCabinet](icons/efilecabinet.png)](https://www.efilecabinet.com/) [eFileCabinet](https://www.efilecabinet.com/)

> :x: No Linux support

### [![Filestack](icons/filestack.png)](https://www.filestack.com/) [Filestack](https://www.filestack.com/)

> :x: Turned out to be just a cloud storage with a web front end
>
> :x: No sync options
>
> :x: Only 500M of storage for a free account
>
> :x: Expensive for a subscription

### [![Seafile](icons/seafile.png)](https://www.seafile.com) [Seafile](https://www.seafile.com)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Terminal client as well as front end client
>
> :heavy_check_mark: Selective Sync
>
> :heavy_check_mark: Version control
>
> :heavy_check_mark: Free community edition
>
> :x: Dereferences symlinks

### [![WeTransfer](icons/wetransfer.png)](https://wetransfer.com/) [WeTransfer](https://wetransfer.com/)

> :x: Turned out to be just a cloud storage with a web front end
>
> :x: No sync options
>
> :x: Just a service to send (large) files to others

### [![Fex.net](icons/fexnet.png)](https://fex.net/) [Fex.net](https://fex.net/)

> :x: Turned out to be just a cloud storage with a web front end
>
> :x: No sync options

### [![Adobe Creative Cloud](icons/adobecreativecloud.png)](https://www.adobe.com/creativecloud.html) [Adobe Creative Cloud](https://www.adobe.com/creativecloud.html)

> :x: No (native) Linux support

### [![Degoo](icons/degoo.png)](https://degoo.com) [Degoo](https://degoo.com)

> :heavy_minus_sign: Free version is just a cloud storage with a web front end
>
> :heavy_check_mark: Zero knowledge encryption
>
> :x: Subscription required for sync options
>
> :x: Limited to three desktop devices unless you subscribe to the Ultimate package
>
> :x: No Linux support

### [![Koofr](icons/koofr.png)](https://koofr.eu/) [Koofr](https://koofr.eu/)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Selective Sync
>
> :x: Dereferences symlinks

### [![IDrive](icons/idrive.png)](https://www.idrive.com/) [IDrive](https://www.idrive.com/)

> :heavy_check_mark: Linux support
>
> :x: Dereferences symlinks

### [![FlipDrive](icons/flipdrive.png)](https://www.flipdrive.com/) [FlipDrive](https://www.flipdrive.com/)

> :warning: Free account has a 25M file size limit
>
> :x: No Linux support

### [![insync](icons/insync.png)](https://www.insynchq.com/) [insync](https://www.insynchq.com/)

> :heavy_check_mark: Linux support
>
> :information_source: insync is not actually a service, but a standalone client that can talk to multiple cloud services, most notably Google Drive
>
> :x: Dereferences symlinks (if symlinked directory has not already been synced, i.e. exists in sync / backup)

### [![ExpanDrive](icons/expandrive.png)](https://www.expandrive.com/) [ExpanDrive](https://www.expandrive.com/)

> :heavy_check_mark: Linux support
>
> :information_source: Like insync, ExpanDrive is not actually a service, but a standalone client that can talk to multiple cloud services such as Strongspace, Dropbox, Google Drive, box, OneDrive, Amazon Drive, Nextcloud as well as several other options
>
> :information_source: No free option, 7 day trial
>
> :information_source: No files are stored locally; cloud storage files are accessible through a virtual drive as long as ExpanDrive is running and is connected
>
> :information_source: File permissions appear to be fixed at 755 (rwxr-xr-x) for all files
>
> :information_source: Practically no additional settings
>
> :x: No offline access
>
> :x: No sync option

### [![Bynder Orbit](icons/bynderorbit.png)](https://www.bynder.com) [Bynder Orbit](https://www.bynder.com)

> :x: Business focus only
>
> :x: No sync option as far as I can tell

### [![pCloud](icons/pcloud.png)](https://www.pcloud.com/) [pCloud](https://www.pcloud.com/)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Two-way sync
>
> :heavy_check_mark: Selective sync
>
> :heavy_check_mark: Continuous sync
>
> :heavy_check_mark: Possibility to sync more than one directory
>
> :heavy_check_mark: No hard limit on the number of devices (though they recommend not linking more than five)
>
> :heavy_check_mark: Versioning
>
> :heavy_check_mark: LAN sync
>
> :heavy_check_mark: Possibility to exclude certain file types
>
> :heavy_check_mark: Initial setup time (just install the client and you are done)
>
> :heavy_minus_sign: Frequent notifications made the service come across as nagware
>
> :heavy_plus_sign: a crypto service add-on is also offered, which is limited to files being stored in a "Crypto Folder" subdirectory
>
> :x: No symlink support (just ignores them)
>
> :x: File permissions are not preserved (i.e. execute permissions are lost)

Now pCloud is kind of different in that by design it is an Online only cloud service. Essentially it means that anything you move into the pCloud folder is for all practial purposes _deleted_ from your system. Depending on your needs this can be a very good thing or it may not be. For example this could allow you keep all of the photos you take in pCloud, saving up space on your mobile device. This is something that turned out to be an appeal for me as well. For example I don't need to have my documents synced to each and every installation, but it can be useful to have such a straightforward access to them if need be.

Ultimately this means that to be able to see and open your files you will need online access. Should you need offline access to your files then you would have to set up additional syncs between the cloud service and individual local folders. This actually works rather well, but a big issue for me is that due to the nature of how the cloud service works the file permissions are not being retained. The end effect of this is that the executable permissions for files are not preserved, which is a bit of a blocker for me as I rely on quite a few shell scripts. Granted I could manage to work around this, but in the end I concluded that it was not worth the long term effort to do so.

### [![Nextcloud](icons/nextcloud.png)](https://nextcloud.com/) [Nextcloud](https://nextcloud.com/)

> :heavy_check_mark: On premise solution (i.e. host your own) or optionally sign up with a provider
>
> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Two-way sync
>
> :heavy_check_mark: Selective sync
>
> :heavy_check_mark: Continuous sync
>
> :heavy_check_mark: Possibility to sync more than one directory
>
> :heavy_check_mark: No hard limit on the number of devices
>
> :heavy_check_mark: Versioning
>
> :heavy_minus_sign: No local peer-to-peer LAN sync, however as this is an on premise solution it does not matter much
>
> :heavy_check_mark: Possibility to exclude certain file types
>
> :heavy_check_mark: Preserves file permissions
>
> :heavy_minus_sign: Conflict resolution
>
> :x: No symlink support (just ignores them)

Nextcloud is pretty awesome. Setting up a self-hosted cloud service can present some challenges even for novice users. I happen to own a Synology DS918+ Network Attached Storage (NAS) which to say is versatile would be an understatement. To set up Nextcloud on this NAS all I really needed to do was to download two docker images (one for Nextcloud, and one for the Mariadb database) and figuring out how to link and make these run with the right settings. On the computers using this host I only needed to install the nextcloud client.

Such a cloud service would then only work within your local network. Should you need this "on the go" as well then getting it exposed on the web can potentially be challenging.

Nextcloud ticks a lot of boxes for me and has a fair amount of features and I may very well end up using this for something else in the future. What was kind of annying for me is that it does not support syncing symlinks. What was more annoying is that every symlink that exists comes up as a warning, which can make it difficult to differentiate them from actual warnings. It was also not quite clear how Nextcloud handles conflicts. This may be wrong, but it seemed that if a client has started syncing and is interrupted (let's say by a restart), then the next time it starts syncing any files that differ from the server are moved away and the files from the server are restored.

That Nextcloud managed to come up with conflicted files when I was only running one host and one client was one of the main reasons why I did not stop looking for alternatives.

### ![ownCloud](icons/owncloud.png) ownCloud

> :information_source: Given that Nextcloud is built on ownCloud I did not try this one out, I'd expect similar pros and cons though

### [![Pydio](icons/pydio.png)](https://pydio.com/) [Pydio](https://pydio.com/)

> :heavy_check_mark: On premise solution (i.e. host your own)
>
> :heavy_check_mark: Linux support
>
> :heavy_minus_sign: No versioning
>
> :heavy_minus_sign: Deprecated in favour of Pydio Cells; security fixes only, no new features, official end of life scheduled for December 2019

Pydio appears to be more focused on file sharing and if going for something like this then I think Pydio Cells would be a better option.

### [![Pydio Cells](icons/pydiocells.png)](https://pydio.com/) [Pydio Cells](https://pydio.com/)

> :heavy_check_mark: On premise solution (i.e. host your own)
>
> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Versioning
>
> :heavy_minus_sign: PydioSync not supported yet as of time of writing

Pydio Cells is a complete re-implementation / re-design of Pydio into a micro-services architecture and has a stronger focus on collaboration and sharing.

While Pydio seems like a very capable file management platform it is also more of a business solution and is very far from the simple file syncing solution that I am looking for.

### [![Synology Drive](icons/synologydrive.png)](https://www.synology.com/en-global/dsm/feature/drive) [Synology Drive](https://www.synology.com/en-global/dsm/feature/drive)

> :heavy_check_mark: On premise solution (i.e. host your own) through Synology NAS
>
> :heavy_check_mark: Can also work as an online service thanks to Synology QuickConnect
>
> :heavy_minus_sign: You need to own a Synology NAS in order to be able to install and use this
>
> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Two-way sync, one-way upload and one-way download options
>
> :heavy_check_mark: Options for routine backup tasks
>
> :heavy_check_mark: Selective sync
>
> :heavy_check_mark: Continuous sync
>
> :heavy_check_mark: Possibility to sync more than one directory
>
> :heavy_check_mark: No hard limit on the number of devices
>
> :heavy_check_mark: Versioning
>
> :heavy_check_mark: Conflict resolution (option to keep the last modified version or to keep the version on the server)
>
> :heavy_minus_sign: No local peer-to-peer LAN sync, however as this is an on premise solution it does not matter much
>
> :heavy_check_mark: Possibility to exclude certain file types
>
> :heavy_check_mark: Preserves file permissions
>
> :heavy_check_mark: Supports synchronisation of symlinks in a non-dereferencing manner
>
> :heavy_check_mark: Easy and intuitive to set up on the NAS side
>
> :heavy_check_mark: Easy and intuitive to set up on client / desktop side

So I happened to receive one of these Synology newsletters informing me that Synology Drive 2.0 had been released. I had never seen it before, nor heard of anyone ever talking about or recommending it. I figured that I might as well just try it out; after all how is one more going to hurt?

I must say that Synology Drive 2.0 came as a huge surprise and ultimately ticked all of the boxes for me. It does everything I want it to do, and nothing that I do not want. It is an excellent example of doing one thing, and doing it really well.

As for other features you have options to share files via Synology QuickConnect links, you can have a Team Folder for collaboration efforts and you can both star and label files and directories if need be.

I think that it is safe to say that Synology Drive concludes my search for a viable Dropbox replacement and that it hits the ball out of the park. It is hands down the best file sync solution that I have come across on this quest.

----

As an epilogue let's take these experiences into account and revisit the service that I was trying to move away from.

### [![Dropbox](icons/dropbox.png)](https://www.dropbox.com) [Dropbox](https://www.dropbox.com)

> :heavy_check_mark: Linux support
>
> :heavy_check_mark: Two-way sync
>
> :heavy_check_mark: Selective sync (can choose not to download / sync certain subdirectories)
>
> :heavy_check_mark: Continuous sync
>
> :heavy_minus_sign: Not possible to sync more than one directory
>
> :heavy_minus_sign: Limited to three devices unless you pay for a subscription
>
> :heavy_check_mark: Versioning
>
> :heavy_check_mark: Conflict resolution (the conflicted file contains the name of the origin host, which is nice)
>
> :heavy_check_mark: LAN sync
>
> :heavy_minus_sign: Not possible to exclude certain file types
>
> :heavy_check_mark: Preserves file permissions
>
> :x: ~~Dereferences symlinks~~

Pretty good actually, but not all good. Again we see a sync service that _dereferences_ symlinks.

So what's the deal with that anyway? I believe lay people like it because they only use one computer and they only need to add symlinks to other directories that they want to back up.

This is a clear case of a one-way (upload) sync which translates to a backup solution.

If you have a two-way (bi-directional) sync between computers then things get more complicated. As an example my first encounter with this issue was that within my ~/Dropbox directory I had ended up creating a symlink to another directory, let's say referring to ~/Dropbox/Documents.

When moving from my laptop to my desktop I happen to discover that what was a symlink on the other machine was now an actual folder duplicating every file in the other directory. That's not what I intended. Wanting to clean up this mess and without further ado I deleted the duplicated folder (it held the exact same data after all). What happens next is that Dropbox syncs this action resulting in the symlink being deleted on the other machine, the twist being that it again follows the symlink and deletes the main ~/Dropbox/Documents folder as well. This of course results in another sync action and all documents end up being deleted everywhere. Experimenting with this flaw I found that in scenarios like this Dropbox can also end up deleting files _outside_ of the ~/Dropbox directory. So not quite so safe and isolated as I had been led to believe.

In conclusion following symlinks is something that only makes sense for one-way (upload/backup) solutions and not for two-way (bi-directional) sync solutions. I believe that so many cloud services get this wrong because they try to do both at the same time. There is undoubtedly also pressure to offer features that other more popular services do and I have seen many discussions arguing that following symlinks is justified because "Dropbox does this".

My advice is to be clear about which of the three principles of sync solutions you need (sync, upload or download) and choose your sync service accordingly.

---
**Edit**: Turns out that Dropbox no longer dereferences symlinks since mid-2019 \[[ref](https://help.dropbox.com/installs-integrations/sync-uploads/symlinks)\]

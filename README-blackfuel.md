blackfuel / asuswrt-merlin
==========================

The goal of this project is to leverage the efforts of the excellent Asuswrt-Merlin project and to extend it with additional kernel features that will make your router more useful, reliable and secure.  It is an enhanced version of Asuswrt - the firmware used by all recent Asus routers.

Useful
------
- Additional USB features are enabled in the kernel to allow USB-to-Serial converters and/or USB HID class devices to be connected to your router.  Connect an uninterruptible power supply, Arduino or serial device to your router.  This could open the door for home automation, smart home technologies and integration with other tech gadgets.
- Mount an ISO or UDF image and advertise it on a Samba share.

Reliable
--------
- A GPS-backed NTP server means that every device on your LAN will synchronize its clock locally.  No Internet connection is required for time synchronization.  Now all your devices can synchronize their clocks with a GPS receiver via the NTP server running on your router.
- Removal of some unwanted apps and features from the original Asus firmware means that there are less things to go wrong, and your router is less likely to do something unexpected.
- Optionally compile your own pre-built apps into the firmware image for high availability purposes or other reasons where it does not make sense to run the app from an external USB storage device.  For example, Dnscrypt is an app that performs DNS lookups and it should be compiled into the firmware, since without it, LAN clients would not be able to access the Internet.  Another example is Cryptsetup because it cannot be installed on an encrypted USB storage device when it's the program used to mount the encrypted USB storage device.  Any pre-built app may be compiled into the firmware image.  This allows you to run any Entware, Optware or Asuswrt-linked app side-by-side within the firmware. And since the firmware is squashfs compressed, all of your pre-built apps are safely and securely compressed into the read-only firmware image.  The technique for doing this is a set of tools that change the library root folder for each selected program and its dependencies, from "/opt" to "/entware", "/optware", "/native", or some other root directory name.

Secure
------
- Real-time disk encryption with dm-crypt and LUKS secures your NAS.  For example, now you can run an E-mail server on your router and it will be secured with disk encryption.  I found success with the XMail and Dovecot packages from the Entware-ng repository, as a reliable IMAP/POP3/SMTP service running on your router.  It is really amazing what this little router is capable of.
- An Arduino Pro Mini 3.3V is used to temporarily write a passphrase into the router's RAM, for the purpose of mounting an encrypted disk at startup, without needing to permanently store the passphrase inside the router itself.  Once the router has mounted the encrypted disk, it simply deletes its copy of the passphrase, for security purposes.  If your router and external USB storage device are ever taken from you, the passphrase is kept safe inside the Arduino microcontroller.  It can be quickly connected and disconnected from the router, or tethered on a long cable up to 40 meters away.  Perhaps my Arduino is hidden in the wall, or accesses another Arduino over a wireless link to fetch the passphrase? 

*Who doesn't love these types of features?*

All ARM models are supported:

- RT-AC56U
- RT-AC68U
- RT-AC87U
- RT-AC88U
- RT-AC3100
- RT-AC3200
- RT-AC5300

**This firmware's filesystem has a new root folder that contain additional programs.**

Folder | Description
------ | -----------
**/entware** | *Pre-built programs linked against the Entware-ng libraries.*


### Donations may be sent to my Bitcoin address: 1i5Tpno73gJdr1XdmoxT6CjVFGef5KkZM
Any amount is appreciated.  This helps me share new material and pay the bills.  Thank you.

blackfuel/asuswrt-merlin
========================

This is an enhanced version of Asuswrt - the firmware used by all recent Asus routers.

The goal of this project is to leverage the efforts of the Asuswrt-Merlin project and to
extend it with additional kernel features that make the router more useful, reliable and
secure.

Useful
- Additional USB features are enabled in the kernel to allow USB-to-Serial converters and/or USB HID class devices to be connected to the router.  Connect an uninterruptible power supply, Arduino or serial device to the router.  This could open the door to home automation, smart home technologies and integration with other tech gadgets.
- Mount an ISO or UDF image.

Reliable
- A GPS-backed NTP server means that every device on your LAN synchronizes its clock locally.  No Internet connection is required for time synchronization.  Now all your devices can synchronize their clocks with a GPS receiver via the NTP server running on the router.
- Removal of some unwanted apps and features from the original Asus firmware means there are less things to go wrong, and the router is less likely to do something unexpected.

Secure
- Real-time disk encryption with dm-crypt and LUKS secures your NAS.  For example, now you can run an E-mail server on the router and it will be secured with disk encryption.  I found success with XMail + Dovecot packages from the Entware-NG repository, as reliable IMAP/POP3/SMTP servers running on the router.  It is really amazing what this little router is capable of.
- My two-factor pre-boot authentication technique uses an Arduino Pro Mini to temporarily write a passphrase into the routers RAM, for the purpose of mounting an encrypted disk at startup without needing to permanently store the passphrase inside the router itself.  If your router and external USB storage device are ever taken from you, the passphrase is kept safe on an Arduino microcontroller that can be conveniently connected and disconnected, or tethered on a long cable up to 40 meters away.  Perhaps my Arduino is hidden in the wall, or accesses another Arduino over a wireless link to fetch the passphrase?  

Who doesn't love these types of features?

At this time, the supported devices are:

- RT-AC56U
- RT-AC68U

The USB modem and WiMAX support is disabled in this version of the kernel because it was not compatible with the USB serial port drivers.


## Enable Firewall

    `System Preferences -> Security & Privacy -> Firewall -> Turn on Firewall`
    Enables the standard Mac firewall, which helps to monitor and block certain network traffic.

    While there go to firewall options and `Enable Stealth Mode`



## Enable FileVault

`System Preferences -> Security & Privacy -> Filevault -> Turn on Filevault`

Filevault is Mac's disk encryption. If you want to decrease the attack surface of your computer, encryption is the way to go. Encryption will make it impossible for people to reboot your computer, pop in another OS and simply change some files around on your computer to avoid all sort of authentication.



## Destroy Filevault keys on standby

By default, the Filevault encryption key is held in memory on standby, thus allowing a smart attacker to extract the key from there. Therefore being able to decrypt your own drive. This setting drops the Filevault key and, therefore, requires you to login again after going into standby mode. Simply run this in the terminal:
```
$ sudo pmset -a destroyfvkeyonstandby 1
$ sudo pmset -a hibernatemode 25

```
If you set the above parameter, it is better to also change your powernap and standby settings (more on it, can be read here):

$ sudo pmset -a powernap 0
$ sudo pmset -a standby 0
$ sudo pmset -a standbydelay 0
$ sudo pmset -a autopoweroff 0
1. Check Privacy permissions

System Preferences -> Security & Privacy -> Privacy -> Location Services
Not all programs should have access to sensitive information, such as your location. Thus, check the list of programs who have access to it and remove programs, which shouldn't.



4. Disable Creation of Metadata Files

Mac OS creates .DS_STORE files in directories for better performance when accessing the file system. While these files are relevant on your own operating system, they should not be added to USB, external hard- or network drives. These two settings change this, so no metadata file is written to them.
On Networks drive, disable the creation of .DS_STORE files using:

$ defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true
On USB drives:

$ defaults write com.apple.desktopservices DSDontWriteUSBStores -bool true
5. Disable diagnostics

System Preferences -> Security & Privacy -> Privacy -> Diagnostics & Usage
When we are concerned about security, we are also concerned about sharing too much information. Or at least being selective with the information we do share. Disabling the diagnostic setting will help keep the information within our circle of influence.



6. Disable Guest User

The guest user account is an inherent risk as it allows an unauthenticated user into the system. While the guest user account doesn't have many privileges, it's still a security risk.

If you are in need of the guest user, such as when someone else wants to use your computer (as happens in this world), I simply reactivate it with very constrained privileges.



7. Disable password hints

This one speaks for itself. Any hints toward being able to make more educated guesses as to the password you are using should be avoided.



8. Disable recent items

Recent items can be, and often are used, in forensic computer analysis. Disabling it, denies it as a potential source of information.



9. Disable Spotlight localization & suggestions

Both of these disable the sending of unnecessary information to both Apple and Microsoft when using Spotlight.

System Preferences -> Spotlight -> Search Results


System Preferences -> Security & Privacy -> Location Services -> System Services -> Details


10. Enable Screensaver

System Preferences -> Desktop & Screen Saver
Set the screensaver to start after 5 minutes. Together with the below changes, it will lock your screen on starting the screensaver.



11. Require an administrator password

Require an admin password to access system settings.
System Preferences -> Security & Privacy -> Advanced...



12. Require a password to unlock

System Preferences -> Security & Privacy
This option requires you to enter a password after sleep or the screensaver begins.



13. Save to Disk by Default

There are a couple of programs, such as Pages, Keynote, Numbers and others which are by default setup to save files in iCloud. The command disables it:

$ defaults write NSGlobalDomain NSDocumentSaveNewDocumentsToCloud -bool false
14. Show all filename extensions

Finder -> Preferences -> Advanced
As a security aware person, it's important to knowthe extensions of files, as it controls how a file is opened and processed. By default, not all filename extensions are shown in Finder. This changes that.



15. Set a firmware password

Setting a firmware password is essential to avoid hackers being able to bypass the login password by simply booting into single user mode or altering your hard drive.
A firmware password requires you to first enter a password before being able to boot from another operating system.

Take the following steps:

Restart your Mac and press the Command R keys to boot to Recovery Mode mode.

After a little bit, the OS X Utilities will appear. Choose Firmware Password Utility from the Utilities menu.

In the Firmware Utility window, select Turn On Firmware Password and follow the wizard.

Quit the Firmware Utility and restart your computer.

The password will be activated on the next bootup. You can check whether it worked, by going into Recovery Mode again and see if you are prompted for a password.

16. Turn off Autologin

System Preferences -> Users & Groups -> Login Options
Turn off automatic login to only let authorized people use the computer.



17. Deactivate Restart and Shutdown

System Preferences -> Users & Groups -> Login Options
Restricting the behavior of unauthenticated users in the login menu is always a good idea. This hides the sleep, restart and shutdown buttons in the login dialog.



18. Disable Captive Portal

When MacOS connects to new networks, it probes the network and launches a Captive Portal assistant utility if connectivity can't be determined. However, this assistant can potentially be exploited. This command disables Captive Portal:

$ sudo defaults write /Library/Preferences/SystemConfiguration/com.apple.captive.control Active -bool false
Next up
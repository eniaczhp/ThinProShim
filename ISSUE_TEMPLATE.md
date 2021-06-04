Make sure you have provided the following information:

 - [x] link to your code branch cloned from keybase shim-review repo
 - [x] completed README.md file with the necessary information
 - [x] shim.efi to be signed
 - [x] public portion of your certificate(s) embedded in shim (the file passed to VENDOR_CERT_FILE)
 - [x] binaries, for which hashes are added do vendor_db ( if you use vendor_db and have hashes whitelisted )
 - [x] any extra patches to shim via your own git tree or as files
 - [x] any extra patches to grub via your own git tree or as files
 - [x] build logs


###### What organization or people are asking to have this signed:
    HP Inc.

###### What product or service is this for:
    ThinPro for PC (an Ubuntu based Linux variant).  This is not our first linux release.  The actual version is 7.1/7.2.

###### What is the origin and full version number of your shim?
    https://github.com/rhboot/shim/tree/15

###### What's the justification that this really does need to be signed for the whole world to be able to boot it:
    Previous ThinPro are only released with HP hardwares support.  The next ThinPro release is targeted for not just HP's machines, but also general PC from other vendors.  We need our bootloader to be signed by MS UEFI key for it to be bootable there.

###### How do you manage and protect the keys used in your SHIM?
    The cert and keys are protected by HP's signing infrastructure.  Developer doesn't have direct access to the key.

###### Do you use EV certificates as embedded certificates in the SHIM?
    No

###### If you use new vendor_db functionality, are any hashes whitelisted, and if yes: for what binaries ?
    N/A

###### Is kernel upstream commit 75b0cea7bf307f362057cc778efe89af4c615354 present in your kernel, if you boot chain includes a linux kernel ?
    Yes

###### if SHIM is loading grub2 bootloader, is CVE CVE-2020-10713 fixed ?
    Yes

##### Were your old SHIM hashes provided to Microsoft ?
    Yes

##### Did you change your certificate strategy, so that affected by CVE CVE-2020-10713 grub2 bootloaders can not be verified ?
    Yes

###### What is the origin and full version number of your bootloader (GRUB or other)?
    Grub 2.04

###### If your SHIM launches any other components, please provide further details on what is launched
    It launches grub2 and fwupd

###### How do the launched components prevent execution of unauthenticated code?
    Full set of grub2 fixes, fwupd will not execute unauthenticated code.

###### Does your SHIM load any loaders that support loading unsigned kernels (e.g. GRUB)?
    No, our shim and grub will not load any unsigned binary when the system boots under
    secure boot mode.

###### What kernel are you using? Which patches does it includes to enforce Secure Boot?
    5.6.8, maybe move to a newer kernel later this year.  it has all the secureboot lockdown patches.

###### What changes were made since your SHIM was last signed?
    Update 13 to 15, plus shim-patches from photon branch

###### What is the hash of your final SHIM binary?
$ sha256sum shimx64.efi
c3615588e7ba3d9c52a60014d4b84eb440b86404b3213c6a650e273965268a8f  shimx64.efi
$ sha1sum shimx64.efi
5f33fb7c60b5548e49abbc2bc5d0f9ddfab9aab2  shimx64.efi


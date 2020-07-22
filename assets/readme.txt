# What organization or people are asking to have this signed:

    HP Inc.

# What product or service is this for:

    ThinPro for PC (an Ubuntu based Linux variant).  This is not our first linux release.  The actual version is 7.1/7.2.

# What's the justification that this really does need to be signed for the whole world to be able to boot it:

    Previous ThinPro are only released with HP hardwares support.  The next ThinPro release is targeted for not just HP's machines, but also general PC from other vendors.  We need our bootloader to be signed by MS UEFI key for it to be bootable there.

# Who is the primary contact for security updates, etc.

    Name: Eniac Zhang
    Position: Engineer
    Email address: eniacz@hp.com
    PGP key, signed by the other security contacts, and preferably also with signatures that are reasonably well known in the linux community: n/a

# Who is the secondary contact for security updates, etc.

    Name: Frick, Michael <michael.frick@hp.com>
    Position: Manager
    Email address: michael.frick@hp.com
    PGP key, signed by the other security contacts, and preferably also with signatures that are reasonably well known in the linux community: n/a

# What upstream shim tag is this starting from:

    https://github.com/rhboot/shim/tree/15

# URL for a repo that contains the exact code which was built to get this binary:

    https://github.com/eniaczhp/ThinProShim/tree/20200722

# What patches are being applied and why:

    none

# What OS and toolchain must we use to reproduce this build? Include where to find it, etc. We're going to try to reproduce your build as close as possible to verify that it's really a build of the source tree you tell us it is, so these need to be fairly thorough. At the very least include the specific versions of gcc, binutils, and gnu-efi which were used, and where to find those binaries.
   
    See method.txt for configuration details

# Which files in this repo are the logs for your build? This should include logs for creating the buildroots, applying patches, doing the build, creating the archives, etc.

    See build.log

# Put info about what bootloader you're using, including which patches it includes to enforce Secure Boot here:

    It's grub2 with the well known set of secure boot patches (among other patches.)

# Put info about what kernel you're using, including which patches it includes to enforce Secure Boot here:

    It will use kernel version 5.6.4 and above, which has the well known set of secure boot patches.


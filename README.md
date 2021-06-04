This repo is for review of requests for signing shim.  To create a request for review:

- clone this repo
- edit the template below
- add the shim.efi to be signed
- add build logs
- add any additional binaries/certificates/hashes that may be needed
- commit all of that
- tag it with a tag of the form "myorg-shim-arch-YYYYMMDD"
- push that to keybase
- use channel names under your vendor/company to discuss the review process and to get an approval
- approval is ready when you have Approved-by: Peter Jones <pjones@redhat.com> or TODO: add list of confirmed approvers

Note that we really only have experience with using grub2 on Linux, so asking
us to endorse anything else for signing is going to require some convincing on
your part.

Here's the template:

-------------------------------------------------------------------------------
What organization or people are asking to have this signed:
-------------------------------------------------------------------------------
    HP Inc.

-------------------------------------------------------------------------------
What product or service is this for:
-------------------------------------------------------------------------------
    ThinPro for PC (an Ubuntu based Linux variant).  This is not our first linux release.  The actual version is 7.1/7.2.

-------------------------------------------------------------------------------
What's the justification that this really does need to be signed for the whole world to be able to boot it:
-------------------------------------------------------------------------------
    Previous ThinPro are only released with HP hardwares support.  The next ThinPro release is targeted for not just HP's machines, but also general PC from other vendors.  We need our bootloader to be signed by MS UEFI key for it to be bootable there.

-------------------------------------------------------------------------------
Who is the primary contact for security updates, etc.
-------------------------------------------------------------------------------
- Name: Eniac Zhang
- Position: engineer
- Email address: eniacz@hp.com
- PGP key, signed by the other security contacts, and preferably also with signatures that are reasonably well known in the linux community: n/a

-------------------------------------------------------------------------------
Who is the secondary contact for security updates, etc.
-------------------------------------------------------------------------------
- Name: Frick, Michael <michael.frick@hp.com>
- Position: manager
- Email address: michael.frick@hp.com
- PGP key, signed by the other security contacts, and preferably also with signatures that are reasonably well known in the linux community: n/a

-------------------------------------------------------------------------------
What upstream shim tag is this starting from:
-------------------------------------------------------------------------------
    https://github.com/rhboot/shim/

-------------------------------------------------------------------------------
URL for a repo that contains the exact code which was built to get this binary:
-------------------------------------------------------------------------------
    https://github.com/vathpela/shim-review/
    tag: HPI-shim-x64-20210603
    please build the shim with command:
  $ docker build -t hpishim -f hpishim.docker .

-------------------------------------------------------------------------------
What patches are being applied and why:
-------------------------------------------------------------------------------
none

-------------------------------------------------------------------------------
If bootloader, shim loading is, grub2: is CVE-2020-10713 fixed ?
-------------------------------------------------------------------------------
yes, we use grub2_2.04-1ubuntu45 which has all the latest grub fixes.

-------------------------------------------------------------------------------
If you use vendor_db functionality of providing multiple certificates and/or
hashes please briefly describe your certificate setup. If there are whitelisted hashes
please provide exact binaries for which hashes are created via file sharing service,
available in public with anonymous access for verification
-------------------------------------------------------------------------------
n/a

-------------------------------------------------------------------------------
Do you use EV certificates as embedded certificates in the SHIM?
-------------------------------------------------------------------------------
no

-------------------------------------------------------------------------------
Are you re-using a previously used (CA) certificate?
-------------------------------------------------------------------------------
no, we created new CA for this.

-------------------------------------------------------------------------------
Please provide exact SBAT entries for all SBAT binaries you are booting or planning to boot directly through shim
-------------------------------------------------------------------------------

# cat sbat.csv
sbat,1,SBAT Version,sbat,1,https://github.com/rhboot/shim/blob/main/SBAT.md
shim,1,UEFI shim,shim,1,https://github.com/rhboot/shim
shim.thinpro,1,HP,shim,15.4,https://www.hp.com/

# cat grub.sbat
sbat,1,SBAT Version,sbat,1,https://github.com/rhboot/shim/blob/main/SBAT.md
grub,1,Free Software Foundation,grub,2.04,https://www.gnu.org/software/grub/
grub.thinpro,1,HP,grub2,2.04-1ubuntu45+hp1,https://www.hp.com/


-------------------------------------------------------------------------------
What OS and toolchain must we use to reproduce this build?  Include where to find it, etc.  We're going to try to reproduce your build as close as possible to verify that it's really a build of the source tree you tell us it is, so these need to be fairly thorough. At the very least include the specific versions of gcc, binutils, and gnu-efi which were used, and where to find those binaries.
-------------------------------------------------------------------------------
Ubuntu Bionic 18.04, all details are contained in the docker script

-------------------------------------------------------------------------------
Does your SHIM load any loaders that support loading unsigned kernels (e.g. GRUB)?
-------------------------------------------------------------------------------
no, our shim/grub will not load unsigned kernel when booting under secure boot mode.

-------------------------------------------------------------------------------
Which files in this repo are the logs for your build?   This should include logs for creating the buildroots, applying patches, doing the build, creating the archives, etc.
-------------------------------------------------------------------------------
build.log

-------------------------------------------------------------------------------
What is the SHA256 hash of your final SHIM binary?
-------------------------------------------------------------------------------
c3615588e7ba3d9c52a60014d4b84eb440b86404b3213c6a650e273965268a8f  shimx64.efi

-------------------------------------------------------------------------------
Add any additional information you think we may need to validate this shim
-------------------------------------------------------------------------------
n/a

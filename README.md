gentoo_patches
==============

This is a repository of patches that I use for modifying Gentoo packages.
Usage of the patches in this repository make use of portage's epatch_user feature in ebuilds.

How to use these patches
------------------------

As root

    # git clone https://github.com/bencord0/gentoo_patches /etc/portage/patches


(optional) Modify ebuilds to accept user patches

Some ebuilds don't yet invoke epatch_user.
The easiest way to add this is to inherit from base.eclass 

--- a/app-misc/hello/hello-2.9.ebuild    2014-05-31 02:00:20.000000000 +0100
+++ b/app-misc/hello/hello-2.9.ebuild    2014-05-31 01:50:39.000000000 +0100
@@ -4,6 +4,8 @@
 
 EAPI="4"
 
+inherit base
+
 DESCRIPTION="GNU \"Hello, world\" application"
 HOMEPAGE="http://www.gnu.org/software/hello/"
 SRC_URI="mirror://gnu/${PN}/${P}.tar.gz"

    # ebuild /usr/portage/app-misc/hello/hello-2.9.ebuild digest 

Install packages as normal

    # emerge app-misc/hello

Use the modified package

    $ hello
    Goodbye, cruel world!

USB port mapping SSDTs for various motherboards. To be used in conjuction with USBInjectAll.kext.

By default, OS X restricts the maximum number of addressable USB ports to fifteen. RehabMan's USBInjectAll extension attempts to inject all potential ports for a given chipset and in doing so, exceeds this limit. Without further modification, the result would typically be that some of a user's ports are functional (those injected below the limit) but not others.

In order to solve this problem, most users will apply a kext patch which disables or raises OS X's port limit, such that all of the ports injected by RehabMan's extension are addressable. This certainly works but tends to be less than ideal, as the specific patch required to bypass the port limit tends to change both within and between point releases of OS X. It also results in many non-existent ports being injected, which may have a negative impact upon system stability and sleep functions.

The purpose of my SSDT is essentially to omit all but the externally accessible USB ports from RehabMan's USBInjectAll extension, leaving the total number of ports below the limit of fifteen. This eliminates the need for an ever-changing port limit patch, yielding more hassle-free update installations.

This is the main branch that builds upstream version without a patch to set startpage.
There are branches for Bodhi & AntiX on this repo also available thatuse custom startpage and to build them is the same, other than specifying the branch when cloning this repo.

The following should build and install the unsigned package on any debian based distro. 
Please report any issues.

```bash
# Install packaging tools etc
sudo apt install wget git devscripts equivs
# Get upstream source tarball, extract it, and enter dir:
cd /tmp # optional
wget https://distfiles.hacktivis.me/releases/badwolf/badwolf-1.4.0.tar.gz -O badwolf_1.4.0.orig.tar.gz  
tar xf badwolf_1.4.0.orig.tar.gz                                                                       
cd badwolf-1.4.0
# get the packaging files I made (debian folder):
git clone https://github.com/enigma9o7/badwolf-debian-packaging debian
# Install the build dependencies for this package I defined in control file:
sudo mk-build-deps --install --remove
# Build unsigned packages:
dpkg-buildpackage -us -uc                
# Install badwolf package you just built:                                        
sudo apt install ../badwolf_1.4.0-1_*.deb
# Optional: Remove all the packaging tools and build dependencies you no longer need
sudo apt remove badwolf-build-deps git devscripts equivs --autoremove
```

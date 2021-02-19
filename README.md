# Debianization of pypilot.
This repository contains procedures and scripts needed to make all the debian packages necessary to run pypilot. 

The used packaging tool here is **dh_make** and the packaging approach is **native debian package** ( even if it's a separate repository)

---

## Create a debian package for rtimulib2 library 
rtimulib2 is a wildly used and well established library. Pypilot have it's own flavour of it.It must not be confused or replaced with any other rtimulib lib.

### Download this repository 
```
git clone https://github.com/pypilot/pypilot-debian.git
cd pypilot-debian
```


### Get rtimulib2 source code 
```
wget https://github.com/seandepagnier/RTIMULib2/archive/master.zip
unzip master.zip
cp -r RTIMULib2-master/* rtimulib2/
rm -r master.zip RTIMULib2-master
```

### Build the Package
```
cd rtimulib2
dpkg-buildpackage -rfakeroot -b -uc -us  # To build a locale package 
debuild -S # To build a source package (Required to upload to lauchpad)
```


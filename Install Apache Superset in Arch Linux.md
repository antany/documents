# Install Apache Superset in Arch Linux

## Install Development dependenices
``` sudo pacman -S base-devel python python-pip python-wheel ```
Install all development packages, when prompted
Install Python 3.7, at this time of preparing this document, apache superset will work only python 3.7 or older version. If system has recent version of python, then python 3.7 has to be installed as well.

## Install python 3.7
..* Ignore this step, if apache supset fixed the issue with recent version of python 3.7

..* Download the source from https://www.python.org/downloads/source/

```shell 
wget https://www.python.org/ftp/python/3.7.10/Python-3.7.10.tar.xz 
tar -xvf Python-3.7.10.tar.xz 
mv Python-3.7.10 python37 
cd python37 
./configure --enable-optimizations --with-ensurepip=install 
make -j 8 
```

... make step will take quite some time



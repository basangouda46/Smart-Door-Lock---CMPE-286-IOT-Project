# Smart-Door-Lock---CMPE-286-IOT-Project

Step 1: Install dependancies

```
sudo apt install build-essential \
    cmake \
    gfortran \
    git \
    wget \
    curl \
    graphicsmagick \
    libgraphicsmagick1-dev \
    libatlas-base-dev \
    libavcodec-dev \
    libavformat-dev \
    libboost-all-dev \
    libgtk2.0-dev \
    libjpeg-dev \
    liblapack-dev \
    libswscale-dev \
    pkg-config \
    python3-dev \
    python3-numpy \
    python3-pip \
    zip
    python3-picamera
```

Step 2: Updates

```
sudo pip3 install --upgrade picamera[array]
```

Step 3: Increase the swap file size so we can build dlib

```
sudo nano /etc/dphys-swapfile
```

Find `CONF_SWAPSIZE` and change its value from 100 to 1024. Save
and exit then run this command:

```
sudo /etc/init.d/dphys-swapfile restart
```

Step 4: Build and install dlib

```
cd
git clone -b 'v19.6' --single-branch https://github.com/davisking/dlib.git
cd ./dlib
sudo python3 setup.py install --compiler-flags "-mfpu=neon"
```

This may take a significant time to run (Raspberry Pi 4 took about 30 minutes)

Step 5: Revert the swap size

```
sudo nano /etc/dphys-swapfile
```

Find `CONF_SWAPSIZE` and change its value from 1024 to 100. Save
and exit then run this command:

```
sudo /etc/init.d/dphys-swapfile restart
```

Step 6: Install `face_recognition` and examples

```
sudo pip3 install face_recognition
```

You're done!

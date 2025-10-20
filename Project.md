**A step-by-step breakdown of The Project**
---
## Pre-development Stage
### Install Dependencies (Ubuntu)
- Prepare **Environment** on HOST machine

```bash
sudo apt install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev python3-subunit mesa-common-dev zstd liblz4-tool file locales libacl1
sudo locale-gen en_US.UTF-8
```
### Download Poky
Poky is the reference build system for the Yocto Project. It performs cross-compiling using the BitBake tool, OpenEmbedded Core, and a default set of metadata.
```bash
# clone poky.
git clone -b kirkstone https://github.com/yoctoproject/poky.git
cd poky
```

### Initialize the Build Environment
Run inside `poky`:
```bash
source oe-init-build-env
```
This creates the `build` directory and sets up environment variables.

### BitBake Configurations
1. **`build/conf/bblayers.conf`** → Specifies the layers included in the build, ex :`meta-openembedded`.
2. **`build/conf/local.conf`** → Contains user-specific settings (e.g., `MACHINE`, `DISTRO`).
3. **`meta/conf/layer.conf`** → Defines how BitBake processes each layer, including priorities and dependencies.

### BitBake Custom Layers 
   [meta-distros(audio, ivi), meta-ivi]
- **`meta-distros`** → 2 distribution configurations (Distro 1 : Infotainment, Distro 2 : Audio).
- **`meta-IVI`** → Contains an image recipe with a C++ application and Nano editor.

### Integrate BSP Layer for Raspberry Pi
1- go to (https://layers.openembedded.org/layerindex/branch/kirkstone/layers/)
2- search for raspberrypi, and select (meta-raspberrypi) layer
![meta-raspberrypi](Images/meta-raspberrypi.png)
3- clone meta-raspberrypi from here :
```bash
git clone -b kirkstone git://git.yoctoproject.org/meta-raspberrypi
```
![meta-raspberrypi-git](Images/meta-raspberrypi-git.png)
4- add the layer to the bblayers.conf
```bash
bitbake-layers add-layer ../meta-raspberrypi
```
5- clone the openembedded-core
```bash
git clone -b kirkstone git://git.openembedded.org/openembedded-core
```
### Integrate Qt-5
1- go to  (https://layers.openembedded.org/layerindex/branch/kirkstone/layers/)
2- search for Qt, and select (meta-qt5) layer
![meta-qt5](Images/meta-qt5.png.png)
3- clone meta-qt5 from here :
```bash
git clone -b kirkstone https://github.com/meta-qt5/meta-qt5.git
```
4- add the layer to the bblayers.conf
```bash
bitbake-layers add-layer ../meta-qt5
```
---
## Create Distribution Layer (meta-distros)
### **Create Infotainment Distro**
### Enable Systemd for Infotainment Distribution

### **Create Audio Distro**

---
## Create SW Layer (meta-IVI)

---
## Create Cpp Package Recipe `helloworld`

---
## Integrate Nano

---
## Integrate Audio

---
## Create the Image Recipe: ivi-test-image.bb

### Inheritance 

### Package Installation 

### Image Features 
### Machine Features 
---
## Building an Image
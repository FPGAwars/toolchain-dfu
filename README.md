# toolchain-dfu
Apio package that contains the [dfu-util](http://dfu-util.sourceforge.net/) utility for programming the [Fomu board](https://github.com/im-tomu/fomu-hardware)

Instead of compiling the dfu-util from scratch, the scripts just download the already compiled files from the amazing [fpga-toolchain](https://github.com/open-tool-forge/fpga-toolchain) project and create the apio packages

## How to create a new release

This information is for **developers**

* Clone the toolchain-dfu
* Open the **build.sh** file
* Change the **VERSION** variable to the new version for the Apio package (For example VERSION=2020.10.6)

```bash
# -- dfu apio package version
VERSION=2020.11.24
```

* Set the **dfu version** to include in the apio package

```
# -- fpga-toolchain version to download
# -- nightly-20201124
SRC_VER="nightly-20201124"
```

* **Save** the file
* **Execute** the building script for all the **architectures** you want to create

It will download the executables from the [fpga-toolchain](https://github.com/open-tool-forge/fpga-toolchain) project and package them for apio

The **apio target architectures** are:

 * linux_x86_64: For linux 64-bits
 * windows_amd64: for windows 64-bits
 * windows_x86: for windows 32-bits
 * darwin: For Mac

Example: Building the package for Linux

```bash
bash build linux_x86_64
```

* The **apio packages** are stored in the local **releases** folder  
* Create the **new release of toolchain-dfu** in Github  
The tag and name of the release should start with the **letter v** and have three numbers separated by a colon. Ex: v2020.10.6  
* **Upload the apio packages** from the releases local folder  
* Apio should **upgrade** to the new version with the **install command**:
```
apio install dfu
```
* You can check that the new version is installed with:
```
apio install -l
```

## Authors

* [Carlos Venegas](https://github.com/cavearr)
* [Juan González (Obijuan)](https://github.com/Obijuan)

## Credits

* The [dfu-util](http://dfu-util.sourceforge.net/) has been developed by Harald Welte and Tormod Volden
* The [fpga-toolchain](https://github.com/open-tool-forge/fpga-toolchain) project has been developed by Edward Bordin

* The building scripts are based on the [Tools-systems](https://github.com/FPGAwars/tools-system) by
  * [Jesús Arroyo Torrens](https://github.com/Jesus89)
  * [Juan González-Gómez (Obijuan)](https://github.com/Obijuan)

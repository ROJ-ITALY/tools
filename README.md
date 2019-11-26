# Steps to prepare the HOST PC and configure Yocto for SMARC + eNUC (ROJ Demokit)
1) Download Ubuntu 16.04
2) Download VirtualBox and setup Virtual Machine (VM), if you don't have a native linux host machine
3) Install Ubuntu 16.04
4) Check that your linux host machine is connected to internet (mandatory)
5) Install git
    ```sh
    $ sudo apt-get install git
    ```
6) Clone tools repo
    ```sh
    $ git clone https://github.com/ROJ-ITALY/tools.git -b thud (*1)
    ```
7) Change dir to tools and run these scripts in this specific order
    ```sh
    $ cd tools
    $ ./download_packages
    $ ./create-yocto-environment
    ```
8) Configure Yocto for ROJ demokit:
    Only the first time:
    ```sh
    $ cd $HOME/yocto-enuc-thud
    $ source ./fsl-setup-release.sh -b build
    ```
    Then all other times just enter:
    ```sh
    $ cd $HOME/yocto-enuc-thud
    $ source ./setup-environment build
    ```
9) Building steps accordingly on your smarc module :

- SMARC based on i.MX6 Quad/Dual (RAM 1GB) i.e.
   ```sh
    $ bitbake --read=conf/imx6qenuc_1gb.conf u-boot-imx
    ```

- SMARC based on i.MX6 Quad (RAM 2GB) i.e.
   ```sh
	$ bitbake --read=conf/imx6qenuc_2gb.conf u-boot-imx
    ```

- SMARC based on i.MX6 solo (RAM 512MB) i.e.
   ```sh
	$ bitbake --read=conf/imx6soloenuc_512mb.conf u-boot-imx
    ```

- SMARC based on i.MX6 solo (RAM 1GB) i.e.
   ```sh
	$ bitbake --read=conf/imx6soloenuc_1gb.conf u-boot-imx
    ```

---------------------	
# Note:
(*1) Tools dir contains some useful shell scripts in order to prepare the Host system to use Yocto Project.	

---------------------
(c) 2019 Stefano Gurrieri and Paola Martiner

ROJ s.r.l. - Via Vercellone 11
13900 Biella - Italy
www.roj.com


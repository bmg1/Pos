# This Idiot Repo :)) Use It.<br/>
It's very Hard to Remember how to compile Fucking Pos Driver for Raspberry Pi. So i write all steps here for you. maybe when you want to install it the version of Rasbian changed! don't worry update your raspberry and enjoy!<br/>
<br/>

### A. Update your raspberry:
1. sudo apt-get update
2. sudo apt-get dist-upgrade
3. uname -a
[ 5.15.61-v7l+ ]

I attached C files of the driver so clone them:<br/>

### B. Clone Repository
1. git clone https://github.com/bmg1/myPOS-Linux
2. Extract Linux Driver_ttyPos V314.zip
3. cd ttyPos_V314_20170802
4. make

you see this Error:
make[1]: *** /lib/modules/5.15.61-v7l+/build: No such file or directory.  Stop.
Makefile:9: recipe for target 'all' failed
make: *** [all] Error 2
Don't worry you read these to solve these fucking problem.

### C. Clone linux raspberry and Hard link it 
1. cd /usr/src
2. git clone --depth 1 https://github.com/raspberrypi/linux.git<br/>
3. ln -s linux 5.15.61-v7l+
4. ln -s /usr/src/linux /lib/modules/5.15.61-v7l+/build

Now Go to C files and Make adn install them.
### D. Make Drive and Install
1. Cd ttyPos_V314_20170802
2. sudo make
3. sudo make install

If need ".config"
### D.1 Make .config, menuconfig tools
1. apt install flex 
2. apt install bison
3. apt-get install libssl-dev
4. cd /usr/src/linux
5. make menuconfig
* #[save]
* #[exit]



### E. Check module insertet or Not:
1. lsmod
2. try to find ttPos :)

if it's not inserted insert it manually:
### F. Insert kernel module
1. cd /lib/modules/5.15.61-v7l+/ttPos
2. insmod ttyPos.ko
3. and Check E2 again.

Good Luck

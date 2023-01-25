# Package for wireless/wire connection with the A1
### Initially it was 
- capable to work with both aliango,A1;
- working with different vesion of sdk such as 3_1,3_2
### now
- only 3_2 V
- only A1
### dependesies
- [LCM][LCM_link]
### usage 
#### prepare the network
- push button twice and hold for 5 sec.
- dog should up
- switch on the wifi(or wired connection) (`UnerteeRoboticsA1-XXX` password `00000000` - for wifi)
#### follow the connection guid (one of them):
#### 1) doesn't work for me
- run `ifconfig`
- find your network name (just turn off the connection and you will see disapered target name)
- Then, open the `ipconfig.sh` file under the folder `unitree_legged_real`
- change `wlp3s0` your network name
- run `sudo chmod +x ipconfig.sh`
- run `sudo ipconfig.sh`
#### 2) this works for me:
- set adress and mask  
`wifi_settings -> settings -> IPv4 -> manual`  
 set IP adress:192.168.123.162 mask:255.255.255.0
- run  
`sudo ifconfig lo multicast`  
`sudo route add -net 224.0.0.0 netmask 240.0.0.0 dev lo`
#### 3) works but with drawback - crush option to connect to other networks
- run `ifconfig`
- find your network name (just turn off the connection and you will see disapered target name)
- `sudo gedit /etc/network/interfaces`
- And add the following 4 lines at the end:
`auto enx000ec6612921`  
`iface enx000ec6612921 inet static`  
`address 192.168.123.162`  
`netmask 255.255.255.0`  
Where the port name(enx000ec6612921) have to be changed to your own.

#### test
- run server and example  
`roslaunch unitree_legged_real real.launch ctrl_level:=lowlevel`  
`rosrun unitree_legged_real position_lcm`  
### errors:
-   `error while loading shared libraries: liblcm.so.1: cannot open shared object file: No such file or directory`  
    * error while runing `rosrun unitree_legged_real position_lcm`
    * [solution][err1_solution] `$ sudo ldconfig -v`






[LCM_link]:https://lcm-proj.github.io/build_instructions.html
[err1_solution]:https://github.com/CogChameleon/ChromaTag/issues/2
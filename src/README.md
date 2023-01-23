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
- run `rosrun unitree_legged_real position_lcm`
### errors:
-  * run `rosrun unitree_legged_real position_lcm`
    * error `error while loading shared libraries: liblcm.so.1: cannot open shared object file: No such file or directory`
    * [solution][err1_solution] `$ sudo ldconfig -v`






[LCM_link]:https://lcm-proj.github.io/build_instructions.html
[err1_solution]:https://github.com/CogChameleon/ChromaTag/issues/2
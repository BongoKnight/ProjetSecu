Analyse des versions


Version 1 du protocole :
```apache
session engagée : 	session(b,s,pkb,pks,idemploye, idbadgeuse) /\ session(b,i,pkb,pki,idemploye, idbadgeuse)
```
```apache
SUMMARY
  UNSAFE

DETAILS
  TYPED MODEL

PROTOCOL
  calp-v1.if

GOAL
  Secrecy goal () on idemploye)

BACKEND
  CL-AtSe

STATISTICS
  Analysed   : 6 states
  Reachable  : 3 states
  Translation: 0.00 seconds 
  Computation: 0.00 seconds 

ATTACK TRACE
 i -> (b,3):  start
 (b,3) -> i:  {idemploye.idbadgeuse}_pks
              & Secret(idemploye,(),set_52);  Add b to set_52;  Add s to set_52;
              & Built from step_0

 i -> (b,6):  start
 (b,6) -> i:  {idemploye.idbadgeuse}_pki
              & Secret(idemploye,(),set_59);  Add b to set_59;  Add i to set_59;
              & Built from step_0


```
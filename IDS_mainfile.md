
_________________
Master Container 
_________________

1) linux - IDS
a) IDS - TCPDump
        suricaata 
        snort 
b) NAT + internal adapter  
    Internet access + access to two other container              [ubuntu(client), Kali Linux(attacker)]

________________________
Ubuntu Client Container 
________________________

1) Ubuntu Client => user with basic use like internet access through the IDS-Container
a) Toola :- Ping, net-tools , git , weget or curl maybe 

________________________________
kali linux(attacker ) Container 
________________________________

1) Kali linux => using differenet attack modes with custom scripts to ubuntu container 
a) Connection to the internet and Ubuntu container will be through the IDS container 
     
     
Scenario 
Implementation of IDS with multiple integration and system monitoring tools, we have ubuntu based machine acting as a IDS System with the internet access as a gateway to other containers to have a communication through the IDS system. Client system will be a ubuntu machine for accessing internet and IDS implementation testings. And as we all know we will be using a Kali linux/ Parrot os machine as a attacker machine that plays the role of the attacker. End of the day the attacker machine is used for the testing purpose. 

Note:
All the communications between each system and the internet will be done through the IDS only 

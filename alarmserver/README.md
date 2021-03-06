Pre-requisites
--------------
 - Python "requests" module is needed for Alarmserver python script.
 
     sudo apt-get install python-pip
     
     pip install requests

Service Installation
--------------------
1. Upload your alarmserver scripts at ~/alarmserver

2. Set permission and copy to /usr/lib/alarmserver

    (a) chmod ug+x ~/alarmserver/*.py
   
    (b) if this is a fresh installation: 
            
            mv ~/alarmserver/alarmserver.cfg.original ~/alarmserver/alarmserver.cfg
    
     (c) sudo cp -R ~/alarmserver /usr/lib/
    
     

2. Create a hard-link at /usr/lib/systemd/system/alarmserver.service

     ln /usr/lib/alarmserver/alarmserver.service /usr/lib/systemd/system/alarmserver.service
 
  NOTE: symbolic link doesn't work with systemd.
  

3. Run the following commands

     sudo systemctl enable alarmserver.service
     
     sudo systemctl start alarmserver.service


Monitoring
----------
To see status of alarmserver service, run the following command:

    systemctl status alarmserver.service
    

To see past log of alarmserver:

    journalctl -u alarmserver -x
    

To see current alarmserver logs as they are written:

    journalctl -u alarmserver -xf
    

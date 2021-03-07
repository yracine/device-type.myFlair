# device-type.flairDevices Hubitat-Flair integration

My Flair Devices 

Author:             Yves Racine

linkedIn profile:   www.linkedin.com/in/yracine


You can now download the code at 

<b>
http://www.ecomatiqhomes.com/hubitatstore 
</b>

P.S. Technical support packages are also available.
**************************************************************************************************


Setup time: about 10-20 minutes depending on your ST skills.


PREREQUISITES
==============

- a) Puck gateway operational & connected to Flair via the internet.

- b) Flair device (vent or hvac unit) operational & connected to Flair via the Puck gateway

- c) Flair Setup completed: basic information about your home & rooms entered via the Flair Mobile App or the Flair portal- Developer access to SmartThings (http://graph.api.smartthings.com/)

- d) Your Hubitat hub is operational

INSTALLATION STEPS
=====================


# 1) Depending on your contribution, create one or multiple Device Driver(s) -  for My Flair Vent, My Puck Device, My Flair HVAC Unit, My Flair Tstat

For each device (My Flair Vent, My Puck Device, My Flair Tstat, My Flair Hvac Unit),


For each device (My NextTstatV2, My NextAlarmV2, My NextSensorV2),

a) Create a new device driver 

go to http://192.168.xx.xx/driver/list (insert your own hub's IP address)

b) Hit the "+New Driver" at the top right corner

c) Copy and paste the code from the corresponding txt file in the zip 

d) Hit the save button on the right inside of the screen


# 2) Create a new smartapp (MyFlairServiceMgr)

go to http://192.168.xx.xx/app/list (insert your own hub's IP address)

a) Hit the "+New App" at the top right corner

b) Copy and paste the code from the corresponding txt file in the zip 

c) Hit the save button on the right inside of the screen

d) Make sure that enable OAuth in Smartapp is active (click oAuth in the upper right corner)
* Hit "Update" at the bottom

If the instructions above are not clear enough, you can refer to the troubleshooting section below with some pictures:

https://thingsthataresmart.wiki/index.php?title=MyFlairServiceMgr#Issue_.231:_I_don.27t_know_how_to_create_a_custom_smartapp


# 3) Go to the installed apps section of hubitat, execute MyFlairServiceMgr 

http://192.168.xx.xx/installedapp/list (insert your own hub's IP address)

a) Click on "Add User app" in the right corner of the window

# 4) Connect Hubitat to the Flair APIs

[Hubitat IDE] <b> Check the logs for any installation errors.  

http://192.168.xx.xx/logs (insert your own hub's IP address)
    

    
*************************************************************************************************************************************
N.B. If you have any errors:

If you get a blank screen after pressing 'Next or you get the following error: "'Java.lang.NullPointerException: Cannot get property 'accessToken' on null object" in the IDE', you'd need to enable oAuth as specified in step 2f) above.

<b> At the end of the authorization flow,  if you have the following error message: "Unexpected error" even if you press several times, this probably means that you have not "saved" one of the Device Handler Types (MyNextTstatV2,MyNextAlarmV2,MyNextSensorV2) under the right shard.  Refer to the prerequisites & step 1 for more details.
  
*************************************************************************************************************************************


If the instructions above are not clear enough, you can refer to the troubleshooting section below with some pictures:

http://thingsthataresmart.wiki/index.php?title=MyFlairServiceMgr#Issue_.231:_I_don.27t_know_how_to_create_a_custom_smartapp



After being connected, click 'Next' and select your location, your Flair Devices -Puck(s), Vents(s), Tstat(s), and HVAC Unit(s)-
that you want to control from Smartthings and, then press 'Next' for the 'Other Settings &Notification' page, 
and then 'Done' or 'Save' when finished.

*************************************************************************************************************************************
N.B. If you have any errors:

If you get a blank screen after pressing 'Next or you get the following error: "Error -'Java.lang.NullPointerException: Cannot get property 'accessToken' on null object" in the IDE', you'd need to enable oAuth as specified in step 2f) above.


 
*************************************************************************************************************************************



# 5) Your device(s) should now be ready to process your commands

After about 1 minute, You should see your newly Flair devices instantiated under:

[Hubitat IDE]  http://192.168.xx.xx/device/list (insert your own hub's IP address)

And also

# 6) (Optional) Set device's preferences 


a) Go to https://graph.api.smartthings.com/device/list   (or whatever your shard is and click on My Devices in the IDE's top menu)

a) Click on the flair device(s) that you just created

http://192.168.xx.xx/device/edit/"device number" (Device number can vary from one location to the next)

b) Edit the preferences in the middle section of the screen) 

You only need to edit the following parameters

    (a) <trace> when needed, set to true to get more tracing (no spaces)
    (b) <logFilter:1..5> Values=[Level 1=ERROR only,2=<Level 1+WARNING>,3=<2+INFO>,4=<3+DEBUG>,5=<4+TRACE>]
    
And, press "save preferences" at the end.

N.B. The detailed logging will be set for the next 15 minutes only (deactivated after to avoid performance issues)
        
    For My Puck Device, you can also change the offset values for the temperature and humidity UI fields.
    
    (c) humOffset - Humidity offset (+/-)
    (d) tempOffset - Temperature offset (+/-)

    P.S. Don't enter any values for the appKey, privateKey and any serial Id numbers as the values are populated by the
    Service Manager by default during the authentification flow.


# 8) Use some of the Zoned Heating/Cooling Smartapps available (optional)

The following zoned Heating/cooling smartapps have many safeguards built-in to protect your HVAC.

- The smartapps can check the static HVAC pressure using your Puck and Flair vent devices by comparing the room's pressure and the associated vent's pressure located in the same room.
- The smartapps will check the vent's internal temperature to make sure it's not too hot or too cold
- The smartapps will not close more than 50% of the smart vents inputted in the smartapp
- You can define some minimum open threshold (by default 10% in zone, 20% outside the zone) to avoid closing the vents too tight.



<b>
http://www.ecomatiqhomes.com/store 
</b>


/****************************************************

<b>a) ScheduleTstatZones</b>

/****************************************************

For more details:

http://thingsthataresmart.wiki/index.php?title=ScheduleTstatZones

The smartapp that enables Multi Zoned Heating/Cooling Solutions based on any connected thermostats/sensors- - coupled with smart vents (optional, can be any Flair, Keen Home, EcoVent, EcoNet smart vents) for better temp settings control throughout your home". 

The smartapp can reproduce the  Flair eveness and eveness active modes based on the thermostat's setpoints.  

The smartapp can also control multiple Minisplit/Windows unit and portable heaters/coolers inside your scheduled zones (based on the Flair HVACUnit device, see http://thingsthataresmart.wiki/index.php?title=My_Flair_HVac_Unit).




/****************************************************

<b>b) ecobeeSetZoneWithSchedule</b>

/****************************************************

For more details:

http://thingsthataresmart.wiki/index.php?title=EcobeeSetZoneWithSchedule


The smartapp that enables Multi Zoned Heating/Cooling Solutions based on your ecobee thermostats (using comfort settings) and any connected sensors- coupled with smart vents (optional, can be any Flair, Keen Home, EcoVent, EcoNet smart vents) for better temp settings control throughout your home". 

The smartapp can reproduce the Flair eveness and eveness active setpoint modes based on the thermostat's climate settings.  

The smartapp can also control multiple Minisplit/Windows unit and portable heaters/coolers inside your scheduled zones (based on the Flair HVACUnit device, see http://thingsthataresmart.wiki/index.php?title=My_Flair_HVac_Unit )




/****************************************************

<b>c) ScheduleRoomTempControl</b>

/****************************************************

For more details:

http://thingsthataresmart.wiki/index.php?title=ScheduleRoomTempControl

The smartapp that enables Multi Zoned Heating/Cooling Solutions based on your Flair devices and any connected thermostats/sensors. 

The smartapp can reproduce the Flair DeferToRooms' setpoint mode using or not your thermostat (optional).  You can also choose or not to set your thermostat's setpoints in the smartapp.




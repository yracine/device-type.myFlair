# device-type.flairDevices Flair-SmartThings integration

My Flair Devices 

Author:             Yves Racine

linkedIn profile:   www.linkedin.com/in/yracine

Date:               2017-04-25


You can now download the code at 

<b>
http://www.ecomatiqhomes.com/store 
</b>

P.S. Technical support packages are also available.
**************************************************************************************************


Setup time: about 10-20 minutes depending on your ST skills.


PREREQUISITES
=====================

- Your Flair devices fully operational (and connected to wifi)
- Your Flair credentials (username/password)
- Developer access to SmartThings (http://graph.api.smartthings.com/)
-  <b>Location set for your ST account  </b>

Under the ST mobile app, click on the 3-horizontal lines- "hamburger"- menu in the upper left corner, and then the "gear'" icon to review your location and save it.

-  <b>Determine your shard, please consult this thread: </b>


https://community.smartthings.com/t/faq-how-to-find-out-what-shard-cloud-slice-ide-url-your-account-location-is-on/53923

Or the SmartThings documentation here:

http://docs.smartthings.com/en/latest/publishing/index.html#ensure-proper-location

<b> If you are on a different shard, you need to change the links below for your right shard. 
As an example, in North America, </b>

replace https://graph.api.smartthings.com/ide/devices by https://graph-na02-useast1.api.smartthings.com


Or use  https://consigliere-regional.api.smartthings.com/ to point to the right shard.

INSTALLATION STEPS
=====================


# 1) Depending on your contribution, create one or multiple Device Handler Type(s) - DTH for My Flair Vent, My Puck Device, My Flair HVAC Unit, My Flair Tstat

For each device (My Flair Vent, My Puck Device, My Flair Tstat, My Flair Hvac Unit),

a) Go to https://graph.api.smartthings.com/ide/devices

b) Hit the "+New Device Handler" at the top right corner

c) Hit the "From Code" tab on the left corner

d) Copy and paste the code from the corresponding txt file

<b>The code will be sent to you via your paypal verified email address.</b>

e) Hit the create button at the bottom

f) Hit the "publish/for me" button at the top right corner (in the code window)


# 2) Create a new smartapp (MyFlairServiceMgr)

a) Go to https://graph.api.smartthings.com/ide/apps

b) Hit the "+New SmartApp" at the top right corner

c) Hit the "From Code" tab on the left corner

d) Copy and paste the code  

<b>The code will be sent to you via your paypal verified email address.</b>

e) Hit the create button at the bottom

f) <b>Make sure that "enable OAuth" in Smartapp is active </b>

* Goto app settings (top right corner, click on it)
* Click on Oauth (middle of the page), and enable OAuth in Smart app
* Hit "Update" at the bottom

g) Go back to the code window, and hit the "publish/for me" button at the top right corner 


# 3) Under the ST mobile app, execute MyFlairServiceMgr

<b>Click on the Smartapps link in the upper section of the following Marketspace screen (last icon in the bottom menu), and then Smartapps/MyApps (last item in the list).</b>


# 4) Connect Smartthings to the Flair Portal

You should already have an Flair username and password, if not go to https://my.flair.co/

Go through the authentication process using MyFlairServiceMgr smartapp.

After being connected, click 'Next' and select your location, your Flair Devices -Puck(s), Vents(s), Tstat(s), and HVAC Unit(s)-
that you want to control from Smartthings and, then press 'Next' for the 'Other Settings &Notification' page, 
and then 'Done' when finished.

<b>If you get a blank screen after pressing 'Next or you get the following error: " Error - bad state. Unable to complete page configuration", you'd need to enable oAuth as specified in step 2f) above. </b>




# 5) Your device(s) should now be ready to process your commands

After about 1 minute, You should see your newly Flair devices instantiated under:

a) https://graph.api.smartthings.com/device/list

And also

b) Under the ST mobile app, under MyHome/Things (main menu at the bottom of the screen).


# 6) To populate the UI fields for your newly created device(s), press the "refresh" tile </b>

You may have to hit your Flair device's 'refresh' button several times as the smartThings app is not always responsive. 


# 7) (Optional) Set device's preferences 


a) Go to https://graph.api.smartthings.com/device/list

b) Click on the Flair Devices that you just created

c) Click on Preferences (edit)

N.B. You can also edit the preferences under Things/Your Flair Device/Edit Device using the ST mobile app.

You only need to edit the following parameters


    (a) <trace> when needed, set to true to get more tracing (no spaces)
    (b) <logFilter:1..5> Values=[Level 1=ERROR only,2=<Level 1+WARNING>,3=<2+INFO>,4=<3+DEBUG>,5=<4+TRACE>]
    
    
    For My Puck Device, you can also change the offset values for the temperature and humidity UI fields.
    
    (c) humOffset - Humidity offset (+/-)
    (d) tempOffset - Temperature offset (+/-)

    P.S. Don't enter any values for the appKey, privateKey and any serial Id numbers as the values are populated by the
    Service Manager by default during the authentification flow.


# 8) Use some of the Zoned Heating/Cooling Smartapps available (optional)

<b>
http://www.ecomatiqhomes.com/store 
</b>

Amongst others:


/****************************************************

<b>a) ScheduleTstatZones</b>

/****************************************************


The smartapp that enables Multi Zoned Heating/Cooling Solutions based on any ST connected thermostats/sensors- - coupled with smart vents (optional) for better temp settings control throughout your home". 

The smartapp can reproduce the eveness and eveness active Flair modes based on the thermostat's setpoints.  

The smartapp can also control multiple Minisplit/Windows unit and portable heaters/coolers inside your scheduled zones.


For more details:

http://thingsthataresmart.wiki/index.php?title=ScheduleTstatZones

/****************************************************

<b>b) ecobeeSetZoneWithSchedule</b>

/****************************************************

The smartapp that enables Multi Zoned Heating/Cooling Solutions based on your ecobee thermostats (using comfort settings) and any ST connected sensors- coupled with smart vents (optional) for better temp settings control throughout your home". 

The smartapp can reproduce the Flair eveness and eveness active Flair setpoint modes based on the thermostat's climate settings.  

The smartapp can also control multiple Minisplit/Windows unit and portable heaters/coolers inside your scheduled zones.


For more details:

http://thingsthataresmart.wiki/index.php?title=EcobeeSetZoneWithSchedule


/****************************************************

<b>c) ScheduleRoomTempControl</b>

/****************************************************

The smartapp that enables Multi Zoned Heating/Cooling Solutions based on your Flair devices and any ST connected thermostats/sensors- coupled with smart vents (optional) for better temp settings control throughout your home". 

The smartapp can reproduce the Flair DeferToRooms' setpoint mode using or not your ST thermostat (optional).  You can also choose or not to set your thermostat's setpoints in the smartapp.


For more details:

http://thingsthataresmart.wiki/index.php?title=ScheduleRoomTempControl

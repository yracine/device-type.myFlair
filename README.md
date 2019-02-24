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
==============

- a) Puck gateway operational & connected to Flair via the internet.

- b) Flair device (vent or hvac unit) operational & connected to Flair via the Puck gateway

- c) Flair Setup completed: basic information about your home & rooms entered via the Flair Mobile App or the Flair portal- Developer access to SmartThings (http://graph.api.smartthings.com/)


- (d) <b>Location set for your ST account under the ST classic mobile app  </b>

Under the ST classic mobile app, click on the 3-horizontal lines- "hamburger"- menu in the upper left corner, and then the "gear'" icon to review your location and save it.

- (e) <b>Determine your shard, please consult this thread: </b>


https://community.smartthings.com/t/faq-how-to-find-out-what-shard-cloud-slice-ide-url-your-account-location-is-on/53923

Or the SmartThings documentation here fore more details:

http://docs.smartthings.com/en/latest/publishing/index.html#ensure-proper-location

<b> If you are on a different shard, you need to change the links below for your right shard. 
As an example, in North America, </b>

replace https://graph.api.smartthings.com/ide/devices by https://graph-na02-useast1.api.smartthings.com


Or use  https://consigliere-regional.api.smartthings.com/ to point to the right shard.

INSTALLATION STEPS
=====================


# 1) Depending on your contribution, create one or multiple Device Handler Type(s) - DTH for My Flair Vent, My Puck Device, My Flair HVAC Unit, My Flair Tstat

For each device (My Flair Vent, My Puck Device, My Flair Tstat, My Flair Hvac Unit),

a) Go to https://graph.api.smartthings.com/ide/devices    (or whatever your shard is and click on My Device Handlers in the IDE's top menu)

b) Hit the "+New Device Handler" at the top right corner

c) Hit the "From Code" tab on the left corner

d) Copy and paste the code from the corresponding txt file in the zip

<b>The code has been sent to you via your paypal verified email address.</b>

e) Hit the create button at the bottom

f) Hit the "publish/for me" button at the top right corner (in the code window)


# 2) Create a new smartapp (MyFlairServiceMgr)

a) Go to https://graph.api.smartthings.com/ide/apps    (or whatever your shard is and click on My Smartapps in the IDE's top menu)

b) Hit the "+New SmartApp" at the top right corner

c) Hit the "From Code" tab on the left corner

d) Copy and paste the code from the corresponding txt file in the zip

<b>The code has been sent to you via your paypal verified email address.</b>

e) Hit the create button at the bottom

f) <b>Make sure that "enable OAuth" in Smartapp is active </b>

* Goto app settings (top right corner, click on it)
* Click on Oauth (middle of the page), and enable OAuth in Smart app
* Hit "Update" at the bottom

g) Go back to the code window, and hit the "publish/for me" button at the top right corner 


If the instructions above are not clear enough, you can refer to the troubleshooting section below with some pictures:

http://thingsthataresmart.wiki/index.php?title=MyFlairServiceMgr#Issue_.231:_I_don.27t_know_how_to_create_a_custom_smartapp



# 3) Under the ST classic mobile app, execute MyFlairServiceMgr (MarketSpace>Smartapps>MyApps)

<b>Click on the Smartapps link in the upper section of the following Marketspace screen (last icon in the bottom menu), and then Smartapps/MyApps (last item in the list).</b>


# 4) Connect SmartThings to the Flair Portal

You should already have a Flair username and password, if not go to https://my.flair.co/

Go through the authentication process using MyFlairServiceMgr smartapp.  To do so, please press on the "Flair Connect> Required" button in the middle of the screen.


After being connected, click 'Next' and select your location, your Flair Devices -Puck(s), Vents(s), Tstat(s), and HVAC Unit(s)-
that you want to control from Smartthings and, then press 'Next' for the 'Other Settings &Notification' page, 
and then 'Done' when finished.

If you get a blank screen after pressing 'Next or you get the following error: " Error - bad state' or 'Java.lang.NullPointerException: Cannot get property 'accessToken' on null object" in the IDE', <b>you'd need to enable oAuth as specified in step 2f) above.</b>

At the end of the authorization flow, you may have to press "Save" several times if you have have the following error message: "Error processing your request - please try again" or "Unexcepted error".  This is due to some ST platform timeouts due to rate limiting.


# 5) Your device(s) should now be ready to process your commands

After about 1 minute, You should see your newly Flair devices instantiated under:

a) https://graph.api.smartthings.com/device/list   (or whatever your shard is and click on My Devices in the IDE's top menu)

And also

b) Under the ST mobile app, under MyHome/Things (main menu at the bottom of the screen).


# 6) To populate the UI fields for your newly created device(s), press the "refresh" tile </b>

You may have to hit your Flair device's 'refresh' button several times as the smartThings app is not always responsive. 


# 7) (Optional) Set device's preferences 


a) Go to https://graph.api.smartthings.com/device/list   (or whatever your shard is and click on My Devices in the IDE's top menu)

b) Click on the Flair Devices that you just created

c) Click on Preferences (edit)

N.B. You can also edit the preferences under Things/Your Flair Device/Edit Device using the ST classic mobile app.

You only need to edit the following parameters


    (a) <trace> when needed, set to true to get more tracing (no spaces)
    (b) <logFilter:1..5> Values=[Level 1=ERROR only,2=<Level 1+WARNING>,3=<2+INFO>,4=<3+DEBUG>,5=<4+TRACE>]
    
    
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

The smartapp that enables Multi Zoned Heating/Cooling Solutions based on any ST connected thermostats/sensors- - coupled with smart vents (optional, can be any Flair, Keen Home, EcoVent, EcoNet smart vents) for better temp settings control throughout your home". 

The smartapp can reproduce the  Flair eveness and eveness active modes based on the thermostat's setpoints.  

The smartapp can also control multiple Minisplit/Windows unit and portable heaters/coolers inside your scheduled zones (based on the Flair HVACUnit device, see http://thingsthataresmart.wiki/index.php?title=My_Flair_HVac_Unit).




/****************************************************

<b>b) ecobeeSetZoneWithSchedule</b>

/****************************************************

For more details:

http://thingsthataresmart.wiki/index.php?title=EcobeeSetZoneWithSchedule


The smartapp that enables Multi Zoned Heating/Cooling Solutions based on your ecobee thermostats (using comfort settings) and any ST connected sensors- coupled with smart vents (optional, can be any Flair, Keen Home, EcoVent, EcoNet smart vents) for better temp settings control throughout your home". 

The smartapp can reproduce the Flair eveness and eveness active setpoint modes based on the thermostat's climate settings.  

The smartapp can also control multiple Minisplit/Windows unit and portable heaters/coolers inside your scheduled zones (based on the Flair HVACUnit device, see http://thingsthataresmart.wiki/index.php?title=My_Flair_HVac_Unit )




/****************************************************

<b>c) ScheduleRoomTempControl</b>

/****************************************************

For more details:

http://thingsthataresmart.wiki/index.php?title=ScheduleRoomTempControl

The smartapp that enables Multi Zoned Heating/Cooling Solutions based on your Flair devices and any ST connected thermostats/sensors. 

The smartapp can reproduce the Flair DeferToRooms' setpoint mode using or not your ST thermostat (optional).  You can also choose or not to set your thermostat's setpoints in the smartapp.




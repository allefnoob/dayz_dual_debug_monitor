![logo](http://i45.tinypic.com/30rp5qx.jpg)<br /><br />


##NOTICE:

Due to the number of requests I get asking for support on things I've clearly explained in this document
and because of people sending me their entire mission files expecting me to just do it all for them!
I'm now charging £35 for any and all requests to help you install this script.  That is already half my
standard hourly rate that I charge other clients, so I consider this a reasonable fee to ask for.

I've realised that by doing stuff for free people simply take advantage, so now I must charge for my time! 


##DayZ Dual Debug Monitor (V1.2)
=============================

The DayZ Dual Debug Monitor (remember you saw it here first) gives admins a special extended debug monitor while giving normal players 
the regular version (non-admin), It is kept up to date by Nomadic Hayward (aka UrbanSkaters).  When a regular
NON-admin user logs in they will see the debug monitor on the left (see screenshot above) and when an Admin
logs in (assuming you've put their UID in the list as explained below), they will see the extended debug monitor.

* V1.1
* V1.2 <br/> 
Change log for V1.2<br/>
[ADDED] ON/OFF function for Trigger version, simply press the hotkey to turn it on and off respectively.  
[DISCONTINUED] I will no longer be supporting or updating the Always on Version.  
* V1.2.01<br/>
Change log for V1.2.01<br/>
[BugFix] Changed (getPlayerUID vehicle player) to (getPlayerUID player). Thanks to rotceh_dnih
<br/>

The Debug Monitor works with Chernarus but should also work with other maps (back up your original files before testing).

I accept no responsibility for any damage or downtime this script may cuase to your server. (please backup first)  
The script has been tested and confirmed to be working by both admins and regular users on my server.
If you do not understand any of my instructions below, then please contact me: urbanskaters at gmail dot com

##Version requirements

This debug monitor has been tested with Chernarus using DayzCode V1.7.6.1 <br/>
I cannot guarantee that it will work with any other version, though it should work with other maps.

##Instructions

NB: These instructions assume you already know how to unpack your mission.pbo, if not please Google for more information.

First things first, merge the included init.sqf with your own mission init.sqf file. 

You DO NOT need the mission.sqm or description.ext files, these are just to complete the mission folder structure.
You should have your own, but if you haven't then use these instead (they only work with Chernarus though)

Copy the debug folder and contents to your mission folder, along with the merged init.sqf (if you haven't done so already)

You will need to make changes to the following file:

* debug\playerstats.sqf (near line 13)

Look for this code: <code> if ((getPlayerUID player) in ["11111","222222"]) </code>

And change the UIDs to those of yours and your admin(s). 

To add more UIDS simply put a comma at the end of the last UID and add a UID in brackets..

So adding a new UID to the above example would look like this <code> ["11111","22222","33333"] </code>

##Detailed instructions for editing your init.sqf file

* This is what you need to edit in YOUR mission init.sqf file, although you could just copy and paste the one provided in this folder...<br/>
* Don't forget to change your Instance number (at the top of your init file). 
* Comment out this line:<br/>
<code>  call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functionscall</code>
* So it looks like ths:<br/>
<code>  //call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";  			//Compile regular functions</code>
* Then right underneath add this line:<br/>
<code>  call compile preprocessFileLineNumbers "debug\compiles.sqf";				//Compile regular functions</code>
* Right after this line:<br/>
<code>  "filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";</code>
* Add this line:<br/>
<code>  playerstats = compile preprocessFileLineNumbers "debug\playerstats.sqf";</code>
<br/><br/>
That's all you need to edit in your init.sqf, after you've made those changes<br/>that part of the document should look something like this:
<br/>
<br/>
<pre><code> //Load in compiled functions
  call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)
  progressLoadingScreen 0.1;
  call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\publicEH.sqf";				//Initilize the publicVariable event handlers
  progressLoadingScreen 0.2;
  call compile preprocessFileLineNumbers "\z\addons\dayz_code\medical\setup_functions_med.sqf";	//Functions used by CLIENT for mediprogressLoadingScreen 0.4;
  //call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functions
  call compile preprocessFileLineNumbers "debug\compiles.sqf";				//Compile regular functions
  progressLoadingScreen 1.0;
  "filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";
  playerstats = compile preprocessFileLineNumbers "debug\playerstats.sqf";</code></pre>

<br/><br/>
If you're just going to use the included init.sqf instead of merging the changes with your own,<br/> 
then don't forget to change your Instance number at the top of the file.
<br/><br/>

##More Info:

If you want to see what the non-admin debug monitor looks like, then simply ommit your UID from the list.  
Only UID's listed will get the Admin debug monitor. Either SCRL+LCK or the H key should bring it up. 

HOTKEY ADVICE:<br/>
Options > Controls > Custom Controls > (assign your hotkey to User Action 20)

Any questions or comments about this version to: urbanskaters at gmail dot com

If you feel brave and want to try new variables, then visit (for a list of useful commands): 
http://community.bistudio.com/wiki/Category:Scripting_Commands_ArmA2 <br/>
Unfortunately I can't provide support for any changes you make to this script.  

Project Wiki Page: https://github.com/nomadichayward/DayZ_Dual_Admin_Debug_Monitor/wiki/DayZ-Dual-Admin-Debug-Monitor

##Credits:

Credit to P1-Kashwak for letting me modify and republish his original project :)<br/>
The original Project page by P1-Kashwak can be found here: <br/>
http://opendayz.net/index.php?threads/dayz-debug-monitor.8256/

##About Nomadic Hayward:

Hayward is a WordPress consultant, IT Lecturer and Charity Worker living in London.  He calls himself Nomadic
Hayward because that's where his life is heading, he has long since given up doing anything just for the money 
and now focuses on charity work, teaching people how to set up websites, tinkering with code and planning 
his escape in 2015 when his Nomadic lifestyle should be well underway.  He believes in open source projects with a 
real passion and feels that people shouldn't need to charge for doing the things they love doing, as this takes away 
from the pleasure of doing it.  He accepts his own faults but dislikes others who can't do the same! 

##Donations:

This is in response to people asking if they can make a donation for my efforts.<br/>
You can either drop me a gift donation via paypal, my email is urbanskaters AT gmail DOT com<br/>
Or why not give your donation to my favourite charity instead: http://www.actionagainsthunger.org.uk/<br/><br/>
Thank you for your kindness and gratitude.   

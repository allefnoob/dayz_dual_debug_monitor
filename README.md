![logo](http://i45.tinypic.com/30rp5qx.jpg)<br /><br />



##DayZ Dual Debug Monitor (V2 FINAL)
=============================

The DayZ Dual Debug Monitor (remember you saw it here first) gives admins a special extended debug monitor while giving normal players 
the regular version (non-admin), It is kept up to date by Nomadic Hayward (aka UrbanSkaters).  When a regular
NON-admin user logs in they will see the debug monitor on the left (see screenshot above) and when an Admin
logs in (assuming you've put their UID in the list as explained below), they will see the extended debug monitor.
<br/>

##Instructions

NB: These instructions assume you already know how to unpack your mission.pbo, if not please Google for more information.

* Create a folder called Custom in your mission folder.
* Copy your compiles.sqf from your dayz_code\init folder to the custom folder you just created.
* Copy the playerstats.sqf file from debug folder included on this github to your custom folder.
* In your custom folder you should now have 2 files: compiles.sqf and playerstats.sqf
* Open and edit the playerstats.sqf file:

Look for: <code> if ((getPlayerUID player) in ["11111","222222"]) </code>

Then change the UIDs to those of yours and your admin(s).
UIDs are found under your profile in Arma under Player Profile, Edit, Player ID.

To add more UIDS simply put a comma at the end of the last UID and add a UID in brackets..
DO NOT put a comma after the last UID, or it will break the script.

So adding a new UID to the above example would look like this <code> ["11111","22222","33333"] </code>

##Now for the really tricky part, pay attention:

You need to follow the rest of this , stype by step.. Or errors will occur ;)

##Detailed instructions for editing your compiles.sqf file

Look for this code:
<pre><code>if (_dikCode in actionKeys "User20" and (diag_tickTime - dayz_lastCheckBit > 5)) then {
			dayz_lastCheckBit = diag_tickTime;
			_nill = execvm "\z\addons\dayz_code\actions\playerstats.sqf";
		};</code></pre>

and change it to:

<pre><code>if (_dikCode in actionKeys "User20" and (diag_tickTime - dayz_lastCheckBit > 5)) then {
			dayz_lastCheckBit = diag_tickTime;
			_nill = execvm "custom\playerstats.sqf";
		};</code></pre>

Look for this code:

<code>if (_dikCode == 210) then {
				_nill = execvm "\z\addons\dayz_code\actions\playerstats.sqf";
		};</code>
		
and change it to:

<code>if (_dikCode == 210) then {
				_nill = execvm "custom\playerstats.sqf";
		};</code>
 
##Detailed instructions for editing your init.sqf file

* This is what you need to edit in your mission init.sqf file.
* Don't forget to change your Instance number (at the top of your init file). 
* Comment out this line:<br/>
<code>  call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functionscall</code>
* So it looks like ths:<br/>
<code>  //call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";  			//Compile regular functions</code>
* Then right underneath add this line:<br/>
<code>  call compile preprocessFileLineNumbers "custom\compiles.sqf";				//Compile regular functions</code>
* Right after this line:<br/>
<code>  "filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";</code>
* Add this line:<br/>
<code>  playerstats = compile preprocessFileLineNumbers "custom\playerstats.sqf";</code>
<br/><br/>
That's all you need to edit in your init.sqf, after you've made those changes<br/>that part of the document should look something like this:
<br/>
<br/>
No repackage your mission.pbo and upload , then test out your new dual admin debug monitor! 

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

##Donations:

This is in response to people asking if they can make a donation for my efforts.<br/>
You can either drop me a gift donation via paypal, my email is urbanskaters AT gmail DOT com<br/>
Or why not give your donation to my favourite charity instead: http://www.actionagainsthunger.org.uk/<br/><br/>
Thank you for your kindness and gratitude.   

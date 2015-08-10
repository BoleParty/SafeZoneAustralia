Orignial script by Friendly
Edit for Esseker by BoleParty[TGM]

There`s another option out there which is working with ProtectionZones and you could use that one instead. Do what you feel like:)


Stock Epoch AntiHack maybe does a cleanup on the player eventhandlers but i was using InfiStar so i can`t tell for sure.

In case you are using InfiStar in run.sqf change following settings to false:

/*  revert allowDamage   */ _RAD = false; /* true or false */ /* if you have safezones using "player allowDamage false;" or similar.. set _RAD = false; */

/*  HandleDamage check   */ _HDC = false; /* true or false */ /* *experimental + Epoch only* - probably publicVariableServer spam but no more godmode hackers. */

/*  Revert HandleDamage  */ _RHD = false; /* true or false */ /* Needs to be  false  for Paintball script */
/
*  Use EH_Fired check   */ _EHF = false; /* true or false */ /* Some mods revert the EventHandlers by default and can cause problems with this check. Tested on Epoch and AltisLife.  */



The safezone.sqf put anywhere into your mission file.

Edit your init.sqf and add: [] execVM "safezone.sqf";

If you don`t have an init.sqf just create one and add this line to it.

You can put this file into any folder being loctated in your mission.pbo but you have to call it from the right spot then (for example: [] execVM "scripts\safezone.sqf";

Replace your mission.sqm with the attached one or add the code yourself. If you wanna do all on your own then propbably your mission.sqm is still encrypted so you need to decrypt it. I use eliteness for this action and you can download it from here:

http://www.ofpec.com/editors-depot/index.php?action=details&id=383


Your markers class needs to be replaced with following code:

	class Markers
	{
		items=11;
		class Item0
		{
			position[]={20480,0,20480};
			name="center";
			type="Empty";
		};
		class Item1
		{
			position[]={30400,0,6100};
			name="respawn_east";
			type="Empty";
			angle=23.6085;
		};
		class Item2
		{
			position[]={30400,0,6100};
			name="respawn_west";
			type="Empty";
			angle=23.6085;
		};
		class Item3
		{
			position[]={4056.3335,79.623558,19436.004};
			name="westsafezone";
			text="Safe Zone";
			type="mil_warning";
			colorName="ColorRed";
		};
		class Item4
		{
			position[]={4048.0366,82.115974,19438.057};
			name="westspawn";
			markerType="ELLIPSE";
			type="Empty";
			colorName="ColorGreen";
			fillName="Grid";
			a=250;
			b=250;
		};
		class Item5
		{
			position[]={24389.191,7.4310384,13971.914};
			name="centralsafezone";
			text="Safe Zone";
			type="mil_warning";
			colorName="ColorRed";
		};
		class Item6
		{
			position[]={24382.695,7.4310384,13961.509};
			name="centralspawn";
			markerType="ELLIPSE";
			type="Empty";
			colorName="ColorGreen";
			fillName="Grid";
			a=250;
			b=250;
		};
		class Item7
		{
			position[]={34751.414,9.2192793,13432.278};
			name="eastsafezone";
			text="Safe Zone";
			type="mil_warning";
			colorName="ColorRed";
		};
		class Item8
		{
			position[]={34758.129,9.8981638,13431.333};
			name="eastspawn";
			markerType="ELLIPSE";
			type="Empty";
			colorName="ColorGreen";
			fillName="Grid";
			a=250;
			b=250;
		};
		class Item9
		{
			position[]={19032.715,10.724709,33974.82};
			name="northsafezone";
			text="Safe Zone";
			type="mil_warning";
			colorName="ColorRed";
		};
		class Item10
		{
			position[]={19032.531,10.677651,33980.871};
			name="northspawn";
			markerType="ELLIPSE";
			type="Empty";
			colorName="ColorGreen";
			fillName="Grid";
			a=250;
			b=250;
		};
	};
	
	
	Directly after your class Markers add:

	class Sensors
	{
		items=4;
		class Item0
		{
			position[]={4048.4653,82.176712,19441.115};
			a=250;
			b=250;
			activationBy="ANY";
			repeating=1;
			interruptable=1;
			age="UNKNOWN";
			name="westsafezone";
			expCond="(player distance westsafezone) < 250;";
			expActiv="hint ""You have entered A Safe Zone! Do not fire in the Safe Zones."";  inSafeZone = true;";
			expDesactiv="hint ""You are leaving the Safe Zone!""; inSafeZone = false;";
			class Effects
			{
			};
		};
		class Item1
		{
			position[]={24381.781,7.4310384,13961.409};
			a=250;
			b=250;
			activationBy="ANY";
			repeating=1;
			interruptable=1;
			age="UNKNOWN";
			name="centralsafezone";
			expCond="(player distance centralsafezone) < 250;";
			expActiv="hint ""You have entered A Safe Zone! Do not fire in the Safe Zones.""; inSafeZone = true;";
			expDesactiv="hint ""You are leaving the Safe Zone!""; inSafeZone = false;";
			class Effects
			{
			};
		};
		class Item2
		{
			position[]={34756.5,9.7098522,13432.255};
			a=250;
			b=250;
			activationBy="ANY";
			repeating=1;
			interruptable=1;
			age="UNKNOWN";
			name="eastsafezone";
			expCond="(player distance eastsafezone) < 250;";
			expActiv="hint ""You have entered A Safe Zone! Do not fire in the Safe Zones.""; inSafeZone = true;";
			expDesactiv="hint ""You are leaving the Safe Zone!""; inSafeZone = false;";
			class Effects
			{
			};
		};
		class Item3
		{
			position[]={19031.406,10.670341,33982.809};
			a=250;
			b=250;
			activationBy="ANY";
			repeating=1;
			interruptable=1;
			age="UNKNOWN";
			name="northsafezone";
			expCond="(player distance northsafezone) < 250;";
			expActiv="hint ""You have entered A Safe Zone! Do not fire in the Safe Zones.""; inSafeZone = true;";
			expDesactiv="hint ""You are leaving the Safe Zone!""; inSafeZone = false;";
			class Effects
			{
			};
		};
	};
	
After your changes you don`t need to encrypt the file again as the server will read the decrypted mission.sqm without any issues.

Regards
BoleParty

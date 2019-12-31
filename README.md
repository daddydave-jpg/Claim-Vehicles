# Claim-Vehicles
Allows players to save non-persistent vehicles using a code lock (Exile Mod)

STEP 1
Add client folder to your mission folder (MISSION.MAPNAME, eg Exile.Tanoa)

STEP 2
merge interactions into your CfgInteractionMenus in your mission file config.cpp
(example 1)

class CfgInteractionMenus // example 1
{
	class Car // boat, plane, etc, add to all vehicle classes you want to be able to claim
	{
		targetType = 2;
		target = "Car";

		class Actions 
		{
			class ClaimVehicle: ExileAbstractAction // Place somewhere under Actions with the rest of the actions!
			{
				title = "Claim Ownership";
				condition = "true";
				action = "call ExileClient_ClaimVehicles_network_claimRequestSend";
			};
    };
  };
  
STEP 3
server pbo to @exileserver/addons 

STEP 4
Drag code folder to mission.mapname root. In mission config.cpp locate CFGExileCustomCode and insert override ExileServer_system_garbageCollector_deleteObject.sqf
(example 2)

class CfgExileCustomCode // example 2
{
  ExileServer_system_garbageCollector_deleteObject = "code\ExileServer_system_garbageCollector_deleteObject.sqf";
};

Make sure you use correct file path if you place the sqf different than shown above!

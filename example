/*	---------------------------------------------------------------
	 This header contains GTAIV/EFLC PC script common functions.

	 This file is a part of scocl project (C) Alexander Blade 2011

	 Created Some Natives using Existing Game Natives for Convenience.

	---------------------------------------------------------------  */

#pragma once
#include "constants.h"
#include "natives.h"

float x, y, z, h;
Ped ped, ped2, ped3, ped4;
Vehicle vehicle;
float wx, wy, wz, wh;


Player GetPlayerIndex(void)
{
	return GET_PLAYER_ID();
}

Ped GetPlayerPed(void)
{
	Ped playerped = INVALID_HANDLE;
	if (PLAYER_HAS_CHAR(GetPlayerIndex()))
		GET_PLAYER_CHAR(GetPlayerIndex(), &playerped);
	return playerped;
}

//Spawn Cars With Specified Passengers and at Specific Location
void SPAWN_CAR_WITH_FOUR_PASSENGER(eRelationshipGroup type, uint p1, uint p2, uint p3, uint p4, uint car, float dist)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	GET_CLOSEST_CAR_NODE_WITH_HEADING(x + 50, y + dist, z, &wx, &wy, &wz, &h);
	CREATE_CAR(car, wx, wy, wz, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(type, p1, x, wy, z, &ped, TRUE);
		CREATE_CHAR(type, p2, x, wy, z, &ped2, TRUE);
		CREATE_CHAR(type, p3, x, wy, z, &ped3, TRUE);
		CREATE_CHAR(type, p4, x, wy, z, &ped4, TRUE);
		if (DOES_CHAR_EXIST(ped))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, 0);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		if (DOES_CHAR_EXIST(ped4))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped4, vehicle, 1);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped4);
		}
		if (DOES_CHAR_EXIST(ped3))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped3, vehicle, 2);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped3);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);
	}
}

//Spawn Car with Only Two Passengers
void SPAWN_CAR_WITH_TWO_PASSENGER(eRelationshipGroup type, uint p1, uint p2, uint car, float dist)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	GET_CLOSEST_CAR_NODE_WITH_HEADING(x + 50, y + dist, z, &wx, &wy, &wz, &h);
	CREATE_CAR(car, wx, wy, wz, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(type, p1, x, wy, z, &ped, TRUE);
		CREATE_CHAR(type, p2, x, wy, z, &ped2, TRUE);
		if (DOES_CHAR_EXIST(ped))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, 0);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);

	}
}

//Spawn Car With Only Driver (Can be Used for Police Bike too)
void SPAWN_CAR_WITH_DRIVER(eRelationshipGroup type, uint p1, uint car, float dist)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	GET_CLOSEST_CAR_NODE_WITH_HEADING(x + 50, y + dist, z, &wx, &wy, &wz, &h);
	CREATE_CAR(car, wx, wy, wz, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(type, p1, x, wy, z, &ped, TRUE);
		if (DOES_CHAR_EXIST(ped))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);

	}
}

//Create Car with 3 Different Passengers and 'seat = 1 for Right Rear,2 for Left Rear'
void SPAWN_CAR_WITH_THREE_PASSENGER(eRelationshipGroup type, uint p1, uint p2, uint p3, uint car, float dist, int seat)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	GET_CLOSEST_CAR_NODE_WITH_HEADING(x + 50, y + dist, z, &wx, &wy, &wz, &h);
	CREATE_CAR(car, wx, wy, wz, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(type, p1, x, wy, z, &ped, TRUE);
		CREATE_CHAR(type, p2, x, wy, z, &ped2, TRUE);
		CREATE_CHAR(type, p3, x, wy, z, &ped3, TRUE);
		if (DOES_CHAR_EXIST(ped))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, 0);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		if (DOES_CHAR_EXIST(ped3))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped3, vehicle, seat);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped3);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);

	}
}

//Spawn Cop Car with 4 Specific Passengers with Guns. set 1 or 0
void SPAWN_COP_CAR_WITH_FOUR_PASSENGERS(uint p1, uint p2, uint p3, uint p4, uint car, Weapon primary, Weapon secondary, float dist, int armour)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	GET_CLOSEST_CAR_NODE_WITH_HEADING(x + 50, y + dist, z, &wx, &wy, &wz, &h);
	CREATE_CAR(car, wx, wy, wz, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p1, wx, wy, z, &ped, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p2, wx, wy, z, &ped2, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p3, wx, wy, z, &ped3, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p4, wx, wy, z, &ped4, TRUE);

		if (DOES_CHAR_EXIST(ped))
		{
			if (armour == 1) ADD_ARMOUR_TO_CHAR(ped, 100);
			GIVE_WEAPON_TO_CHAR(ped, primary, 200, 1);
			GIVE_WEAPON_TO_CHAR(ped, secondary, 50, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{
			if (armour == 1) ADD_ARMOUR_TO_CHAR(ped2, 100);
			GIVE_WEAPON_TO_CHAR(ped2, primary, 200, 1);
			GIVE_WEAPON_TO_CHAR(ped2, secondary, 50, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, 0);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		if (DOES_CHAR_EXIST(ped4))
		{
			if (armour == 1) ADD_ARMOUR_TO_CHAR(ped4, 100);
			GIVE_WEAPON_TO_CHAR(ped4, primary, 200, 1);
			GIVE_WEAPON_TO_CHAR(ped4, secondary, 50, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped4, vehicle, 1);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped4);
		}
		if (DOES_CHAR_EXIST(ped3))
		{
			if (armour == 1) ADD_ARMOUR_TO_CHAR(ped3, 100);
			GIVE_WEAPON_TO_CHAR(ped3, primary, 200, 1);
			GIVE_WEAPON_TO_CHAR(ped3, secondary, 50, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped3, vehicle, 2);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped3);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);
	}
}

//Spawn Cop Car with 2 Passengers with Guns
void SPAWN_COP_CAR(uint p1, uint p2, uint car, Weapon primarygun, Weapon secondgun, float dist)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	GET_CLOSEST_CAR_NODE_WITH_HEADING(x + 50, y + dist, z, &wx, &wy, &wz, &h);
	CREATE_CAR(car, wx, wy, wz, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p1, x, wy, z, &ped, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p2, x, wy, z, &ped2, TRUE);
		if (DOES_CHAR_EXIST(ped))
		{
			GIVE_WEAPON_TO_CHAR(ped, primarygun, 100, 1);
			GIVE_WEAPON_TO_CHAR(ped, secondgun, 100, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{
			GIVE_WEAPON_TO_CHAR(ped2, primarygun, 100, 1);
			GIVE_WEAPON_TO_CHAR(ped2, secondgun, 100, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, 0);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);
	}
}

//Spawn TACICAL Police/Force Car With Specific Passengers with Set of Weapons.
void SPAWN_TACTICAL_POLICE_WITH_CAR_AND_GUNS(uint p1, uint p2, uint p3, uint p4, uint car, float dist, Weapon ar, Weapon smg, Weapon sg, Weapon handgun, int amt)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	GET_CLOSEST_CAR_NODE_WITH_HEADING(x + 50, y + dist, z, &wx, &wy, &wz, &h);
	CREATE_CAR(car, wx, wy, wz, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p1, x, wy, z, &ped, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p2, x, wy, z, &ped2, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p3, x, wy, z, &ped3, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p4, x, wy, z, &ped4, TRUE);
		
		if (DOES_CHAR_EXIST(ped))
		{
			ADD_ARMOUR_TO_CHAR(ped, amt);
			GIVE_WEAPON_TO_CHAR(ped, ar, 300, 1);
			GIVE_WEAPON_TO_CHAR(ped, smg, 150, 1);
			GIVE_WEAPON_TO_CHAR(ped, sg, 30, 1);
			GIVE_WEAPON_TO_CHAR(ped, handgun, 20, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped4))
		{
			ADD_ARMOUR_TO_CHAR(ped4, amt);
			GIVE_WEAPON_TO_CHAR(ped4, ar, 300, 1);
			GIVE_WEAPON_TO_CHAR(ped4, smg, 150, 1);
			GIVE_WEAPON_TO_CHAR(ped4, sg, 30, 1);
			GIVE_WEAPON_TO_CHAR(ped4, handgun, 20, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped4, vehicle, 0);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped4);
		}
		if (DOES_CHAR_EXIST(ped2))
		{
			ADD_ARMOUR_TO_CHAR(ped2, amt);
			GIVE_WEAPON_TO_CHAR(ped2, ar, 300, 1);
			GIVE_WEAPON_TO_CHAR(ped2, smg, 150, 1);
			GIVE_WEAPON_TO_CHAR(ped2, sg, 30, 1);
			GIVE_WEAPON_TO_CHAR(ped2, handgun, 20, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, 1);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		if (DOES_CHAR_EXIST(ped3))
		{
			ADD_ARMOUR_TO_CHAR(ped3, amt);
			GIVE_WEAPON_TO_CHAR(ped3, ar, 300, 1);
			GIVE_WEAPON_TO_CHAR(ped3, smg, 150, 1);
			GIVE_WEAPON_TO_CHAR(ped3, sg, 30, 1);
			GIVE_WEAPON_TO_CHAR(ped3, handgun, 20, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped3, vehicle, 2);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped3);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);

	}
}

//Spawn TACTICAL Police/Force with 2 Passengers with Set of Weapons. Arnour 'amt' = set 100
void SPAWN_TACTICAL_CAR_WITH_TWO_PASSENGER_WITH_GUNS(uint p1, uint p2, Weapon ar, Weapon smg, Weapon sg, Weapon handgun, uint car, float dist, int amt)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	GET_CLOSEST_CAR_NODE_WITH_HEADING(x + 50, y + dist, z, &wx, &wy, &wz, &h);
	CREATE_CAR(car, wx, wy, wz, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p1, x, wy, z, &ped, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p2, x, wy, z, &ped2, TRUE);
		
		
		if (DOES_CHAR_EXIST(ped))
		{
			ADD_ARMOUR_TO_CHAR(ped, amt);
			GIVE_WEAPON_TO_CHAR(ped, ar, 300, 1);
			GIVE_WEAPON_TO_CHAR(ped, smg, 150, 1);
			GIVE_WEAPON_TO_CHAR(ped, sg, 30, 1);
			GIVE_WEAPON_TO_CHAR(ped, handgun, 20, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{
			ADD_ARMOUR_TO_CHAR(ped2, amt);
			GIVE_WEAPON_TO_CHAR(ped2, ar, 300, 1);
			GIVE_WEAPON_TO_CHAR(ped2, smg, 150, 1);
			GIVE_WEAPON_TO_CHAR(ped2, sg, 30, 1);
			GIVE_WEAPON_TO_CHAR(ped2, handgun, 20, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, 0);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);

	}
}

//Spawn Police Bike but must have 2 seats
void SPAWN_POLICE_BIKE_TWO_SEAT(uint p1, uint p2, uint bike, float dist)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	GET_CLOSEST_CAR_NODE_WITH_HEADING(x + 50, y + dist, z, &wx, &wy, &wz, &h);
	CREATE_CAR(bike, wx, wy, wz, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p1, x, wy, z, &ped, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p2, x, wy, z, &ped2, TRUE);
		if (DOES_CHAR_EXIST(ped))
		{
			GIVE_PED_HELMET(ped);
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{
			GIVE_PED_HELMET(ped2);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, -2);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);
	}
}

//Spawn Police Bike 
void SPAWN_POLICE_BIKE(uint p1,  uint bike, float dist)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	GET_CLOSEST_CAR_NODE_WITH_HEADING(x + 50, y + dist, z, &wx, &wy, &wz, &h);
	CREATE_CAR(bike, wx, wy, wz, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p1, x, wy, z, &ped, TRUE);
		if (DOES_CHAR_EXIST(ped))
		{
			GIVE_PED_HELMET(ped);
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);
	}
}
//Spawn Boat with Only Two Passengers
void SPAWN_BOAT(eRelationshipGroup type, uint p1, uint p2, uint car, float dist)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	vector3 loc;
	GET_NTH_CLOSEST_WATER_NODE_WITH_HEADING(x + 10, y + dist, z, true, true, &loc, &h);
	CREATE_CAR(car, loc.x, loc.y, loc.z, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(type, p1, x, y + 50, z, &ped, TRUE);
		CREATE_CHAR(type, p2, x, y + 50, z, &ped2, TRUE);
		if (DOES_CHAR_EXIST(ped))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, -2);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);
	}
}

//Spawn Police Helicopter. 
void SPAWN_POLICE_HELICOPTER(uint p1, uint p2, uint p3, uint p4, uint heli, Weapon primary, Weapon secondary, float dist)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	CREATE_CAR(heli, x, y + dist, z + dist, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p1, x, y + dist, z + 50, &ped, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p2, x, y + dist, z, &ped2, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p3, x, y + dist, z, &ped3, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p4, x, y + dist, z, &ped4, TRUE);
		ADD_ARMOUR_TO_CHAR(ped, 100);
		ADD_ARMOUR_TO_CHAR(ped2, 100);
		ADD_ARMOUR_TO_CHAR(ped3, 100);
		ADD_ARMOUR_TO_CHAR(ped4, 100);
		if (DOES_CHAR_EXIST(ped))
		{

			GIVE_WEAPON_TO_CHAR(ped, primary, 400, 1);
			GIVE_WEAPON_TO_CHAR(ped, secondary, 50, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{

			GIVE_WEAPON_TO_CHAR(ped2, primary, 400, 1);
			GIVE_WEAPON_TO_CHAR(ped2, secondary, 50, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, 0);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		if (DOES_CHAR_EXIST(ped4))
		{

			GIVE_WEAPON_TO_CHAR(ped4, primary, 400, 1);
			GIVE_WEAPON_TO_CHAR(ped4, secondary, 50, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped4, vehicle, 1);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped4);
		}
		if (DOES_CHAR_EXIST(ped3))
		{

			GIVE_WEAPON_TO_CHAR(ped3, primary, 400, 1);
			GIVE_WEAPON_TO_CHAR(ped3, secondary, 50, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped3, vehicle, 2);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped3);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);

	}
}


//Spawn Police Boat. 
void SPAWN_POLICE_BOAT(uint p1, uint p2, uint p3, uint p4, uint boat, Weapon primary, Weapon secondary, float dist)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	vector3 loc;
	GET_NTH_CLOSEST_WATER_NODE_WITH_HEADING(x + 10, y + dist, z, true, true, &loc, &h);
	CREATE_CAR(boat, loc.x, loc.y, loc.z, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p1, x, y + 100, z, &ped, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p2, x, y + 100, z, &ped2, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p3, x, y + 100, z, &ped3, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p4, x, y + 100, z, &ped4, TRUE);
		if (DOES_CHAR_EXIST(ped))
		{

			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			GIVE_WEAPON_TO_CHAR(ped, primary, 300, 1);
			GIVE_WEAPON_TO_CHAR(ped, secondary, 150, 1);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{

			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, 0);
			GIVE_WEAPON_TO_CHAR(ped2, primary, 300, 1);
			GIVE_WEAPON_TO_CHAR(ped2, secondary, 150, 1);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		if (DOES_CHAR_EXIST(ped3))
		{

			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped3, vehicle, 0);
			GIVE_WEAPON_TO_CHAR(ped3, primary, 300, 1);
			GIVE_WEAPON_TO_CHAR(ped3, secondary, 150, 1);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped3);
		}
		if (DOES_CHAR_EXIST(ped4))
		{

			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped4, vehicle, 0);
			GIVE_WEAPON_TO_CHAR(ped4, primary, 300, 1);
			GIVE_WEAPON_TO_CHAR(ped4, secondary, 150, 1);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped4);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);
	}
}

//Spawn Helicopter
void SPAWN_HELICOPTER(eRelationshipGroup type, uint p1, uint p2, uint p3, uint p4, uint heli, float dist)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	CREATE_CAR(heli, x, y + dist, z, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(type, p1, x, y + dist, z, &ped, TRUE);
		CREATE_CHAR(type, p2, x, y + dist, z, &ped2, TRUE);
		CREATE_CHAR(type, p3, x, y + dist, z, &ped3, TRUE);
		CREATE_CHAR(type, p4, x, y + dist, z, &ped4, TRUE);
		if (DOES_CHAR_EXIST(ped))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			TASK_CAR_MISSION_PED_TARGET_NOT_AGAINST_TRAFFIC(ped, heli, GetPlayerIndex(), 4, 50, 2, 5, 10);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, 0);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		if (DOES_CHAR_EXIST(ped4))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped4, vehicle, 1);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped4);
		}
		if (DOES_CHAR_EXIST(ped3))
		{
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped3, vehicle, 2);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped3);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);

	}
}

//Spawn TACTICAL Police/Force with 2 Passengers with Set of Weapons plus RPG or Grenade (your choice). Arnour 'amt' = set 100
void SPAWN_TACTICAL_CAR_WITH_TWO_PASSENGER_AND_HEAVY_WEAPON(uint p1, uint p2, Weapon heavy, Weapon smg, Weapon sg, Weapon handgun, uint car, float dist, int amt)
{
	GET_CHAR_COORDINATES(GetPlayerPed(), &x, &y, &z);
	WAIT(0);
	GET_CLOSEST_CAR_NODE_WITH_HEADING(x + 50, y + dist, z, &wx, &wy, &wz, &h);
	CREATE_CAR(car, wx, wy, wz, &vehicle, TRUE);
	SET_CAR_HEADING(vehicle, h);
	if (DOES_VEHICLE_EXIST(vehicle))
	{
		WAIT(0);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p1, x, wy, z, &ped, TRUE);
		CREATE_CHAR(RELATIONSHIP_GROUP_COP, p2, x, wy, z, &ped2, TRUE);
		
		
		if (DOES_CHAR_EXIST(ped))
		{
			ADD_ARMOUR_TO_CHAR(ped, amt);
			GIVE_WEAPON_TO_CHAR(ped, heavy, 2, 1);
			GIVE_WEAPON_TO_CHAR(ped, smg, 150, 1);
			GIVE_WEAPON_TO_CHAR(ped, sg, 30, 1);
			GIVE_WEAPON_TO_CHAR(ped, handgun, 20, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_DRIVER(ped, vehicle);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped);
		}
		if (DOES_CHAR_EXIST(ped2))
		{
			ADD_ARMOUR_TO_CHAR(ped2, amt);
			GIVE_WEAPON_TO_CHAR(ped2, heavy, 3, 1);
			GIVE_WEAPON_TO_CHAR(ped2, smg, 150, 1);
			GIVE_WEAPON_TO_CHAR(ped2, sg, 30, 1);
			GIVE_WEAPON_TO_CHAR(ped2, handgun, 20, 1);
			TASK_WARP_CHAR_INTO_CAR_AS_PASSENGER(ped2, vehicle, 0);
			MARK_CHAR_AS_NO_LONGER_NEEDED(&ped2);
		}
		MARK_CAR_AS_NO_LONGER_NEEDED(&vehicle);

	}
}

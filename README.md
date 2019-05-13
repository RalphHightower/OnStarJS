# OnStarJS
[![Build Status](https://travis-ci.org/samrum/OnStarJS.svg?branch=master)](https://travis-ci.org/samrum/OnStarJS)
[![Coverage Status](https://coveralls.io/repos/github/samrum/OnStarJS/badge.svg?branch=master)](https://coveralls.io/github/samrum/OnStarJS?branch=master)

An unofficial NodeJS library to make OnStar requests.

**Use at your own risk. This is an unofficial library.**

Use the Get Account Vehicles request to see which requests your vehicle supports.

# Usage

## Sample
Use a random version 4 uuid as a deviceId.

    import OnStar from "onstarjs";

    const config = {
      deviceId: "742249ce-18e0-4c82-8bb2-9975367a7631",
      vin: "1G2ZF58B774109863",
      username: "foo@bar.com",
      password: "p@ssw0rd",
      onStarPin: "1234",
    };

    const onStar = OnStar.create(config);

    onStar
      .alert({
        action: ["Flash"],
      })
      .then(() => {
        onStar.start();
      });

## Get Account Vehicles
    onStar.getAccountVehicles();

## Start
    onStar.start();

## Cancel Start
    onStar.cancelStart();

## Alert
    onStar.alert([options]);

Option | Default | Valid Values
--- | --- | --- 
action | ["Flash", "Honk"] | ["Flash", "Honk"]
delay | 0 | Any integer (minutes)
duration | 1 | Any integer (minutes)
override | ["DoorOpen", "IgnitionOn"] | ["DoorOpen", "IgnitionOn"]

## Cancel Alert
    onStar.cancelAlert();

## Lock Door
    onStar.lockDoor([options]);

Option | Default | Valid Values
--- | --- | ----
delay | 0 | Any integer (minutes)

## Unlock Door
    onStar.unlockDoor([options]);

Option | Default | Valid Values
--- | --- | ---
delay | 0 | Any integer (minutes)

## Charge Override
    onStar.chargeOverride([options]);

Option | Default | Valid Values
--- | --- | ---
mode | "CHARGE_NOW" | "CHARGE_NOW", "CANCEL_OVERRIDE"

## Get Charging Profile
    onStar.getChargingProfile();

## Set Charging Profile
    onStar.setChargingProfile([options]);

Option | Default | Valid Values
--- | --- | ---
chargeMode | "IMMEDIATE" | "DEFAULT_IMMEDIATE", "IMMEDIATE", "DEPARTURE_BASED", "RATE_BASED", "PHEV_AFTER_MIDNIGHT" 
rateType | "MIDPEAK" |  "OFFPEAK", "MIDPEAK", "PEAK"

## Diagnostics
    onStar.diagnostics([options]);

Option | Default | Valid Values
--- | --- | ---
diagnosticItem | ["ODOMETER", "TIRE PRESSURE",  "AMBIENT AIR TEMPERATURE", "LAST TRIP DISTANCE"] | ["ENGINE COOLANT TEMP", "ENGINE RPM", "LAST TRIP FUEL ECONOMY", "EV ESTIMATED CHARGE END", "EV BATTERY LEVEL", "OIL LIFE", "EV PLUG VOLTAGE", "LIFETIME FUEL ECON", "HOTSPOT CONFIG", "LIFETIME FUEL USED", "ODOMETER", "HOTSPOT STATUS", "LIFETIME EV ODOMETER", "EV PLUG STATE", "EV CHARGE STATE", "TIRE PRESSURE", "AMBIENT AIR TEMPERATURE", "LAST TRIP DISTANCE", "INTERM VOLT BATT VOLT", "GET COMMUTE SCHEDULE", "GET CHARGE MODE", "EV SCHEDULED CHARGE START", "FUEL TANK INFO", "HANDS FREE CALLING", "ENERGY EFFICIENCY", "VEHICLE RANGE"]

# Credits
Made possible by [mikenemat](https://github.com/mikenemat/)'s work in [gm-onstar-probe](https://github.com/mikenemat/gm-onstar-probe). Most of the implementation follows what they were doing.

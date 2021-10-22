Marlin 2.0.x Configuration for Ender3 Pro w/ SKR 32 bit & AutoLev
=====

My Ender3 Pro Marlin configuration w/Autolevel
Tested with bugfix-2.0.x, marlin-2.0.9.1


## Tunables that should be enabled

file: **Configuration.h**

```c
#define PREVENT_COLD_EXTRUSION
#define EXTRUDE_MINTEMP 170
#define PREVENT_LENGTHY_EXTRUDE
#define EXTRUDE_MAXLENGTH 400 // tune this according to bowden tube length for load/unload
#define S_CURVE_ACCELERATION
```

file: **Configuration_adv.h**

```c
#define BABYSTEPPING
```

## Autolev parameters


file: **Configuration.h**

```c
#define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN
#define FIX_MOUNTED_PROBE
#define NOZZLE_TO_PROBE_OFFSET { -42, -11, 0 }
#define MULTIPLE_PROBING 2
#define AUTO_BED_LEVELING_BILINEAR
#define DEBUG_LEVELING_FEATURE
#define Z_SAFE_HOMING
#define Z_MIN_PROBE_REPEATABILITY_TEST
#define Z_CLEARANCE_DEPLOY_PROBE 3
#define Z_CLEARANCE_BETWEEN_PROBES 3
#define Z_CLEARANCE_MULTI_PROBE 3
//#define Z_AFTER_PROBING  //  -- > comment this line
#define Z_PROBE_LOW_POINT -2
#if ENABLED(Z_SAFE_HOMING)
  #define Z_SAFE_HOMING_X_POINT X_BED_SIZE/2  // X point for Z homing  
  #define Z_SAFE_HOMING_Y_POINT Y_BED_SIZE/2  // Y point for Z homing
#endif
```

## Other parameters to consider/verify

```c
#define PREHEAT_BEFORE_PROBING
```


## Install/calibrate Autolev

1. After updating the Marlin firmware, clear EEPROM

```gcode
M502 ; factory reset
M500 ; save
```

2. Set carriage to home

```gcode
G28
G1 Z0
```

3. Turn on the temperature in the menu Temperature -> Preheat PLA
4. Wait for the temperature to reach the predefined values
5. Adjust Z offset by using a piece of paper and adjusting the Z position in menu Motion -> Move Axis -> Move Z -> Move 0.1mm. Beware
not to scratch the bed by jumping large values
6. Take note of the Z value when finishing adjusting the Z
7. Store the value and save

```gcode
M851 Z(value of Z from step 6)
M500 ; Save to EEPROM
```

To test the new base offset:
```gcode
G28    ; home all axis
G1 Z0  ; nozzle should be at right position
```
# Marlin 2.0.x Configuration for Ender3 Pro With AutoLev

My Ender3 Pro Marlin configuration w/Autolevel
Tested with bugfix-2.0.x, marlin-2.0.9.1


### Tunables that should be enabled

#### Configuration.h

#define PREVENT_COLD_EXTRUSION
#define EXTRUDE_MINTEMP 170

#define PREVENT_LENGTHY_EXTRUDE
#define EXTRUDE_MAXLENGTH 400 // tune this according to bowden tube length for load/unload

#define S_CURVE_ACCELERATION

#### Configuration_adv.h

#define BABYSTEPPING


### Autolev parameters

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
//#define Z_AFTER_PROBING  // comment
#define Z_PROBE_LOW_POINT -2

#if ENABLED(Z_SAFE_HOMING)
  #define Z_SAFE_HOMING_X_POINT X_BED_SIZE/2  // X point for Z homing
  #define Z_SAFE_HOMING_Y_POINT Y_BED_SIZE/2  // Y point for Z homing
#endif



### Other parameters to consider/verify

PREHEAT_BEFORE_PROBING



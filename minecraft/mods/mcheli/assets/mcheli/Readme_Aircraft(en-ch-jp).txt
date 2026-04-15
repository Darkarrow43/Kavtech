; ★ Important ★
; Configuration files and models can be reloaded without closing Minecraft.
; [ Enter a vehicle → Press R to open the supply interface → MOD Options → Development → Reload Aircraft Settings ]
; Textures and sounds must be reloaded using Minecraft's native function, not via the Helicopter MOD.
; [ Press Esc to open the game menu → Options → Resource Packs → Done ]

;***********************************************************************************
■ Common Settings for Helicopter/Fighter Plane/Ground Vehicle/Tank Configuration Files
;***********************************************************************************

DisplayName = AH-6 Killer Egg
; Display Name ※Do not use full-width characters; only half-width alphanumerics and symbols are allowed.

AddDisplayName = ja_JP, AH-6 キラ－エッグ
; Name displayed when holding the item.
; ※ When using Japanese full-width characters, file encoding must be UTF-8.

ItemID = 28801
; Item ID (will be +256 when actually used in Minecraft)
; ※ ItemID is not used in version 1.7.2+, but must be set for compatibility with 1.6.4 and earlier.

Invulnerable = true
; Vehicle invincibility mode.
; Recommended for base defense weapons in multiplayer games.

CreativeOnly = true
; Only creative mode players can place or retrieve the item.

AddTexture = sh60-us-1
AddTexture = sh60-jp-1
AddTexture = sh60-jp-2
; Additional textures (can add multiple).
; Uses a .png file with the same name as the config file by default.
; Add extra textures here (no file extension).

ThirdPersonDist = 12
; Default third-person view distance.
; PageUp/Down adjusts distance in 4-block increments in the Helicopter MOD; recommended to set as a multiple of 4.

CameraPosition = 0.0, 1.1, 3.7
CameraPosition = 0.0, 1.1, 3.7, false
CameraPosition = 0.0, 1.1, 3.7, true, 30, 45
; Camera coordinates.
; Multiple settings allow switching between different views with the H key.
; Positions 1-3: Coordinates.
; 4th position: If set to true, camera view is always locked.
; 5th position: Horizontal angle.
; 6th position: Vertical angle.

CameraZoom = 3
; Maximum camera zoom multiplier.

HUD = heli, heli_gnr, none, gunner
; HUD configuration file names used for each seat.
; In this example: Pilot seat uses heli.txt, 2nd seat uses heli_gnr.txt, 3rd seat has no HUD, 4th seat uses gunner.txt.
; If fewer settings than seats, unspecified seats use the following defaults:
; Default when not set:
; Helicopter: HUD = heli, heli_gnr, gunner, gunner, gunner, gunner...
; Plane: HUD = plane, plane, gunner, gunner, gunner, gunner...
; Ground Vehicle: HUD = vehicle
;
; ※ Only the pilot seat uses the 2nd seat's HUD configuration in gunner mode.
;    Even for single-seat vehicles, if gunner mode is enabled, the 2nd seat must be set.
;    Example: HUD = heli, heli_gnr

EnableGunnerMode = true
; Whether to enable gunner mode toggle (true=enabled, false=disabled).

EnableNightVision = true
; Whether to enable night vision mode toggle (true=enabled, false=disabled).

EnableEntityRadar = false
; Whether to enable radar (true=enabled, false=disabled).

Speed = 0.6
; Vehicle speed (higher value = faster).

MotionFactor = 0.96
; Vehicle movement deceleration coefficient (range 0.0~1.0, lower value = stronger deceleration).

Gravity = -0.04
; Vehicle gravity setting (negative value means falling).

GravityInWater = -0.04
; Gravity setting in water (negative value means falling).

StepHeight = 2.5
; Maximum block height the vehicle can step over.

MobilityYaw
MobilityYawOnGround
; Horizontal turn sensitivity (higher value = more agile).
; MobilityYawOnGround only affects ground, not water.
MobilityRoll
; Roll sensitivity (higher value = faster roll).
MobilityPitch
; Pitch sensitivity (higher value = more agile; for ground vehicles, indicates pitch angle limits).
MinRotationPitch
MaxRotationPitch
; Range MinRotationPitch -80~0
; Range MaxRotationPitch 0~80
; Pitch angle limits (min/max).
; ※ Enabling this for helicopters/planes also restricts roll.

MinRotationRoll
MaxRotationRoll
; Roll angle limits (min/max).
; Range MinRotationRoll -80~0
; Range MaxRotationRoll 0~80
; ※ Enabling this for helicopters/planes also restricts pitch.

UnmountPosition = 3.0, 1.0, -2.0
; Coordinates when dismounting.

AddSeat =-0.45,  0.80,  1.20
AddSeat = 0.45, -0.50,  1.20
AddSeat =-0.90, -0.50,  0.20
AddSeat = 0.90, -0.50,  0.20, true
; Add a seat ※At least 1 seat is required except for drones.
; The first one is the pilot seat.
; Parameters are coordinates (X,Y,Z).
; The 4th parameter determines if the seat rotates with the driver's direction (mainly for tank turrets).

AddGunnerSeat = -0.45, 0.80, 1.20,   0.0, 2.00, -1.01,   true
AddGunnerSeat = -0.45, 0.80, 1.20,   0.0, 2.00, -1.01,   true, -60, 78, true
; AddGunnerSeat=Seat X,Y,Z,  Camera X,Y,Z,  Can switch view,  Camera upper limit (-90~0), Camera lower limit (0~90), Seat rotates with turret
; Add a gunner seat.
; Players in this seat default to camera view.
; Parameters include seat coordinates and camera position (camera position can be omitted, defaults to CameraPosition).
; If view switching is false, camera view is locked; if true, H key can switch back to player view.
; The 10th parameter controls if the seat rotates with the driver's direction.

AddFixRotSeat = -0.45,  0.80,  1.20, 0.0,2.00,-1.01,  true,  -50, 40
; AddFixRotSeat=Seat X,Y,Z,  Camera X,Y,Z,  Can switch view,  Fixed horizontal angle, Fixed vertical angle
; Add a fixed-view seat.
; Similar to AddGunnerSeat, but camera angle is fixed and cannot be adjusted.
; Setting fixed angles disables mouse view adjustment (Ctrl key can switch to free view).

; ★★★★★
; Vehicle carrying functionality requires:
; ・Carrying vehicle specifies the carried vehicle (AddRack)
; ・Carried vehicle specifies the rack number of the carrier (RideRack)
; Either condition being met will take effect.

AddRack = container,                 0.0, 1.4, -4.7,  0.0, 1.0, -16.1
AddRack = container / ah-64,         0.0, 1.4, -4.7,  0.0, 1.0, -16.1,  5.0, 20
AddRack = helicopter/vehicle / t-4,  0.0, 1.4, -4.7,  0.0, 1.0, -16.1,  5.0, 100000,  0.0, 0.0
; ■ Carrier settings
; AddRack =
;  Parameter 1: Carryable entity name
;  Parameters 2-4: Rack coordinates X,Y,Z (position on the vehicle)
;  Parameters 5-7: Entrance/exit coordinates X,Y,Z (entity must be near these coordinates to load/unload)
;  Parameter 8: Entrance radius (can be omitted)
;  Parameter 9: Parachute opening height (set very high to disable parachute)
;  Parameter 10: Carried entity's horizontal angle
;  Parameter 11: Carried entity's vertical angle
; Add a rack that can carry containers/helicopters/etc.
;  Entity names can use container/helicopter/plane/vehicle or directly specify a vehicle name (e.g., ah-64), separated by /.

RideRack = c5, 1
; ■ Carried vehicle settings
; RideRack = Carrier vehicle name, Rack number (1~)

ExclusionSeat = 15, 17
; Unlimited number of parameters (must be ≥2)
; Set mutually exclusive seats/racks.
; Example: ExclusionSeat = 3,4,5:
;  If seat 3 is occupied, seats 4/5 cannot hold entities.
;  If seat 4 is occupied, seats 3/5 cannot hold entities.
;  If seat 5 is occupied, seats 3/4 cannot hold entities.
;
; Seat/Rack numbering rule: Number all seat definitions first in order, then number the racks.
; Example configuration order:
;  AddSeat  → No.1
;  AddRack  → No.4
;  AddGunnerSeat → No.2
;  AddRack  → No.5
;  AddSeat  → No.3
;  AddRack  → No.6
; It is recommended to define racks last for clear numbering.

TurretPosition = 0.0, 0.0, 0.25
; Turret rotation center position (not recommended to modify unless necessary).

AddWeapon = m230,     0.00, 0.90, 2.54,   0.0, 0.0, true, 2
AddWeapon = hydra70,  0.00, 0.90, 2.54,   0.0, 0.0, true, 1, 0,-60,60, 0,25
AddWeapon = m134,     1.48, 0.40, 1.54,   1.0, 0.0
AddWeapon = m134,    -1.48, 0.40, 1.54,  -1.0, 0.0
AddTurretWeapon = hydra70,  0.00, 0.90, 2.54,   0.0, 0.0, true, 1, 0,-60,60, 0,25
; Add a weapon (filename must match the extensionless file in the weapons folder).
; Consecutively adding the same weapon (e.g., m134) is treated as a single weapon with multiple firing points.
; Parameter order: Weapon config name, Position (X,Y,Z), Rotation angles (Horizontal, Vertical), Usable by driver, Seat, Default horizontal angle, Min horizontal angle, Max horizontal angle, Min pitch angle, Max pitch angle.
;
; Seat: 1=Seat 1, 2=Seat 2, and so on.
; Parameter combination explanation:
;  true,2 → Usable by player in seat 2, usable by driver if seat 2 is empty.
;  false,2 → Only usable by player in seat 2.
;  false,1 → Only usable by driver (not recommended).
;  true,1 → Only usable by driver.
; Defaults to true,1 if omitted.
;
; AddTurretWeapon differs from AddWeapon only in that the firing point rotates with the turret.

AddSearchLight      = 0.71,  -0.02,  0.02,   0x50FFFFFF,   0x10FFFFC0,    60.0, 20.0,       0,   0
AddFixedSearchLight = 0.71,  -0.02,  0.02,   0x50FFFFFF,   0x10FFFFC0,    60.0, 20.0,       0,   0
AddSteeringSearchLight = -0.52,0.90, 1.76,   0x50FFFFFF,   0x00FFFFC0,    27.0, 15.0,       5,   0,     45
;AddSearchLight     = Coord X,Y,Z,   Start color, End color,  Distance, End radius, Horizontal angle, Pitch angle, Rudder angle
; AddSearchLight      : Dynamic searchlight (rotates with occupant's view).
; AddFixedSearchLight : Fixed-direction searchlight.
; AddSteeringSearchLight : Fixed light that rotates with wheel direction (rudder angle should match wheel turn angle).

AddPartLightHatch =  0.32, 0.23, 1.83,   -1,0,-0.024, 90
;AddPartLightHatch= Coord X,Y,Z, Rotation axis X,Y,Z, Rotation angle -1800~1800
; Add a part that only extends when the searchlight is turned on.
; ★Important: AddSearchLight or AddFixedSearchLight must be set first.

AddRecipe = " Y ",  "YXY",  " YD",  X, iron_block, Y, iron_ingot, D,dye,2
AddRecipe ="YXY", X, mcheli:ah-6, Y, redstone
AddShapelessRecipe = iron_block, iron_ingot, dye,2
; Add crafting recipe (multiple AddRecipe lines can add recipes).
; 3 characters inside "" correspond to horizontal arrangement on the crafting table.
; (Format same as Forge's GameRegistry.addRecipe)
; Detailed example:
; X = iron block name
; Y = iron ingot item name
; D = green dye item name (items with damage value need the damage value appended to the name)
; Item name reference: http://minecraft.gamepedia.com/Data_values
; Vanilla items can omit the "minecraft:" prefix.
; MOD items need to specify the MOD name (e.g., mcheli:ah-6).
; AddShapelessRecipe adds a shapeless crafting recipe.

FlareType = 1
; Flare/Decoy type:
; 0=None
; 1=Normal
; 2=For large aircraft
; 3=Sideways ejection
; 4=Forward ejection
; 5=Downward ejection
; 10=Tank smoke grenade

Float  = true
; Enable floating.

FloatOffset = -1.0
; Floating height offset (can be negative).

SubmergedDamageHeight = 2
; Water contact below this height does not cause damage (unit: blocks).

MaxHP = 100
; Hit Points / Durability.

ArmorDamageFactor = 0.5
; Vehicle damage coefficient (1.0=100%, 0.5=50%).

ArmorMinDamage = 5
; Minimum damage threshold (damage below this value is ignored).

ArmorMaxDamage = 500
; Maximum damage cap (damage exceeding this is calculated as this value).

InventorySize = 18
; Vehicle inventory size (must be a multiple of 9).

DamageFactor = 0.2
; Player damage coefficient (0.2=takes 20% damage).
; Note: Vehicle takes damage simultaneously when the player is damaged.

Sound = heli
; Sound file when throttle is increased (corresponds to sounds/heli.ogg).

UAV = true
SmallUAV = true
; true=Drone (cannot enter pilot seat).
; UAV=true: Large drone (cannot be controlled by handheld terminal).
; SmallUAV=true: Small drone (can be controlled by handheld terminal).
; Note: Drone control station can control all types, handheld terminal only for small drones.

TargetDrone = true
; Only for planes: true=Unmanned target drone (cannot enter pilot seat).
; Can only be spawned by a drone control station, automatically flies low altitude circles after spawning.

OnGroundPitch = angle
; Pitch angle when parked on ground (e.g., Zero fighter nose up on ground).

AddPartHatch = Position X,Y,Z, Rotation axis X,Y,Z, Rotation angle 0~180
; Add a hatch that opens/closes with Z key.
; Model naming: vehiclename_hatch?.obj (? starts from 0).
; If model is not found, it won't be displayed (model is optional if no display is needed).

AddPartSlideHatch = Movement X,Y,Z
; Add a sliding hatch (model naming rule same as AddPartHatch).

AddPartCamera = Coord X,Y,Z, Horizontal link, Pitch link
; Add a part that always faces the player.
; Model naming: vehiclename_camera?.obj.

AddPartRotation = 0.00, 9.00, -31.17,  0,-1,0,       1.3,      false
; AddPartRotation = Position X,Y,Z,        Rotation axis X,Y,Z,   Rotation speed,  Continuous rotation
; Add a periodically rotating part.

AddPartWeapon        = m230,       false, true, true,  -2.51,  1.29,  -1.51
AddPartWeapon        = m102_105mm, false, true, true,  -2.51,  1.29,  -1.51, 1.00
AddPartWeapon        = rehinmetall_apfsds / rehinmetall_he, false, true, false,  0.00, 2.10, 0.00, 0
AddPartTurretWeapon  = mg7_62mm,   false, true, true,  -0.83,  3.39,  -0.57, 0
AddPartRotWeapon     = m134_r50,   false, true, true,  -1.825, 1.475, -0.25, 1,0,0
AddPartWeaponChild   = false, true, 0.00, 0.5, 3.00
AddPartWeaponMissile = aim120,     false, false,false, -2.51,  1.29,  -1.51
; Helicopter/Plane weapon part settings.
; AddPartWeapon = Linked weapon name (none for none), Hidden in gunner mode?, Horizontal link, Pitch link, Rotation coord X,Y,Z, Recoil distance
; AddPartRotWeapon = Linked weapon name, Hidden in gunner mode?, Horizontal link, Pitch link, Rotation coord X,Y,Z, Rotation axis X,Y,Z
; AddPartWeaponChild = Horizontal link, Pitch link, Rotation coord X,Y,Z
; Changes with the weapon angle of AddWeapon (weapon names separated by /).
; Recoil distance is the backward movement for cannons.
; AddPartRotWeapon is for rotary barrel guns (rotates when firing).
; Model naming: vehiclename_weapon?.obj
;
; AddPartWeaponChild is added as a child part of AddPartWeapon.
; Must be defined immediately after AddPartWeapon.
; Model naming: vehiclename_weapon?_0.obj (? is the parent part number).
;
; AddPartWeaponMissile is hidden when the weapon is not ready (e.g., missiles/bombs).

AddPartWeaponBay = Weapon name, Position X,Y,Z, Rotation axis X,Y,Z, Rotation angle 0~180
; Add a rotating weapon bay.
AddPartSlideWeaponBay = Weapon name, Movement X,Y,Z
; Add a sliding weapon bay.
; Model naming: vehiclename_wb?.obj.

AddPartCanopy = Position X,Y,Z, Rotation axis X,Y,Z, Rotation angle 0~180
; Add a rotating canopy.
AddPartSlideCanopy = Movement X,Y,Z
; Add a sliding canopy.
; Model naming: vehiclename_canopy?.obj (can add multiple).
; Compatibility note: Omitting the number defaults to _canopy0.obj.

AddPartThrottle = Position X,Y,Z,  Rotation axis X,Y,Z,  Rotation angle 0~180,  Movement X,Y,Z
; Add a part that rotates/moves linked to the throttle.
; Items before rotation angle are required.

AddPartLG = Position X,Y,Z, Rotation axis X,Y,Z, Rotation angle 0~180 [, Rotation axis X,Y,Z, Rotation angle 0~180]
AddPartLGRev = Position X,Y,Z, Rotation axis X,Y,Z, Rotation angle 0~180 [, Rotation axis X,Y,Z, Rotation angle 0~180]
AddPartSlideRotLG = Movement X,Y,Z,  Position X,Y,Z, Rotation axis X,Y,Z, Rotation angle 0~180
AddPartLGHatch = Position X,Y,Z, Rotation axis X,Y,Z, Rotation angle 0~180 [, Rotation axis X,Y,Z, Rotation angle 0~180]
; Add landing gear (automatically retracts when taking off).
; Model naming: vehiclename_lg?.obj.
; AddPartLGRev has the opposite action of AddPartLG.
; AddPartLGHatch only opens when the landing gear is folding/unfolding.
;
; Action explanation:
; AddPartLG      Retract: 0°→90°.
; AddPartLGRev   Retract: 90°→0°.
; AddPartSlideRotLG Retract: 0°→90°.
; AddPartLGHatch Retract: 0°→90°→0°.

TrackRollerRot = 30
; Track roller rotation speed (negative value reverses, but not recommended).

AddTrackRoller = -1.72,  0.77,  5.04
; Add a track roller (only coordinates needed, X negative=right side, positive=left side).
; Can be set independently of tracks.

AddCrawlerTrack = false, 0.37, -2.09,  1.03/-3.41, 0.72/-3.57, 0.37/-3.42, -0.15/-2.55, -0.25/-2.16, -0.25/3.88, -0.13/4.21, 0.52/5.29, 0.78/5.39, 1.03/5.28, 1.10/5.04, 1.15/-3.12
;AddCrawlerTrack = Track direction,  Segment spacing, Track X pos, Rotation point Y/Z, ...
; Adjust the direction parameter if track movement is abnormal.
; Test mode in the game shows set positions with red/blue points.

PartWheelRot = 40
; Wheel rotation speed (higher value = faster).

AddPartWheel     = -1.05, 0.157, 1.965,  30
; Add wheel     X,Y,Z coord,  Max turn angle.
AddPartWheel     =  0.68,  0.19,  1.20,  30,   0.0, 1.0, 0.2,   0.68, 0.19, 0.70
; Add wheel     X,Y,Z coord,  Turn angle, Rotation axis X,Y,Z,    Rotation position X,Y,Z.
; Default rotation axis is (0,1,0) if omitted.

AddPartSteeringWheel =  -0.54, 0.88,  0.48,   0.0,     1.0, -1.7,  130
; Add steering wheel        X,Y,Z coord,   Rotation axis X,Y,Z,   Max rotation angle.

ThrottleUpDown = 1.0
ThrottleUpDownOnEntity = 2.0
; Throttle response coefficient (lower value = slower takeoff).
;
; ThrottleUpDownOnEntity is the response coefficient when the vehicle is carried on another entity (default 2.0).
; Calculation formula:
; ThrottleUpDown * Carrying entity speed * ThrottleUpDownOnEntity → Throttle sensitivity.
; Example: When ThrottleUpDownOnEntity=2.0 and carried on a minecart (max speed≈1.7)
;       1.7 * 2.0=3.4 → Only 1/3 the distance is needed to take off.

AutoPilotRot = -0.4
; Auto-turn angle (higher value = smaller turn radius).
; 0=Straight.
; Negative value=Left turn, Positive value=Right turn.

ConcurrentGunnerMode = true
; Allow entering gunner mode even when the 2nd seat is occupied.

Regeneration = true
; Occupants in the 2nd seat and beyond automatically regenerate health.

ParticlesScale = 0.1
; Size of particle effects like dust (higher value = more noticeable effect).

FuelSupplyRange = 25
; Range for supplying fuel to other vehicles (unit: meters).
; Own fuel is not consumed when supplying.
; Cannot supply itself.

AmmoSupplyRange = 35
; Range for supplying ammo to other vehicles (unit: meters).
; Own ammo is not consumed when supplying.
; Cannot supply itself.

MaxFuel         = 600
; Maximum fuel capacity.
FuelConsumption = 0.5
; Fuel consumption per second.
; Endurance (seconds) = Max fuel capacity / Consumption per second.
; 600 / 0.5 = 1200 seconds.

Stealth = 0.5
; Stealth (0.0~1.0, default 0.0).
; Higher value = harder to lock onto by missiles (increases lock time, shortens lock range).

SmoothShading = false
; Smooth shading toggle.
; false=Flat shading (sharp edges).
; true=Smooth shading (softened edges).
; Note: SmoothShading=false in mcheli.cfg disables smooth shading globally.

HideEntity = false
; Whether to hide occupant models.
; true=Hide.
; false=Show.

EntityWidth  = 0.9
EntityHeight = 0.9
; Occupant model render size (width/height, range -100.0~100.0).
; 0.5=Half size.

EntityPitch = 45
EntityRoll  = 20
; Occupant model render angle (-360~360).

CanRide = false
; Whether riding is allowed.
; true=Allowed (default).
; false=Prohibited.

BoundingBox =  Collision box center X,Y,Z,  Width, Height, Damage multiplier
; Add a collision box.
; Only affected by this MOD's machine guns/missiles.
; Does not collide with blocks/entities.
; Enable TestMode in MOD options to display.
; Damage multiplier defaults to 1.0 (0.5=half damage, 3.0=triple damage).

Category = W.A
; Vehicle category (only used for creative mode inventory sorting).

CanMoveOnGround = false
CanRotOnGround  = false
; Ground movement/rotation prohibition.
;  CanMoveOnGround: Prohibit ground movement.
;  CanRotOnGround: Prohibit ground rotation.

EnableParachuting = true
; Enable parachuting (only for players in seat 3 and beyond, press Space to parachute).
MobDropOption  = 0.0, 0.0, -11.5,  10
; Occupant drop settings = Drop point X,Y,Z, Drop interval (1/20 second).

RotorSpeed = 50.0
; Rotor speed (higher value = faster, negative value reverses but not recommended).

;***********************************************************************************
■ Helicopter Exclusive Settings
;***********************************************************************************

;Requires four files (all lowercase):
;  helicopters folder: Configuration file.
;  models/helicopters: Model.
;  textures/helicopters: Texture.
;  textures/items: Item texture.

EnableFoldBlade = false
; Rotor blade folding function (true=enabled).

AddRotor= 6, 60,  0.00,  3.35,  0.00,  0.0, 1.0, 0.0, true
AddRotor= 2, 60,  0.50,  1.90, -6.55,  1.0, 0.0, 0.0
; Add rotor (unlimited number).
; First one in this example is main rotor, second is tail rotor.
; Only the first rotor can be folded.
; Parameters: Number of blades, Angle between blades, Position X,Y,Z, Rotation axis X,Y,Z, Foldable.
; Model naming: vehiclename_rotor?.obj.
;
; ※ Legacy AddRotorOld is deprecated.

AddRepellingHook =  0.60, 2.75, -14.21, 30
; Rappelling hook settings = Hook coordinates X,Y,Z, Deployment interval.

;***********************************************************************************
■ Fighter Plane Exclusive Settings
;***********************************************************************************

;Requires four files (all lowercase):
;  planes folder: Configuration file.
;  models/planes: Model.
;  textures/planes: Texture.
;  textures/items: Item texture.

AddPartRotor = Position X,Y,Z, Rotation axis X,Y,Z, Rotation angle (-180~180)
; Add rotor (rotates during VTOL).
; Model naming: vehiclename_rotor?.obj.
AddBlade = Number of blades, Angle between blades, Position X,Y,Z, Rotation axis X,Y,Z
; Must be added after AddPartRotor.
; Model naming: vehiclename_blade?.obj.

AddPartWing = Position X,Y,Z, Rotation axis X,Y,Z, Rotation angle 0~180
; Add foldable main wing.
; Model naming: vehiclename_wing?.obj.
AddPartPylon = Position X,Y,Z, Rotation axis X,Y,Z, Rotation angle 0~180
; Add foldable pylon.
; Model naming: vehiclename_wing?_pylon?.obj.
; Must be added after AddPartWing.
; Example:
; AddPartWing  → Model: vehiclename_wing0.obj
; AddPartPylon → Model: vehiclename_wing0_pylon0.obj / wing0_pylon1.obj

PivotTurnThrottle = 0.0
; Movement amount during ground turning.
; 0=Pivot turn, >0=Turn while moving.
; Tank setting suggestions:
;  Neutral steer=0
;  Skid steer>0

EnableBack = true
; Allow reversing.

VariableSweepWing = true
SweepWingSpeed = 1.2
; Variable-sweep wing settings (requires AddPartWing).
; VariableSweepWing=true: Wing can be adjusted in air.
; SweepWingSpeed=1.2: Speed when wings are folded.

AddPartNozzle = Position X,Y,Z, Rotation axis X,Y,Z, Rotation angle 0~180
; Add engine nozzle (rotates during VTOL).
; Model naming: vehiclename_nozzle?.obj.
; Particle size controlled by ParticlesScale.

EnableVtol = true
; Whether to enable VTOL functionality.
DefaultVtol = true
; Default state when VTOL is enabled (true=VTOL automatically enabled on ground).
VtolYaw = 0.3
; Horizontal turn amount in VTOL mode.
VtolPitch = 0.3
; Pitch turn amount in VTOL mode.

EnableEjectionSeat = true
; Ejection seat toggle.
; true=Adds ejection seat button to GUI.
; 1-seat vehicles support 1, 2-seat vehicles support 2.

AddParticleSplash  =  1.0,  0.97,   13.19,      3,     9.0,   1.1,        20, 0.30, -0.03
;AddParticleSplash = Coord X,Y,Z,  Particle count,  Size,  Speed,  Duration, Rise speed, Gravity
; Generate splash particles when moving on water.
; Unrelated to EnableSeaSurfaceParticle.

EnableSeaSurfaceParticle = true
; Whether to generate splashes when flying over sea surface.
; Size affected by ParticlesScale (recommended 0.7).
; Note: Unrelated to AddParticleSplash.

;***********************************************************************************
■ Ground Vehicle Exclusive Settings
;***********************************************************************************

;Requires four files (all lowercase):
;  vehicles folder: Configuration file.
;  models/vehicles: Model.
;  textures/vehicles: Texture.
;  textures/items: Item texture.

AddPart = Parameter 1, Parameter 2, Parameter 3, Parameter 4, Position X,Y,Z
; Add a part that rotates with the player.
; Parameter 1: Hide in first-person view? (true=show).
; Parameter 2: Link horizontally? (true=link).
; Parameter 3: Link with pitch? (true=link).
; Parameter 4: Part type (0=Normal,1=Rotate when firing,2=Recoil when firing).
; Model naming: vehiclename_part?.obj.
AddChildPart = Parameter 1, Parameter 2, Parameter 3, Parameter 4, Position X,Y,Z
; Add a child part (must be after AddPart).
; Model naming: vehiclename_part?_#.obj (# starts from 0).
; Example:
; AddPart     → vehiclename_part0.obj
; AddChildPart → vehiclename_part0_0.obj / part0_1.obj

; RotationPitchMax/Min are legacy parameters, do not use.

;***********************************************************************************
■ Tank Exclusive Settings
;***********************************************************************************

;Requires four files (all lowercase):
;  tanks folder: Configuration file.
;  models/tanks: Model.
;  textures/tanks: Texture.
;  textures/items: Item texture.

DefaultFreelook = true
; Enable free look immediately after entering vehicle (mainly for tanks).

OnGroundPitchFactor = 2.0
OnGroundRollFactor  = 1.3
; Terrain adaptation tilt speed.
; Higher value = faster tilting.
; Recommended higher for fast vehicles, lower for slow vehicles.
; Too high causes screen shake, too low gets stuck in blocks.

CameraRotationSpeed = 25
; Camera rotation speed (for tanks, can be used to limit turret rotation speed).

WeightType = Tank
; Weight type: Tank / Car / Unknown.
; Tank: No self-damage when hitting mobs, destroys more blocks.
; Car: Self-damage when hitting mobs, destroys fewer blocks.
; Block destruction rules set in mcheli.cfg.

WeightedCenterZ = 0.0
; Center of gravity Z coordinate (affects terrain adaptation tilt).
; ※ Effect is unstable, disable if unsuitable.

SetWheelPos =  1.75,  -0.24,  4.85, 3.02, 1.44, -1.54, -2.91
;SetWheelPos =  X coord, Y coord,  Z coord1, Z coord2...
; Set ground contact points (vehicle tilts based on these).
; Negative X values need not be set.
; ★ Y coordinate strongly recommended to be fixed at -0.24.

======================================Updated 2025.10.8, parameters below are added by MCHeli-Reforged=====================================
    /**
     * Radar Type
     */
radarType = MODERN_AA
;Modern Anti-Air Radar
radarType = EARLY_AA
;Early Anti-Air Radar
radarType = MODERN_AS
;Modern Air-to-Surface Radar
radarType = EARLY_AS
;Early Air-to-Surface Radar
;Default=None

The above radar parameters are case-sensitive.

nameOnModernAARadar = "?"
;Name displayed for this vehicle on Modern Anti-Air Radar.
;Default=?

nameOnEarlyAARadar = "?"
;Name displayed for this vehicle on Early Anti-Air Radar.
;Default=?

nameOnModernASRadar = "?"
;Name displayed for this vehicle on Modern Air-to-Surface Radar.
;Default=?

nameOnEarlyASRadar = "?"
;Name displayed for this vehicle on Early Air-to-Surface Radar.
;Default=?

explosionSizeByCrash = 5
;Explosion radius when the vehicle is destroyed.
;Default=5

throttleDownFactor = 1
;Reverse speed multiplier (Recommended value 3, so reverse speed is about half of forward speed. But reverse speed is also affected by motionfactor).
;Default=1

haschaff = false
;Whether it has chaff.
;Default=false

chaffUseTime = 100
;Chaff effect duration.
;Default=None

chaffWaitTime = 400
;Chaff cooldown duration.
;Default=None

hasmaintenance = false
;Whether it has a maintenance system.
;Default=false

maintenanceUseTime = 20
;Maintenance system effect duration (Duration is the health regeneration percentage).
;Default=None

maintenanceWaitTime = 300
;Maintenance system cooldown duration.
;Default=None

engineShutdownThreshold = 20
;Vehicle crippling threshold, engine shuts down if health falls below this percentage.
;Default=None

hasaps = false
;Whether it has an Active Protection System.
;Default=false

apsUseTime = 100
;APS effect duration (When active, can intercept Rocket and Missile type weapons).
;Default=100

apsWaitTime = 400
;APS cooldown duration.
;Default=400

apsRange = 8
;APS range.
;Default=8

enableRWR = false
;Whether it has a Radar Warning Receiver.
;Default=false

hudType = 0
;HUD custom field, used to indicate the vehicle's HUD.
;Default=None

weaponGroupType = 0
;HUD custom field, used to indicate the vehicle's weaponGroupType.
;Default=None

armorExplosionDamageMultiplier = 1.0
;Vehicle explosion damage multiplier, final explosion damage = explosion damage * explosion multiplier.
;Default=1

;Currently, MCH-R supports the original MCH collision boxes and adds two new types. The syntax is as follows:
;The first type is BoundingBox = {center_x}, {center_y}, {center_z}, {width}, {height}, {length}, {multiplier}, DEFAULT, {name}
;It generates a DEFAULT type collision box centered at center_x,center_y,center_z, with width, height, length as specified, damage multiplier, and hit display name.
;DEFAULT type collision boxes do not rotate with the turret. Example:
BoundingBox = 0.0, 1.21, 3.6, 4.684, 0.8871, 1.5, 0.4, DEFAULT, Upper Glacis
;This example creates a normal collision box at 0.0, 1.21, 3.6, with width/height/length 4.684, 0.8871, 1.5, damage multiplier 0.4, showing hit location as 'Upper Glacis'.

;The second type is BoundingBox = {center_x}, {center_y}, {center_z}, {width}, {height}, {length}, {multiplier}, TURRET, {name}
;It generates a TURRET type collision box centered at center_x,center_y,center_z, with width, height, length, damage multiplier, and hit display name.
;TURRET type collision boxes rotate with the turret around 0,y,0 (we recommend setting the turret rotation position as 0,y,0). Example:
BoundingBox = 0.0, 2.16, -0.44, 4.1, 1, 5.4, 0.4, TURRET, Turret Front
;This example creates a turret collision box at 0.0, 2.16, -0.44, with width/height/length 4.1, 1, 5.4, damage multiplier 0.4, showing hit location as 'Turret Front', which rotates with the turret.

; ★ 重要 ★
; 配置文件和模型可在不关闭Minecraft的情况下重新加载。
; [ 进入载具 → 按R键打开补给界面 → MOD选项 → 开发 → 重新加载飞行器设置 ]
; 纹理和音效需使用Minecraft原生功能重载，而非通过直升机MOD。
; [ 按Esc打开游戏菜单 → 设置 → 资源包 → 完成 ]

;***********************************************************************************
■ 直升机/战斗机/地面载具/车辆配置文件的通用设置
;***********************************************************************************

DisplayName = AH-6 杀手蛋
; 显示名称 ※请勿使用全角字符，仅限半角英数字及符号

AddDisplayName = ja_JP, AH-6 キラ－エッグ
; 手持物品时显示的名称
; ※ 使用日语全角字符时，文件编码必须为UTF-8

ItemID = 28801
; 物品ID (在Minecraft中实际使用时将+256)
; ※ 1.7.2+版本不再使用ItemID，但若需兼容1.6.4及更早版本则必须设置

Invulnerable = true
; 载具无敌模式
; 建议在多人游戏中用于基地防御武器

CreativeOnly = true
; 仅创造模式玩家可放置或回收物品

AddTexture = sh60-us-1
AddTexture = sh60-jp-1
AddTexture = sh60-jp-2
; 附加纹理（可添加多个）
; 默认使用与配置文件同名的png文件
; 此处添加额外纹理（无需扩展名）

ThirdPersonDist = 12
; 第三人称视角默认距离
; 直升机MOD中可用PageUp/Down以4方块为单位调整距离，建议设为4的倍数

CameraPosition = 0.0, 1.1, 3.7
CameraPosition = 0.0, 1.1, 3.7, false
CameraPosition = 0.0, 1.1, 3.7, true, 30, 45
; 摄像机坐标
; 多重设置时可通过H键切换不同视角
; 第1-3位：坐标
; 第4位设为true时始终锁定摄像机视角
; 第5位：水平角度
; 第6位：垂直角度

CameraZoom = 3
; 摄像机最大缩放倍数

HUD = heli, heli_gnr, none, gunner
; 各座位使用的HUD配置文件名称
; 本例中：驾驶席使用heli.txt，第2席用heli_gnr.txt，第3席无HUD，第4席用gunner.txt
; 若设置数量少于座位数，未指定的座位将使用以下默认配置：
; 未设置时默认配置：
; 直升机：HUD = heli, heli_gnr, gunner, gunner, gunner, gunner...
; 固定翼：HUD = plane, plane, gunner, gunner, gunner, gunner...
; 地面载具：HUD = vehicle
;
; ※ 仅驾驶席在炮手模式下会使用第2席的HUD配置
;    即使单人载具，若启用炮手模式也需设置第2席
;    例如：HUD = heli, heli_gnr

EnableGunnerMode = true
; 是否启用炮手模式切换（true=启用，false=禁用）

EnableNightVision = true
; 是否启用夜视模式切换（true=启用，false=禁用）

EnableEntityRadar = false
; 是否启用雷达（true=启用，false=禁用）

Speed = 0.6
; 载具速度（值越大越快）

MotionFactor = 0.96
; 载具移动减速系数（范围0.0~1.0，值越小减速越强）

Gravity = -0.04
; 载具重力设置（负值表示下落）

GravityInWater = -0.04
; 水中重力设置（负值表示下落）

StepHeight = 2.5
; 可跨越的方块高度

MobilityYaw
MobilityYawOnGround
; 水平转向灵敏度（值越大机动性越强）
; MobilityYawOnGround 仅影响地面，不影响水面
MobilityRoll
; 滚转灵敏度（值越大滚转越快）
MobilityPitch
; 俯仰灵敏度（值越大机动性越强；地面载具表示俯仰角上下限）
MinRotationPitch
MaxRotationPitch
; 范围 MinRotationPitch -80~0
; 范围 MaxRotationPitch 0~80
; 俯仰角限制（最小/最大）
; ※ 直升机/战斗机启用此设置将同时限制滚转

MinRotationRoll
MaxRotationRoll
; 滚转角限制（最小/最大）
; 范围 MinRotationRoll -80~0
; 范围 MaxRotationRoll 0~80
; ※ 直升机/战斗机启用此设置将同时限制俯仰

UnmountPosition = 3.0, 1.0, -2.0
; 下机时的坐标

AddSeat =-0.45,  0.80,  1.20
AddSeat = 0.45, -0.50,  1.20
AddSeat =-0.90, -0.50,  0.20
AddSeat = 0.90, -0.50,  0.20, true
; 添加座位 ※除无人机外必须至少1个座位
; 第1个为驾驶席
; 参数为坐标(X,Y,Z)
; 第4个参数决定座位是否随驾驶员朝向旋转（主要用于坦克炮塔）

AddGunnerSeat = -0.45, 0.80, 1.20,   0.0, 2.00, -1.01,   true
AddGunnerSeat = -0.45, 0.80, 1.20,   0.0, 2.00, -1.01,   true, -60, 78, true
; AddGunnerSeat=座位X,Y,Z,  摄像机X,Y,Z,  可切换视角,  摄像头上限(-90~0), 摄像头下限(0~90), 座位随炮塔旋转
; 添加炮手座位
; 此座位玩家默认为摄像机视角
; 参数含座位坐标和摄像机位置（摄像机位置可省略，默认使用CameraPosition）
; 视角切换设为false时锁定摄像机视角，true时可用H键切回玩家视角
; 第10个参数控制座位是否随驾驶员朝向旋转

AddFixRotSeat = -0.45,  0.80,  1.20, 0.0,2.00,-1.01,  true,  -50, 40
; AddFixRotSeat=座位X,Y,Z,  摄像机X,Y,Z,  可切换视角,  水平固定角度, 垂直固定角度
; 添加固定视角座位
; 与AddGunnerSeat类似，但摄像机角度固定不可调
; 设置固定角度后无法用鼠标调整视角（可用Ctrl键切换自由视角）

; ★★★★★
; 载具搭载功能需满足：
; ・搭载方指定被搭载载具（AddRack）
; ・被搭载方指定搭载方挂架编号（RideRack）
; 任一条件满足即可生效

AddRack = container,                 0.0, 1.4, -4.7,  0.0, 1.0, -16.1
AddRack = container / ah-64,         0.0, 1.4, -4.7,  0.0, 1.0, -16.1,  5.0, 20
AddRack = helicopter/vehicle / t-4,  0.0, 1.4, -4.7,  0.0, 1.0, -16.1,  5.0, 100000,  0.0, 0.0
; ■ 搭载方设置
; AddRack = 
;  参数1：可搭载实体名
;  参数2-4：挂架坐标X,Y,Z（在载具上的位置）
;  参数5-7：出入口坐标X,Y,Z（实体需靠近此坐标才能装载/卸载）
;  参数8：入口半径（可省略）
;  参数9：开伞高度（设极大值可禁用降落伞）
;  参数10：被载实体水平角度
;  参数11：被载实体垂直角度
; 添加可搭载容器/直升机等的挂架
;  实体名可用 container/helicopter/plane/vehicle 或直接指定载具名（如ah-64），用/分隔

RideRack = c5, 1
; ■ 被搭载方设置
; RideRack = 搭载载具名, 挂架编号（1~） 

ExclusionSeat = 15, 17
; 参数数量不限（需≥2）
; 设置互斥座位/挂架
; 例如 ExclusionSeat = 3,4,5 时：
;  3号位有实体时，4/5号位不可载实体
;  4号位有实体时，3/5号位不可载实体
;  5号位有实体时，3/4号位不可载实体
;
; 座位/挂架编号规则：先按所有座位定义顺序编号，再编号挂架
; 示例配置顺序：
;  AddSeat  →1号
;  AddRack  →4号
;  AddGunnerSeat →2号
;  AddRack  →5号
;  AddSeat  →3号
;  AddRack  →6号
; 建议最后定义挂架以便编号清晰

TurretPosition = 0.0, 0.0, 0.25
; 炮塔旋转中心位置（非必要不建议修改）

AddWeapon = m230,     0.00, 0.90, 2.54,   0.0, 0.0, true, 2
AddWeapon = hydra70,  0.00, 0.90, 2.54,   0.0, 0.0, true, 1, 0,-60,60, 0,25
AddWeapon = m134,     1.48, 0.40, 1.54,   1.0, 0.0
AddWeapon = m134,    -1.48, 0.40, 1.54,  -1.0, 0.0
AddTurretWeapon = hydra70,  0.00, 0.90, 2.54,   0.0, 0.0, true, 1, 0,-60,60, 0,25
; 添加武器（文件名需匹配weapons文件夹内无扩展名文件）
; 连续添加相同武器（如m134）将视为单武器多发射点
; 参数顺序：武器配置名、位置(X,Y,Z)、旋转角(水平,垂直)、驾驶员可用性、座位、默认水平角、最小水平角、最大水平角、最小俯仰角、最大俯仰角
;
; 座位：1=1号位，2=2号位，依此类推
; 参数组合说明：
;  true,2 → 2号位玩家可用，2号位无人时驾驶员可用
;  false,2 → 仅2号位玩家可用
;  false,1 → 仅驾驶员可用（不推荐）
;  true,1 → 仅驾驶员可用
; 省略时默认为 true,1
;
; AddTurretWeapon与AddWeapon区别仅在于发射点随炮塔旋转

AddSearchLight      = 0.71,  -0.02,  0.02,   0x50FFFFFF,   0x10FFFFC0,    60.0, 20.0,       0,   0
AddFixedSearchLight = 0.71,  -0.02,  0.02,   0x50FFFFFF,   0x10FFFFC0,    60.0, 20.0,       0,   0
AddSteeringSearchLight = -0.52,0.90, 1.76,   0x50FFFFFF,   0x00FFFFC0,    27.0, 15.0,       5,   0,     45
;AddSearchLight     = 坐标X,Y,Z,   起点颜色, 终点颜色,  距离, 末端半径, 水平角, 俯仰角, 舵角
; AddSearchLight      ：动态探照灯（随乘员视角旋转）
; AddFixedSearchLight ：固定方向探照灯
; AddSteeringSearchLight ：随轮胎方向旋转的固定灯（舵角建议匹配轮胎转向角）

AddPartLightHatch =  0.32, 0.23, 1.83,   -1,0,-0.024, 90
;AddPartLightHatch= 坐标X,Y,Z, 旋转轴X,Y,Z, 旋转角度 -1800~1800
; 添加探照灯开启时才会展开的部件
; ★重要：必须先设置AddSearchLight或AddFixedSearchLight

AddRecipe = " Y ",  "YXY",  " YD",  X, iron_block, Y, iron_ingot, D,dye,2
AddRecipe ="YXY", X, mcheli:ah-6, Y, redstone
AddShapelessRecipe = iron_block, iron_ingot, dye,2
; 添加合成配方（多行AddRecipe可增加配方）
; ""内3字符对应工作台横向排列
; (格式同Forge的GameRegistry.addRecipe)
; 示例详解：
; X = 铁块名
; Y = 铁锭物品名
; D = 绿色染料物品名（带损伤值的物品需在名称后加损伤值）
; 物品名参考：http://minecraft.gamepedia.com/Data_values
; 原版物品可省略"minecraft:"前缀
; MOD物品需指定MOD名（如 mcheli:ah-6）
; AddShapelessRecipe 添加无序合成配方

FlareType = 1
; 诱饵弹类型：
; 0=无
; 1=普通
; 2=大型机用
; 3=横向抛洒
; 4=向前抛洒
; 5=向下抛洒
; 10=坦克烟雾弹

Float  = true
; 启用漂浮

FloatOffset = -1.0
; 漂浮高度偏移（可为负值）

SubmergedDamageHeight = 2
; 低于此高度的水接触不造成伤害（单位：方块）

MaxHP = 100
; 耐久值

ArmorDamageFactor = 0.5
; 载具受伤系数（1.0=100%，0.5=50%）

ArmorMinDamage = 5
; 最小伤害阈值（低于此值不受伤害）

ArmorMaxDamage = 500
; 最大伤害上限（超出部分按此值计算）

InventorySize = 18
; 载具物品栏大小（需为9的倍数）

DamageFactor = 0.2
; 玩家受伤系数（0.2=承受20%伤害）
; 注：玩家受伤时载具同步受损

Sound = heli
; 油门提升时的音效文件（对应sounds/heli.ogg）

UAV = true
SmallUAV = true
; true=无人机（无法进入驾驶席）
; UAV=true：大型无人机（不可用手持终端控制）
; SmallUAV=true：小型无人机（可用手持终端控制）
; 注：无人机控制站可控制所有类型，手持终端仅限小型机

TargetDrone = true
; 仅战斗机有效：true=无人靶机（无法进入驾驶席）
; 仅可通过无人机控制站生成，生成后自动低空盘旋

OnGroundPitch = 角度
; 地面停放时的俯仰角（如零式战斗机地面机头上扬）

AddPartHatch = 位置X,Y,Z, 旋转轴X,Y,Z, 旋转角度0~180
; 添加Z键开闭的舱门
; 模型命名：载具名_hatch?.obj（?从0开始）
; 找不到模型时不显示（若无显示需求可不做模型）

AddPartSlideHatch = 移动量X,Y,Z
; 添加滑动式舱门（模型命名规则同AddPartHatch）

AddPartCamera = 坐标X,Y,Z, 水平联动, 俯仰联动
; 添加始终朝向玩家的部件
; 模型命名：载具名_camera?.obj

AddPartRotation = 0.00, 9.00, -31.17,  0,-1,0,       1.3,      false
; AddPartRotation = 位置X,Y,Z,        旋转轴X,Y,Z,   转速,  是否持续旋转
; 添加周期性旋转部件

AddPartWeapon        = m230,       false, true, true,  -2.51,  1.29,  -1.51
AddPartWeapon        = m102_105mm, false, true, true,  -2.51,  1.29,  -1.51, 1.00
AddPartWeapon        = rehinmetall_apfsds / rehinmetall_he, false, true, false,  0.00, 2.10, 0.00, 0
AddPartTurretWeapon  = mg7_62mm,   false, true, true,  -0.83,  3.39,  -0.57, 0
AddPartRotWeapon     = m134_r50,   false, true, true,  -1.825, 1.475, -0.25, 1,0,0
AddPartWeaponChild   = false, true, 0.00, 0.5, 3.00
AddPartWeaponMissile = aim120,     false, false,false, -2.51,  1.29,  -1.51
; 直升机/战斗机武器部件设置
; AddPartWeapon = 关联武器名(none表示无), 炮手模式隐藏?, 水平联动, 俯仰联动, 旋转坐标X,Y,Z, 后坐距离
; AddPartRotWeapon = 关联武器名, 炮手模式隐藏?, 水平联动, 俯仰联动, 旋转坐标X,Y,Z, 旋转轴X,Y,Z
; AddPartWeaponChild = 水平联动, 俯仰联动, 旋转坐标X,Y,Z
; 随AddWeapon武器角度变化（武器名用/分隔）
; 后坐距离为火炮后坐位移
; AddPartRotWeapon用于转管机枪（开火时旋转）
; 模型命名：载具名_weapon?.obj
;
; AddPartWeaponChild 作为AddPartWeapon的子部件添加
; 必须紧接AddPartWeapon后定义
; 模型命名：载具名_weapon?_0.obj（?为父部件编号）
;
; AddPartWeaponMissile 在武器未就绪时隐藏（如导弹/炸弹）

AddPartWeaponBay = 武器名, 位置X,Y,Z, 旋转轴X,Y,Z, 旋转角度0~180
; 添加旋转开启的武器舱
AddPartSlideWeaponBay = 武器名, 移动量X,Y,Z
; 添加滑动开启的武器舱
; 模型命名：载具名_wb?.obj

AddPartCanopy = 位置X,Y,Z, 旋转轴X,Y,Z, 旋转角度0~180
; 添加旋转式座舱盖
AddPartSlideCanopy = 移动量X,Y,Z
; 添加滑动式座舱盖
; 模型命名：载具名_canopy?.obj（可添加多个）
; 兼容性说明：省略数字时默认使用_canopy0.obj

AddPartThrottle = 位置X,Y,Z,  旋转轴X,Y,Z,  旋转角度0~180,  移动量X,Y,Z
; 添加随油门联动旋转/移动的部件
; 旋转角度前为必填项

AddPartLG = 位置X,Y,Z, 旋转轴X,Y,Z, 旋转角度0~180 [, 旋转轴X,Y,Z, 旋转角度0~180]
AddPartLGRev = 位置X,Y,Z, 旋转轴X,Y,Z, 旋转角度0~180 [, 旋转轴X,Y,Z, 旋转角度0~180]
AddPartSlideRotLG = 移动量X,Y,Z,  位置X,Y,Z, 旋转轴X,Y,Z, 旋转角度0~180
AddPartLGHatch = 位置X,Y,Z, 旋转轴X,Y,Z, 旋转角度0~180 [, 旋转轴X,Y,Z, 旋转角度0~180]
; 添加起落架（起飞时自动收起）
; 模型命名：载具名_lg?.obj
; AddPartLGRev 与AddPartLG动作相反
; AddPartLGHatch 仅在起落架折叠/展开时开启
;
; 动作说明：
; AddPartLG      收起：0°→90°
; AddPartLGRev   收起：90°→0°
; AddPartSlideRotLG 收起：0°→90°
; AddPartLGHatch 收起：0°→90°→0°

TrackRollerRot = 30
; 履带轮转速（负值为反转，但不推荐）

AddTrackRoller = -1.72,  0.77,  5.04
; 添加履带轮（仅需坐标，X负值=右侧，正值=左侧）
; 可独立于履带设置

AddCrawlerTrack = false, 0.37, -2.09,  1.03/-3.41, 0.72/-3.57, 0.37/-3.42, -0.15/-2.55, -0.25/-2.16, -0.25/3.88, -0.13/4.21, 0.52/5.29, 0.78/5.39, 1.03/5.28, 1.10/5.04, 1.15/-3.12
;AddCrawlerTrack = 履带正反,  单节间距, 履带X位, 旋转点Y/Z, ...
; 履带运动异常时可调整正反参数
; 游戏测试模式会以红/蓝点显示设定位置

PartWheelRot = 40
; 轮胎转速（值越大越快）

AddPartWheel     = -1.05, 0.157, 1.965,  30
; 添加轮胎     X,Y,Z坐标,  最大转向角
AddPartWheel     =  0.68,  0.19,  1.20,  30,   0.0, 1.0, 0.2,   0.68, 0.19, 0.70
; 添加轮胎     X,Y,Z坐标,  转向角, 旋转轴X,Y,Z,    旋转位置X,Y,Z
; 省略旋转轴时默认(0,1,0)

AddPartSteeringWheel =  -0.54, 0.88,  0.48,   0.0,     1.0, -1.7,  130
; 添加方向盘        X,Y,Z坐标,  旋转轴X,Y,Z,   最大旋转角度

ThrottleUpDown = 1.0
ThrottleUpDownOnEntity = 2.0
; 油门响应系数（值越小起飞越慢）
;
; ThrottleUpDownOnEntity 为载具搭载在其他实体上时的响应系数（默认2.0）
; 计算公式：
; ThrottleUpDown * 搭载实体速度 * ThrottleUpDownOnEntity → 油门灵敏度
; 例如：ThrottleUpDownOnEntity=2.0时搭载矿车（最高速≈1.7）
;       1.7 * 2.0=3.4 → 仅需1/3距离即可起飞

AutoPilotRot = -0.4
; 自动转向角度（值越大转弯半径越小）
; 0=直行
; 负值=左转，正值=右转

ConcurrentGunnerMode = true
; 允许第2席有玩家时仍可进入炮手模式

Regeneration = true
; 第2席及之后的乘员自动回血

ParticlesScale = 0.1
; 沙尘等粒子效果尺寸（值越大效果越明显）

FuelSupplyRange = 25
; 为其他载具供油的范围（单位：米）
; 供油时自身燃料不减少
; 不可给自身供油

AmmoSupplyRange = 35
; 为其他载具补给弹药的范围（单位：米）
; 补给时自身弹药不减少
; 不可给自身补给

MaxFuel         = 600
; 最大燃料容量
FuelConsumption = 0.5
; 每秒燃料消耗量
; 续航时间(秒) = 最大燃料容量 / 每秒消耗量
; 600 / 0.5 = 1200秒

Stealth = 0.5
; 隐身性（0.0~1.0，默认0.0）
; 值越高越难被导弹锁定（延长锁定时间，缩短锁定距离）

SmoothShading = false
; 平滑着色开关
; false=平面着色（棱角分明）
; true=平滑着色（边缘柔化）
; 注：mcheli.cfg中SmoothShading=false将全局禁用平滑着色

HideEntity = false
; 是否隐藏乘员模型
; true=隐藏
; false=显示

EntityWidth  = 0.9
EntityHeight = 0.9
; 乘员模型渲染尺寸（宽/高，范围-100.0~100.0）
; 0.5=尺寸减半

EntityPitch = 45
EntityRoll  = 20
; 乘员模型渲染角度（-360~360）

CanRide = false
; 是否允许乘坐
; true=允许（默认）
; false=禁止

BoundingBox =  碰撞箱中心X,Y,Z,  宽度, 高度, 伤害倍率
; 添加碰撞箱
; 仅受本MOD机炮/导弹影响
; 不与方块/实体碰撞
; 在MOD选项开启TestMode可显示
; 伤害倍率默认1.0（0.5=半伤，3.0=三倍伤）

Category = W.A
; 载具分类（仅用于创造模式物品栏排序）

CanMoveOnGround = false
CanRotOnGround  = false
; 地面移动/旋转禁令
;  CanMoveOnGround：禁止地面移动
;  CanRotOnGround：禁止地面旋转

EnableParachuting = true
; 启用跳伞功能（仅限第3席及之后玩家按空格跳伞）
MobDropOption  = 0.0, 0.0, -11.5,  10
; 乘员投放设置 = 投放点X,Y,Z, 投放间隔（1/20秒）

RotorSpeed = 50.0
; 旋翼转速（值越大越快，负值为反转但不推荐）

;***********************************************************************************
■ 直升机专属设置
;***********************************************************************************

;需四文件（全小写）：
;  helicopters文件夹：配置文件
;  models/helicopters：模型
;  textures/helicopters：纹理
;  textures/items：物品纹理

EnableFoldBlade = false
; 旋翼折叠功能（true=启用）

AddRotor= 6, 60,  0.00,  3.35,  0.00,  0.0, 1.0, 0.0, true
AddRotor= 2, 60,  0.50,  1.90, -6.55,  1.0, 0.0, 0.0
; 添加旋翼（数量不限）
; 本例第1个主旋翼，第2个尾旋翼
; 仅第1个旋翼可折叠
; 参数：叶片数、叶片间角度、位置X,Y,Z、旋转轴X,Y,Z、是否可折叠
; 模型命名：载具名_rotor?.obj
;
; ※ 旧版AddRotorOld已弃用

AddRepellingHook =  0.60, 2.75, -14.21, 30
; 索降钩设置 = 钩坐标X,Y,Z, 投放间隔

;***********************************************************************************
■ 战斗机专属设置
;***********************************************************************************

;需四文件（全小写）：
;  planes文件夹：配置文件
;  models/planes：模型
;  textures/planes：纹理
;  textures/items：物品纹理

AddPartRotor = 位置X,Y,Z, 旋转轴X,Y,Z, 旋转角度(-180~180)
; 添加旋翼（VTOL时旋转）
; 模型命名：载具名_rotor?.obj
AddBlade = 叶片数, 叶片间角度, 位置X,Y,Z, 旋转轴X,Y,Z
; 必须在AddPartRotor后添加
; 模型命名：载具名_blade?.obj

AddPartWing = 位置X,Y,Z, 旋转轴X,Y,Z, 旋转角度0~180
; 添加可折叠主翼
; 模型命名：载具名_wing?.obj
AddPartPylon = 位置X,Y,Z, 旋转轴X,Y,Z, 旋转角度0~180
; 添加可折叠挂架
; 模型命名：载具名_wing?_pylon?.obj
; 必须在AddPartWing后添加
; 示例：
; AddPartWing  → 模型：载具名_wing0.obj
; AddPartPylon → 模型：载具名_wing0_pylon0.obj / wing0_pylon1.obj

PivotTurnThrottle = 0.0
; 地面转向时的移动量
; 0=原地转向，>0=转向时移动
; 坦克设置建议：
;  超信地旋回=0
;  信地旋回>0

EnableBack = true
; 允许倒车

VariableSweepWing = true
SweepWingSpeed = 1.2
; 变后掠翼设置（需AddPartWing）
; VariableSweepWing=true：空中可调节机翼
; SweepWingSpeed=1.2：机翼折叠时的速度

AddPartNozzle = 位置X,Y,Z, 旋转轴X,Y,Z, 旋转角度0~180
; 添加发动机喷口（VTOL时旋转）
; 模型命名：载具名_nozzle?.obj
; 粒子尺寸受ParticlesScale控制

EnableVtol = true
; 是否启用VTOL功能
DefaultVtol = true
; VTOL启用时的默认状态（true=地面自动启用VTOL）
VtolYaw = 0.3
; VTOL状态水平转向量
VtolPitch = 0.3
; VTOL状态俯仰转向量

EnableEjectionSeat = true
; 弹射座椅开关
; true=在GUI添加弹射座椅按钮
; 1座位载具支持1个，2座位载具支持2个

AddParticleSplash  =  1.0,  0.97,   13.19,      3,     9.0,   1.1,        20, 0.30, -0.03
;AddParticleSplash = 坐标X,Y,Z,  粒子数量,  尺寸,  速度,  持续时间, 上升速度, 重力
; 水面移动时生成水花粒子
; 与EnableSeaSurfaceParticle无关

EnableSeaSurfaceParticle = true
; 海面飞行时是否生成水花
; 尺寸受ParticlesScale影响（推荐0.7）
; 注：与AddParticleSplash无关

;***********************************************************************************
■ 地面载具专属设置
;***********************************************************************************

;需四文件（全小写）：
;  vehicles文件夹：配置文件
;  models/vehicles：模型
;  textures/vehicles：纹理
;  textures/items：物品纹理

AddPart = 参数1, 参数2, 参数3, 参数4, 位置X,Y,Z
; 添加随玩家旋转的部件
; 参数1：第一人称是否隐藏（true=显示）
; 参数2：是否水平联动（true=联动）
; 参数3：是否俯仰联动（true=联动）
; 参数4：部件类型（0=普通,1=开火时旋转,2=开火时后坐）
; 模型命名：载具名_part?.obj
AddChildPart = 参数1, 参数2, 参数3, 参数4, 位置X,Y,Z
; 添加子部件（需在AddPart后）
; 模型命名：载具名_part?_#.obj（#从0开始）
; 示例：
; AddPart     → 载具名_part0.obj
; AddChildPart → 载具名_part0_0.obj / part0_1.obj

; RotationPitchMax/Min为旧参数，请勿使用

;***********************************************************************************
■ 车辆专属设置
;***********************************************************************************

;需四文件（全小写）：
;  tanks文件夹：配置文件
;  models/tanks：模型
;  textures/tanks：纹理
;  textures/items：物品纹理

DefaultFreelook = true
; 上车后立即启用自由视角（主要用于坦克）

OnGroundPitchFactor = 2.0
OnGroundRollFactor  = 1.3
; 地形适应倾斜速度
; 值越大倾斜越快
; 高速车辆建议调高，低速车辆调低
; 过高会导致画面抖动，过低会卡进方块

CameraRotationSpeed = 25
; 摄像机旋转速度（坦克可用于限制炮塔转速）

WeightType = Tank
; 重量类型：Tank（坦克） / Car（汽车） / Unknown（未知）
; Tank：撞击生物时自身无伤，破坏更多方块
; Car：撞击生物时自身受伤，破坏较少方块
; 方块破坏规则在mcheli.cfg设置

WeightedCenterZ = 0.0
; 重心Z坐标（影响地形适应倾斜）
; ※ 效果不稳定，如不适建议禁用

SetWheelPos =  1.75,  -0.24,  4.85, 3.02, 1.44, -1.54, -2.91
;SetWheelPos =  X坐标, Y坐标,  Z坐标1, Z坐标2...
; 设置接地点（载具据此倾斜）
; X负值无需设置
; ★ Y坐标强烈建议固定为-0.24

======================================2025.10.8更新，以下为MCHeli-Reforged参数=====================================
    /**
     * 雷达种类
     */
radarType = MODERN_AA
;现代对空雷达
radarType = EARLY_AA
;早期对空雷达
radarType = MODERN_AS
;现代对地雷达
radarType = EARLY_AS
;早期对地雷达
;默认值=无

以上雷达参数大小写敏感

nameOnModernAARadar = "?"
;当前载具在现代对空雷达中显示的名字
;默认值=？

nameOnEarlyAARadar = "?"
;当前载具在早期对空雷达中显示的名字
;默认值=？

nameOnModernASRadar = "?"
;当前载具在现代对地雷达中显示的名字
 ;默认值=？

nameOnEarlyASRadar = "?"
;当前载具在早期对地雷达中显示的名字
 ;默认值=？

explosionSizeByCrash = 5
;载具被摧毁时爆炸范围
 ;默认值=5

throttleDownFactor = 1
;倒车速度倍率(推荐值为3,这样倒车速度大概为前进速度的一半。但倒车速度还受motionfactor影响)
;默认值=1

haschaff = false
;是否有箔条
;默认值=false

chaffUseTime = 100
;箔条生效时长
;默认值=无
 
chaffWaitTime = 400
;箔条冷却时长
;默认值=无

hasmaintenance = false
;是否有维修系统
;默认值=false

maintenanceUseTime = 20
;维修系统生效时长 （时长即为回血百分比）
;默认值=无
 
maintenanceWaitTime = 300
;维修系统冷却时长
;默认值=无

engineShutdownThreshold = 20
;载具瘫痪阈值，血量低于此百分比将关闭载具引擎
;默认值=无
 
hasaps = false
;是否有主动防御系统
;默认值=false

apsUseTime = 100
;APS生效时长(生效时能拦截Rocket和missile类型武器)
;默认值=100
 
apsWaitTime = 400
;APS冷却时长
;默认值=400
 
apsRange = 8
;APS范围
;默认值=8
 
enableRWR = false
;是否有RWR
;默认值=false
 
hudType = 0
;hud自定义字段，用于指示载具hud
;默认值=无
 
weaponGroupType = 0
;hud自定义字段，用于指示载具weaponGroupType
;默认值=无
 
armorExplosionDamageMultiplier = 1.0
;载具爆炸倍率，最终的爆炸伤害=爆炸伤害*爆炸倍率
;默认值=1

;目前MCH-R除了支持mch原版的碰撞箱外，还新增了两种碰撞箱，以下是写法
;第一种为BoundingBox = {center_x}, {center_y}, {center_z}, {width}, {height}, {length}, {multiplier}, DEFAULT, {name}
;它表示在坐标center_x,center_y,center_z的位置生成一个以其为中心，宽高长分别为width,height,length，受到伤害倍率为multiplier，被打击时命中显示名称为name的DEFAULT碰撞箱
;DEFAULT类型碰撞箱不会随炮塔转动，以下是例子
BoundingBox = 0.0, 1.21, 3.6, 4.684, 0.8871, 1.5, 0.4, DEFAULT, Upper Glacis
;该例子代表在0.0, 1.21, 3.6位置，生成宽高长分别为4.684, 0.8871, 1.5，伤害倍率为0.4，被攻击后显示部位为Upper Glacis的普通碰撞箱

;第二种碰撞箱为BoundingBox = {center_x}, {center_y}, {center_z}, {width}, {height}, {length}, {multiplier}, TURRET, {name}
;它表示在坐标center_x,center_y,center_z的位置生成一个以其为中心，宽高长分别为width,height,length，受到伤害倍率为multiplier，被打击时命中显示名称为TURRET的DEFAULT碰撞箱
;TURRET类型碰撞箱会随着炮塔绕0,y,0进行转动(我们推荐将炮塔旋转位置写为0,y,0)，以下是例子
BoundingBox = 0.0, 2.16, -0.44, 4.1, 1, 5.4, 0.4, TURRET, Turret Front
;该例子代表在0.0, 2.16, -0.44位置，生成宽高长分别为4.1, 1, 5.4，伤害倍率为0.4，被攻击后显示部位为Turret Front的随着炮塔旋转的炮塔碰撞箱

; ★ 重要 ★
; 設定ファイルとモデルはMinecraftを終了せずに再読み込みできます。
; [ ビークル搭乗 → Rキーで補給画面を開く → MODオプション → 開発 → 航空機設定再読み込み ]
; テクスチャとサウンドはヘリコプターMODではなく、Minecraftのネイティブ機能で再読み込みする必要があります。
; [ Escキーでゲームメニューを開く → 設定 → リソースパック → 完了 ]

;***********************************************************************************
■ ヘリコプター/戦闘機/地上ビークル/戦車設定ファイルの共通設定
;***********************************************************************************

DisplayName = AH-6 キラーエッグ
; 表示名 ※全角文字は使用不可、半角英数字及び記号のみ使用可

AddDisplayName = ja_JP, AH-6 キラ－エッグ
; アイテム保持時に表示される名前
; ※ 日本語全角文字を使用する場合、ファイルエンコーディングはUTF-8でなければならない

ItemID = 28801
; アイテムID (Minecraftで実際に使用される際は+256される)
; ※ バージョン1.7.2以降ではItemIDは使用されないが、1.6.4以前との互換性のために設定必須

Invulnerable = true
; ビークル無敵モード
; マルチプレイでの基地防衛兵器に推奨

CreativeOnly = true
; クリエイティブモードのプレイヤーのみがアイテムを設置または回収可能

AddTexture = sh60-us-1
AddTexture = sh60-jp-1
AddTexture = sh60-jp-2
; 追加テクスチャ（複数追加可）
; デフォルトで設定ファイルと同じ名前のpngファイルを使用
; ここに追加テクスチャを指定（拡張子なし）

ThirdPersonDist = 12
; デフォルトの第三人称視点距離
; ヘリコプターMODではPageUp/Downで4ブロック単位で距離調整可能、4の倍数設定を推奨

CameraPosition = 0.0, 1.1, 3.7
CameraPosition = 0.0, 1.1, 3.7, false
CameraPosition = 0.0, 1.1, 3.7, true, 30, 45
; カメラ座標
; 複数設定でHキーによる視点切替可能
; 1-3番目：座標
; 4番目：true設定でカメラ視点常時固定
; 5番目：水平角度
; 6番目：垂直角度

CameraZoom = 3
; カメラ最大ズーム倍率

HUD = heli, heli_gnr, none, gunner
; 各座席で使用するHUD設定ファイル名
; 本例：操縦席はheli.txt、2番席はheli_gnr.txt、3番席はHUDなし、4番席はgunner.txtを使用
; 座席数より設定数が少ない場合、未指定席は以下デフォルトを使用：
; 未設定時デフォルト：
; ヘリコプター：HUD = heli, heli_gnr, gunner, gunner, gunner, gunner...
; 固定翼機：HUD = plane, plane, gunner, gunner, gunner, gunner...
; 地上ビークル：HUD = vehicle
;
; ※ 操縦席のみ砲手モード時に2番席のHUD設定を使用
;    単座ビークルでも砲手モード有効時は2番席設定必要
;    例：HUD = heli, heli_gnr

EnableGunnerMode = true
; 砲手モード切替可否（true=有効、false=無効）

EnableNightVision = true
; ナイトビジョンモード切替可否（true=有効、false=無効）

EnableEntityRadar = false
; レーダー可否（true=有効、false=無効）

Speed = 0.6
; ビークル速度（値大きいほど高速）

MotionFactor = 0.96
; ビークル移動減衰係数（範囲0.0~1.0、値小さいほど減衰強力）

Gravity = -0.04
; ビークル重力設定（負値は落下）

GravityInWater = -0.04
; 水中重力設定（負値は落下）

StepHeight = 2.5
; 乗り越え可能ブロック高さ

MobilityYaw
MobilityYawOnGround
; 水平旋回感度（値大きいほど機動性向上）
; MobilityYawOnGround は地上のみ影響、水面は影響なし
MobilityRoll
; ロール感度（値大きいほどロール高速）
MobilityPitch
; ピッチ感度（値大きいほど機動性向上；地上ビークルはピッチ角上下限を示す）
MinRotationPitch
MaxRotationPitch
; 範囲 MinRotationPitch -80~0
; 範囲 MaxRotationPitch 0~80
; ピッチ角制限（最小/最大）
; ※ ヘリコプター/戦闘機で有効時、ロールも制限される

MinRotationRoll
MaxRotationRoll
; ロール角制限（最小/最大）
; 範囲 MinRotationRoll -80~0
; 範囲 MaxRotationRoll 0~80
; ※ ヘリコプター/戦闘機で有効時、ピッチも制限される

UnmountPosition = 3.0, 1.0, -2.0
; 降車時座標

AddSeat =-0.45,  0.80,  1.20
AddSeat = 0.45, -0.50,  1.20
AddSeat =-0.90, -0.50,  0.20
AddSeat = 0.90, -0.50,  0.20, true
; 座席追加 ※無人機以外は最低1座席必須
; 1番目が操縦席
; パラメータは座標(X,Y,Z)
; 4番目パラメータで座席が操縦者方向に回転するか決定（主に戦車砲塔用）

AddGunnerSeat = -0.45, 0.80, 1.20,   0.0, 2.00, -1.01,   true
AddGunnerSeat = -0.45, 0.80, 1.20,   0.0, 2.00, -1.01,   true, -60, 78, true
; AddGunnerSeat=座席X,Y,Z,  カメラX,Y,Z,  視点切替可否,  カメラ上限(-90~0), カメラ下限(0~90), 座席砲塔連動回転
; 砲手席追加
; この座席のプレイヤーはデフォルトでカメラ視点
; パラメータに座席座標とカメラ位置含む（カメラ位置省略可、デフォルトはCameraPosition）
; 視点切替falseでカメラ視点固定、trueでHキーでプレイヤー視点に戻れる
; 10番目パラメータで座席が操縦者方向に回転するか制御

AddFixRotSeat = -0.45,  0.80,  1.20, 0.0,2.00,-1.01,  true,  -50, 40
; AddFixRotSeat=座席X,Y,Z,  カメラX,Y,Z,  視点切替可否,  水平固定角度, 垂直固定角度
; 固定視点席追加
; AddGunnerSeatと類似するが、カメラ角度固定で調整不可
; 固定角度設定でマウス視点調整不能（Ctrlキーで自由視点切替可）

; ★★★★★
; ビークル搭載機能は以下を満たす必要あり：
; ・搭載側が被搭載ビークル指定（AddRack）
; ・被搭載側が搭載側ラック番号指定（RideRack）
; いずれかの条件満たせば有効

AddRack = container,                 0.0, 1.4, -4.7,  0.0, 1.0, -16.1
AddRack = container / ah-64,         0.0, 1.4, -4.7,  0.0, 1.0, -16.1,  5.0, 20
AddRack = helicopter/vehicle / t-4,  0.0, 1.4, -4.7,  0.0, 1.0, -16.1,  5.0, 100000,  0.0, 0.0
; ■ 搭載側設定
; AddRack =
;  パラメータ1：搭載可能実体名
;  パラメータ2-4：ラック座標X,Y,Z（ビークル上位置）
;  パラメータ5-7：出入口座標X,Y,Z（実体はこの座標近くでないと積載/降載不可）
;  パラメータ8：入口半径（省略可）
;  パラメータ9：パラシュート展開高度（極大値設定でパラシュート無効化）
;  パラメータ10：被搭載実体水平角度
;  パラメータ11：被搭載実体垂直角度
; コンテナ/ヘリコプター等搭載可能ラック追加
;  実体名は container/helicopter/plane/vehicle または直接ビークル名指定（ah-64等）、/区切り

RideRack = c5, 1
; ■ 被搭載側設定
; RideRack = 搭載ビークル名, ラック番号（1~）

ExclusionSeat = 15, 17
; パラメータ数無制限（≥2必須）
; 排他的座席/ラック設定
; 例：ExclusionSeat = 3,4,5：
;  3番席占有時、4/5番席は実体搭載不可
;  4番席占有時、3/5番席は実体搭載不可
;  5番席占有時、3/4番席は実体搭載不可
;
; 座席/ラック番号付け規則：全座席定義を順に番号付け後、ラックに番号付け
; 設定順序例：
;  AddSeat  →1番
;  AddRack  →4番
;  AddGunnerSeat →2番
;  AddRack  →5番
;  AddSeat  →3番
;  AddRack  →6番
; 番号明確化のためラックは最後に定義推奨

TurretPosition = 0.0, 0.0, 0.25
; 砲塔回転中心位置（不要な変更は非推奨）

AddWeapon = m230,     0.00, 0.90, 2.54,   0.0, 0.0, true, 2
AddWeapon = hydra70,  0.00, 0.90, 2.54,   0.0, 0.0, true, 1, 0,-60,60, 0,25
AddWeapon = m134,     1.48, 0.40, 1.54,   1.0, 0.0
AddWeapon = m134,    -1.48, 0.40, 1.54,  -1.0, 0.0
AddTurretWeapon = hydra70,  0.00, 0.90, 2.54,   0.0, 0.0, true, 1, 0,-60,60, 0,25
; 兵器追加（ファイル名はweaponsフォルダ内拡張子なしファイルと一致必須）
; 同一兵器連続追加（m134等）は単一兵器多発射点として扱われる
; パラメータ順：兵器設定名、位置(X,Y,Z)、回転角(水平,垂直)、操縦者使用可否、座席、デフォルト水平角、最小水平角、最大水平角、最小俯仰角、最大俯仰角
;
; 座席：1=1番席、2=2番席、以降同様
; パラメータ組み合わせ説明：
;  true,2 → 2番席プレイヤー使用可、2番席無人時操縦者使用可
;  false,2 → 2番席プレイヤーのみ使用可
;  false,1 → 操縦者のみ使用可（非推奨）
;  true,1 → 操縦者のみ使用可
; 省略時デフォルト true,1
;
; AddTurretWeaponとAddWeaponの違いは発射点が砲塔回転に連動する点のみ

AddSearchLight      = 0.71,  -0.02,  0.02,   0x50FFFFFF,   0x10FFFFC0,    60.0, 20.0,       0,   0
AddFixedSearchLight = 0.71,  -0.02,  0.02,   0x50FFFFFF,   0x10FFFFC0,    60.0, 20.0,       0,   0
AddSteeringSearchLight = -0.52,0.90, 1.76,   0x50FFFFFF,   0x00FFFFC0,    27.0, 15.0,       5,   0,     45
;AddSearchLight     = 座標X,Y,Z,   起点色, 終点色,  距離, 末端半径, 水平角, 俯仰角, 舵角
; AddSearchLight      ：動的サーチライト（搭乗者視点回転連動）
; AddFixedSearchLight ：固定方向サーチライト
; AddSteeringSearchLight ：タイヤ方向連動回転固定灯（舵角はタイヤ旋回角に合わせ推奨）

AddPartLightHatch =  0.32, 0.23, 1.83,   -1,0,-0.024, 90
;AddPartLightHatch= 座標X,Y,Z, 回転軸X,Y,Z, 回転角度 -1800~1800
; サーチライト作動時のみ展開するパーツ追加
; ★重要：AddSearchLightまたはAddFixedSearchLight設定が必須

AddRecipe = " Y ",  "YXY",  " YD",  X, iron_block, Y, iron_ingot, D,dye,2
AddRecipe ="YXY", X, mcheli:ah-6, Y, redstone
AddShapelessRecipe = iron_block, iron_ingot, dye,2
; クラフトレシピ追加（複数AddRecipe行で複数レシピ追加可）
; ""内3文字は作業台横並びに対応
; (フォーマットはForgeのGameRegistry.addRecipeと同様)
; 詳細例：
; X = 鉄ブロック名
; Y = 鉄インゴットアイテム名
; D = 緑色染料アイテム名（ダメージ値付きアイテムは名称後にダメージ値追加要）
; アイテム名参考：http://minecraft.gamepedia.com/Data_values
; バニラアイテムは"minecraft:"接頭辞省略可
; MODアイテムはMOD名指定要（例：mcheli:ah-6）
; AddShapelessRecipe は無順序クラフトレシピ追加

FlareType = 1
; フレア/デコイタイプ：
; 0=無し
; 1=通常
; 2=大型機用
; 3=横方向射出
; 4=前方射出
; 5=下方射出
; 10=戦車スモーク弾

Float  = true
; 浮遊機能有効

FloatOffset = -1.0
; 浮遊高度オフセット（負値可）

SubmergedDamageHeight = 2
; この高度以下の水接触はダメージ無し（単位：ブロック）

MaxHP = 100
; ヒットポイント/耐久値

ArmorDamageFactor = 0.5
; ビークルダメージ係数（1.0=100%、0.5=50%）

ArmorMinDamage = 5
; 最小ダメージ閾値（この値未満のダメージは無視）

ArmorMaxDamage = 500
; 最大ダメージ上限（超過分はこの値として計算）

InventorySize = 18
; ビークルインベントリサイズ（9の倍数必須）

DamageFactor = 0.2
; プレイヤーダメージ係数（0.2=20%ダメージ受ける）
; 注：プレイヤー被ダメージ時、ビークルも同時被ダメージ

Sound = heli
; スロットル増加時のサウンドファイル（sounds/heli.oggに対応）

UAV = true
SmallUAV = true
; true=無人機（操縦席進入不可）
; UAV=true：大型無人機（ハンドヘルド端末制御不可）
; SmallUAV=true：小型無人機（ハンドヘルド端末制御可）
; 注：無人機制御ステーションは全タイプ制御可、ハンドヘルド端末は小型機のみ

TargetDrone = true
; 飛行機のみ有効：true=無人標的機（操縦席進入不可）
; 無人機制御ステーションからのみスポーン可、スポーン後自動低空旋回

OnGroundPitch = angle
; 地上駐機時のピッチ角（例：零戦地上機首上げ）

AddPartHatch = 位置X,Y,Z, 回転軸X,Y,Z, 回転角度0~180
; Zキー開閉ハッチ追加
; モデル命名：ビークル名_hatch?.obj（?は0から開始）
; モデル未発見時表示なし（表示不要時モデル不要）

AddPartSlideHatch = 移動量X,Y,Z
; スライド式ハッチ追加（モデル命名規則はAddPartHatch同様）

AddPartCamera = 座標X,Y,Z, 水平連動, 俯仰連動
; 常時プレイヤー方向を向くパーツ追加
; モデル命名：ビークル名_camera?.obj

AddPartRotation = 0.00, 9.00, -31.17,  0,-1,0,       1.3,      false
; AddPartRotation = 位置X,Y,Z,        回転軸X,Y,Z,   回転速度,  連続回転可否
; 周期的回転パーツ追加

AddPartWeapon        = m230,       false, true, true,  -2.51,  1.29,  -1.51
AddPartWeapon        = m102_105mm, false, true, true,  -2.51,  1.29,  -1.51, 1.00
AddPartWeapon        = rehinmetall_apfsds / rehinmetall_he, false, true, false,  0.00, 2.10, 0.00, 0
AddPartTurretWeapon  = mg7_62mm,   false, true, true,  -0.83,  3.39,  -0.57, 0
AddPartRotWeapon     = m134_r50,   false, true, true,  -1.825, 1.475, -0.25, 1,0,0
AddPartWeaponChild   = false, true, 0.00, 0.5, 3.00
AddPartWeaponMissile = aim120,     false, false,false, -2.51,  1.29,  -1.51
; ヘリコプター/戦闘機兵器パーツ設定
; AddPartWeapon = 連動兵器名（noneで無し）, 砲手モード非表示?, 水平連動, 俯仰連動, 回転座標X,Y,Z, 反動距離
; AddPartRotWeapon = 連動兵器名, 砲手モード非表示?, 水平連動, 俯仰連動, 回転座標X,Y,Z, 回転軸X,Y,Z
; AddPartWeaponChild = 水平連動, 俯仰連動, 回転座標X,Y,Z
; AddWeapon兵器角度変化に連動（兵器名は/区切り）
; 反動距離は火砲後退移動量
; AddPartRotWeaponは回転銃身機銃用（発射時回転）
; モデル命名：ビークル名_weapon?.obj
;
; AddPartWeaponChildはAddPartWeaponの子パーツとして追加
; AddPartWeapon直後定義必須
; モデル命名：ビークル名_weapon?_0.obj（?は親パーツ番号）
;
; AddPartWeaponMissileは兵器未準備時非表示（ミサイル/爆弾等）

AddPartWeaponBay = 兵器名, 位置X,Y,Z, 回転軸X,Y,Z, 回転角度0~180
; 回転開閉式兵器ベイ追加
AddPartSlideWeaponBay = 兵器名, 移動量X,Y,Z
; スライド開閉式兵器ベイ追加
; モデル命名：ビークル名_wb?.obj

AddPartCanopy = 位置X,Y,Z, 回転軸X,Y,Z, 回転角度0~180
; 回転式キャノピー追加
AddPartSlideCanopy = 移動量X,Y,Z
; スライド式キャノピー追加
; モデル命名：ビークル名_canopy?.obj（複数追加可）
; 互換性注記：数字省略時デフォルト_canopy0.obj使用

AddPartThrottle = 位置X,Y,Z,  回転軸X,Y,Z,  回転角度0~180,  移動量X,Y,Z
; スロットル連動回転/移動パーツ追加
; 回転角度前は必須項目

AddPartLG = 位置X,Y,Z, 回転軸X,Y,Z, 回転角度0~180 [, 回転軸X,Y,Z, 回転角度0~180]
AddPartLGRev = 位置X,Y,Z, 回転軸X,Y,Z, 回転角度0~180 [, 回転軸X,Y,Z, 回転角度0~180]
AddPartSlideRotLG = 移動量X,Y,Z,  位置X,Y,Z, 回転軸X,Y,Z, 回転角度0~180
AddPartLGHatch = 位置X,Y,Z, 回転軸X,Y,Z, 回転角度0~180 [, 回転軸X,Y,Z, 回転角度0~180]
; 着陸装置追加（離陸時自動格納）
; モデル命名：ビークル名_lg?.obj
; AddPartLGRevはAddPartLGと逆動作
; AddPartLGHatchは着陸装置折り畳み/展開時のみ開閉
;
; 動作説明：
; AddPartLG      格納：0°→90°
; AddPartLGRev   格納：90°→0°
; AddPartSlideRotLG 格納：0°→90°
; AddPartLGHatch 格納：0°→90°→0°

TrackRollerRot = 30
; 履帯ローラー回転速度（負値は逆回転但不推奨）

AddTrackRoller = -1.72,  0.77,  5.04
; 履帯ローラー追加（座標のみ必要、X負値=右側、正值=左側）
; 履帯設定から独立して設定可

AddCrawlerTrack = false, 0.37, -2.09,  1.03/-3.41, 0.72/-3.57, 0.37/-3.42, -0.15/-2.55, -0.25/-2.16, -0.25/3.88, -0.13/4.21, 0.52/5.29, 0.78/5.39, 1.03/5.28, 1.10/5.04, 1.15/-3.12
;AddCrawlerTrack = 履帯方向,  単節間隔, 履帯X位置, 回転点Y/Z, ...
; 履帯動作異常時方向パラメータ調整可
; ゲームテストモードでは設定位置を赤/青点で表示

PartWheelRot = 40
; タイヤ回転速度（値大きいほど高速）

AddPartWheel     = -1.05, 0.157, 1.965,  30
; タイヤ追加     X,Y,Z座標,   最大旋回角
AddPartWheel     =  0.68,  0.19,  1.20,  30,   0.0, 1.0, 0.2,   0.68, 0.19, 0.70
; タイヤ追加     X,Y,Z座標,   旋回角, 回転軸X,Y,Z,    回転位置X,Y,Z
; 回転軸省略時デフォルト(0,1,0)

AddPartSteeringWheel =  -0.54, 0.88,  0.48,   0.0,     1.0, -1.7,  130
; ステアリングホイール追加        X,Y,Z座標,   回転軸X,Y,Z,   最大回転角度

ThrottleUpDown = 1.0
ThrottleUpDownOnEntity = 2.0
; スロットル応答係数（値小さいほど離陸遅い）
;
; ThrottleUpDownOnEntityはビークル他実体搭載時応答係数（デフォルト2.0）
; 計算式：
; ThrottleUpDown × 搭載実体速度 × ThrottleUpDownOnEntity → スロットル感度
; 例：ThrottleUpDownOnEntity=2.0でトロッコ搭載時（最高速≈1.7）
;       1.7 × 2.0=3.4 → 離陸所需距離1/3で済む

AutoPilotRot = -0.4
; 自動旋回角度（値大きいほど旋回半径小さい）
; 0=直進
; 負値=左折、正值=右折

ConcurrentGunnerMode = true
; 2番席占有時も砲手モード進入許可

Regeneration = true
; 2番席以降搭乗者自動体力回復

ParticlesScale = 0.1
; 砂塵等粒子効果サイズ（値大きいほど効果顕著）

FuelSupplyRange = 25
; 他ビークル燃料供給範囲（単位：メートル）
; 供給時自身燃料消費なし
; 自己供給不可

AmmoSupplyRange = 35
; 他ビークル弾薬補給範囲（単位：メートル）
; 補給時自身弾薬消費なし
; 自己補給不可

MaxFuel         = 600
; 最大燃料容量
FuelConsumption = 0.5
; 每秒燃料消費量
; 航続時間(秒) = 最大燃料容量 / 每秒消費量
; 600 / 0.5 = 1200秒

Stealth = 0.5
; ステルス性（0.0~1.0、デフォルト0.0）
; 値高いほどミサイルロック困難（ロック時間延長、ロック距離短縮）

SmoothShading = false
; スムーズシェーディング切替
; false=フラットシェーディング（角ばった縁）
; true=スムーズシェーディング（縁滑らか）
; 注：mcheli.cfgでSmoothShading=falseは全局スムーズシェーディング無効

HideEntity = false
; 搭乗者モデル非表示可否
; true=非表示
; false=表示

EntityWidth  = 0.9
EntityHeight = 0.9
; 搭乗者モデル描画サイズ（幅/高さ、範囲-100.0~100.0）
; 0.5=半サイズ

EntityPitch = 45
EntityRoll  = 20
; 搭乗者モデル描画角度（-360~360）

CanRide = false
; 搭乗許可可否
; true=許可（デフォルト）
; false=禁止

BoundingBox =  衝突箱中心X,Y,Z,  幅, 高さ, ダメージ倍率
; 衝突箱追加
; 本MOD機銃/ミサイルのみ影響
; ブロック/実体と衝突しない
; MODオプションでTestMode有効化で表示可
; ダメージ倍率デフォルト1.0（0.5=半ダメージ、3.0=3倍ダメージ）

Category = W.A
; ビークル分類（クリエイティブモードインベントリソート用のみ）

CanMoveOnGround = false
CanRotOnGround  = false
; 地上移動/回転禁止
;  CanMoveOnGround：地上移動禁止
;  CanRotOnGround：地上回転禁止

EnableParachuting = true
; パラシュート機能有効（3番席以降プレイヤーのみSpaceキーでパラシュート）
MobDropOption  = 0.0, 0.0, -11.5,  10
; 搭乗者投下設定 = 投下点X,Y,Z, 投下間隔（1/20秒）

RotorSpeed = 50.0
; ローター速度（値大きいほど高速、負値は逆回転但不推奨）

;***********************************************************************************
■ ヘリコプター専用設定
;***********************************************************************************

;4ファイル必要（全て小文字）：
;  helicoptersフォルダ：設定ファイル
;  models/helicopters：モデル
;  textures/helicopters：テクスチャ
;  textures/items：アイテムテクスチャ

EnableFoldBlade = false
; ローターブレード折り畳み機能（true=有効）

AddRotor= 6, 60,  0.00,  3.35,  0.00,  0.0, 1.0, 0.0, true
AddRotor= 2, 60,  0.50,  1.90, -6.55,  1.0, 0.0, 0.0
; ローター追加（数無制限）
; 本例1番目主ローター、2番目尾ローター
; 1番目ローターのみ折り畳み可能
; パラメータ：ブレード枚数、ブレード間角度、位置X,Y,Z、回転軸X,Y,Z、折り畳み可否
; モデル命名：ビークル名_rotor?.obj
;
; ※ 旧版AddRotorOldは非推奨

AddRepellingHook =  0.60, 2.75, -14.21, 30
; 降下フック設定 = フック座標X,Y,Z, 展開間隔

;***********************************************************************************
■ 戦闘機専用設定
;***********************************************************************************

;4ファイル必要（全て小文字）：
;  planesフォルダ：設定ファイル
;  models/planes：モデル
;  textures/planes：テクスチャ
;  textures/items：アイテムテクスチャ

AddPartRotor = 位置X,Y,Z, 回転軸X,Y,Z, 回転角度(-180~180)
; ローター追加（VTOL時回転）
; モデル命名：ビークル名_rotor?.obj
AddBlade = ブレード枚数, ブレード間角度, 位置X,Y,Z, 回転軸X,Y,Z
; AddPartRotor後追加必須
; モデル命名：ビークル名_blade?.obj

AddPartWing = 位置X,Y,Z, 回転軸X,Y,Z, 回転角度0~180
; 折り畳み主翼追加
; モデル命名：ビークル名_wing?.obj
AddPartPylon = 位置X,Y,Z, 回転軸X,Y,Z, 回転角度0~180
; 折り畳みパイロン追加
; モデル命名：ビークル名_wing?_pylon?.obj
; AddPartWing後追加必須
; 例：
; AddPartWing  → モデル：ビークル名_wing0.obj
; AddPartPylon → モデル：ビークル名_wing0_pylon0.obj / wing0_pylon1.obj

PivotTurnThrottle = 0.0
; 地上旋回時移動量
; 0=その場旋回、>0=旋回時移動
; 戦車設定推奨：
;  超信地旋回=0
;  信地旋回>0

EnableBack = true
; 後退許可

VariableSweepWing = true
SweepWingSpeed = 1.2
; 可変後退翼設定（AddPartWing必要）
; VariableSweepWing=true：空中翼調整可
; SweepWingSpeed=1.2：翼折り畳み時速度

AddPartNozzle = 位置X,Y,Z, 回転軸X,Y,Z, 回転角度0~180
; エンジンノズル追加（VTOL時回転）
; モデル命名：ビークル名_nozzle?.obj
; 粒子サイズはParticlesScaleで制御

EnableVtol = true
; VTOL機能可否
DefaultVtol = true
; VTOL有効時デフォルト状態（true=地上自動VTOL有効）
VtolYaw = 0.3
; VTOL状態水平旋回量
VtolPitch = 0.3
; VTOL状態俯仰旋回量

EnableEjectionSeat = true
; 射出座席切替
; true=GUIに射出座席ボタン追加
; 1座席ビークルは1つ、2座席ビークルは2つ対応

AddParticleSplash  =  1.0,  0.97,   13.19,      3,     9.0,   1.1,        20, 0.30, -0.03
;AddParticleSplash = 座標X,Y,Z,  粒子数,  サイズ,  速度,  持続時間, 上昇速度, 重力
; 水面移動時水飛沫粒子生成
; EnableSeaSurfaceParticleと無関係

EnableSeaSurfaceParticle = true
; 海面飛行時水飛沫生成可否
; サイズはParticlesScale影響（推奨0.7）
; 注：AddParticleSplashと無関係

;***********************************************************************************
■ 地上ビークル専用設定
;***********************************************************************************

;4ファイル必要（全て小文字）：
;  vehiclesフォルダ：設定ファイル
;  models/vehicles：モデル
;  textures/vehicles：テクスチャ
;  textures/items：アイテムテクスチャ

AddPart = パラメータ1, パラメータ2, パラメータ3, パラメータ4, 位置X,Y,Z
; プレイヤー回転連動パーツ追加
; パラメータ1：一人称非表示？（true=表示）
; パラメータ2：水平連動？（true=連動）
; パラメータ3：俯仰連動？（true=連動）
; パラメータ4：パーツタイプ（0=通常,1=発射時回転,2=発射時反動）
; モデル命名：ビークル名_part?.obj
AddChildPart = パラメータ1, パラメータ2, パラメータ3, パラメータ4, 位置X,Y,Z
; 子パーツ追加（AddPart後要）
; モデル命名：ビークル名_part?_#.obj（#は0から開始）
; 例：
; AddPart     → ビークル名_part0.obj
; AddChildPart → ビークル名_part0_0.obj / part0_1.obj

; RotationPitchMax/Minは旧パラメータ、使用禁止

;***********************************************************************************
■ 戦車専用設定
;***********************************************************************************

;4ファイル必要（全て小文字）：
;  tanksフォルダ：設定ファイル
;  models/tanks：モデル
;  textures/tanks：テクスチャ
;  textures/items：アイテムテクスチャ

DefaultFreelook = true
; 搭乗後即時自由視点有効（主に戦車用）

OnGroundPitchFactor = 2.0
OnGroundRollFactor  = 1.3
; 地形適応傾斜速度
; 値大きいほど傾斜速い
; 高速ビークルは高く、低速ビークルは低く設定推奨
; 高過ぎると画面振動、低過ぎるとブロックに嵌る

CameraRotationSpeed = 25
; カメラ回転速度（戦車は砲塔回転速度制限に使用可）

WeightType = Tank
; 重量タイプ：Tank（戦車）/ Car（自動車）/ Unknown（不明）
; Tank：生物衝突時自身被ダメージ無、ブロック破壊多
; Car：生物衝突時自身被ダメージ有、ブロック破壊少
; ブロック破壊規則はmcheli.cfg設定

WeightedCenterZ = 0.0
; 重心Z座標（地形適応傾斜影響）
; ※ 効果不安定、不適切時無効推奨

SetWheelPos =  1.75,  -0.24,  4.85, 3.02, 1.44, -1.54, -2.91
;SetWheelPos =  X座標, Y座標,  Z座標1, Z座標2...
; 接地点設定（ビークルはこれに基づき傾斜）
; X負値設定不要
; ★ Y座標は-0.24固定強く推奨

======================================2025.10.8更新、以下MCHeli-Reforgedパラメータ=====================================
    /**
     * レーダー種類
     */
radarType = MODERN_AA
;現代対空レーダー
radarType = EARLY_AA
;旧式対空レーダー
radarType = MODERN_AS
;現代対地レーダー
radarType = EARLY_AS
;旧式対地レーダー
;デフォルト=無し

上記レーダーパラメータは大文字小文字区別

nameOnModernAARadar = "?"
;現代対空レーダー当該ビークル表示名
;デフォルト=?

nameOnEarlyAARadar = "?"
;旧式対空レーダー当該ビークル表示名
;デフォルト=?

nameOnModernASRadar = "?"
;現代対地レーダー当該ビークル表示名
;デフォルト=?

nameOnEarlyASRadar = "?"
;旧式対地レーダー当該ビークル表示名
;デフォルト=?

explosionSizeByCrash = 5
;ビークル破壊時爆発範囲
;デフォルト=5

throttleDownFactor = 1
;後退速度倍率（推奨値3、後退速度は前進速度の約半分。但し後退速度はmotionfactorにも影響される）
;デフォルト=1

haschaff = false
;チャフ装備可否
;デフォルト=false

chaffUseTime = 100
;チャフ効果持続時間
;デフォルト=無し

chaffWaitTime = 400
;チャフクールダウン時間
;デフォルト=無し

hasmaintenance = false
;整備システム装備可否
;デフォルト=false

maintenanceUseTime = 20
;整備システム効果持続時間（持続時間は体力回復百分比）
;デフォルト=無し

maintenanceWaitTime = 300
;整備システムクールダウン時間
;デフォルト=無し

engineShutdownThreshold = 20
;ビークル行動不能閾値、体力此百分比以下でエンジン停止
;デフォルト=無し

hasaps = false
;アクティブ防護システム装備可否
;デフォルト=false

apsUseTime = 100
;APS効果持続時間（作動時Rocket及びMissileタイプ兵器迎撃可能）
;デフォルト=100

apsWaitTime = 400
;APSクールダウン時間
;デフォルト=400

apsRange = 8
;APS範囲
;デフォルト=8

enableRWR = false
;レーダー警報受信機装備可否
;デフォルト=false

hudType = 0
;HUDカスタムフィールド、ビークルHUD指示用
;デフォルト=無し

weaponGroupType = 0
;HUDカスタムフィールド、ビークルweaponGroupType指示用
;デフォルト=無し

armorExplosionDamageMultiplier = 1.0
;ビークル爆発倍率、最終爆発ダメージ=爆発ダメージ*爆発倍率
;デフォルト=1

;現在MCH-Rはmch原版衝突箱に加え、二種新衝突箱をサポート。構文如下：
;第一種はBoundingBox = {center_x}, {center_y}, {center_z}, {width}, {height}, {length}, {multiplier}, DEFAULT, {name}
;center_x,center_y,center_zを中心とし、幅、高さ、長さを指定、ダメージ倍率、被弾表示名のDEFAULTタイプ衝突箱生成
;DEFAULTタイプ衝突箱は砲塔回転非連動。例：
BoundingBox = 0.0, 1.21, 3.6, 4.684, 0.8871, 1.5, 0.4, DEFAULT, Upper Glacis
;此例は0.0, 1.21, 3.6位置に、幅/高さ/長さ4.684, 0.8871, 1.5、ダメージ倍率0.4、被弾部位'Upper Glacis'表示の通常衝突箱生成

;第二種はBoundingBox = {center_x}, {center_y}, {center_z}, {width}, {height}, {length}, {multiplier}, TURRET, {name}
;center_x,center_y,center_zを中心とし、幅、高さ、長さ、ダメージ倍率、被弾表示名のTURRETタイプ衝突箱生成
;TURRETタイプ衝突箱は砲塔と共に0,y,0を中心に回転（砲塔回転位置を0,y,0に設定推奨）。例：
BoundingBox = 0.0, 2.16, -0.44, 4.1, 1, 5.4, 0.4, TURRET, Turret Front
;此例は0.0, 2.16, -0.44位置に、幅/高さ/長さ4.1, 1, 5.4、ダメージ倍率0.4、被弾部位'Turret Front'表示の砲塔回転連動衝突箱生成
​​2016/04/17​​
;​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​*​
;■ Weapon configuration file: weapons/​​.txt, sound/​​_snd.ogg
;​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​*​
;★ Important ★
;Weapon configuration files can be reloaded without closing Minecraft.
;Enter a vehicle → Press R to open the supply interface → MOD Options → Development → Reload All Weapons
;This action reloads all weapons (including portable weapons).
;Adding a new weapon requires two files (all lowercase):
; ・Add a weapon configuration file (.txt) in the weapons folder
; ・Add a sound file with the same name in the sound folder (format: weaponname_snd.ogg)
; For example, weapon 'abc' requires weapons/abc.txt and sound/abc_snd.ogg
;※ Sound file is no longer mandatory in version 0.9.4+
;Some numerical parameters have upper and lower limits.
DisplayName = M134 Minigun
;Display Name ※Do not use full-width characters; only half-width alphanumerics and symbols are allowed.
Type = MachineGun1
;Weapon Type (choose one from the following):
; MachineGun1 Fixed-direction Machine Gun (e.g., M134)
; MachineGun2 Player-aimed Machine Gun (e.g., M230)
; Torpedo Torpedo (auto-locks on targets after entering water, e.g., Mk46)
; CAS Close Air Support (e.g., A-10)
; Rocket Fixed-direction unguided rocket (e.g., Hydra70 / SNEB68mm)
; ASMissile Air-to-Surface Missile (strikes ground coordinates, e.g., AGM119)
; AAMissile Air-to-Air Missile (tracks airborne entities, e.g., AIM92)
; TVMissile Player-controlled missile after launch (e.g., AGM114[TV])
; ATMissile Anti-Tank Missile (tracks ground entities, e.g., AGM114)
; Bomb Vertically dropped bomb (e.g., CBU-100)
; MkRocket Marker Rocket (calls artillery strike on impact point, e.g., Hydra 70mm M264RP)
; Dummy Dummy weapon (displays text only, unusable)
; Smoke Smoke grenade (generates contrail, e.g., White Smoke)
; Dispenser Dispenser (uses item at impact point, e.g., Water Dispenser)
; TargetingPod Targeting Pod (marks entities/players/blocks, e.g., targeting_pod_block)
; Railgun Railgun (requires charging to fire)
Power = 8
;Base damage value, 1 damage = 1 heart (half a heart icon)
DamageFactor = tank, 2.0
;Damage multiplier:
; Parameter 1: Target type (player=player, heli/helicopter=helicopter, plane=plane, tank=tank/car, vehicle=ground vehicle)
; Parameter 2: Damage multiplier (e.g., Power=10 + multiplier 3.4 = 34 damage)
;Multiple lines can be added to configure multipliers for different targets.
Acceleration = 4.0
;Projectile velocity (Most weapons max 4.0, MachineGun1/2 and Rocket can go up to 100.0. Too high may cause projectile jitter)
AccelerationInWater = 4.0
;Torpedo speed in water (max 4.0)
VelocityInWater = 0.5
;Acceleration in water (Speed adjusted by multiplying this value per tick)
Explosion = 0
;Impact explosion power (0=no explosion, 1=equivalent to fireball power)
ExplosionInWater = 0
;Underwater explosion power
ExplosionBlock = 0
;Explosion block destruction power (0=does not destroy blocks)
ExplosionAltitude = 10
;Minimum arming height (explodes when ≤10 meters above ground)
DelayFuse = 30
;Delay fuse: Projectile lifetime in ticks (timer starts after impact)
;If Explosion is not 0, explodes when projectile disappears.
Bound = 0.4
;Bounce strength (requires DelayFuse to be set, otherwise explodes on impact)
TimeFuse = 30
;Time fuse: Projectile lifetime in ticks (timer starts after firing)
;If Explosion is not 0, explodes when projectile disappears.
Flaming = false
;Whether to spread fire at the impact point (only effective if Explosion>0)
Sight = MoveSight
;Reticle type:
; MoveSight Reticle moves with the vehicle
; MissileSight Target lock reticle (Required for AAMissile/ATMissile)
; None No reticle
Zoom = 4.2, 9.2
;For portable weapons only: Default zoom level(s) (comma-separated for multiple levels, Z key to cycle)
Group = MainGun
;Weapon Group:
; Firing any weapon in the same group triggers reload for the entire group.
; Example: A tank's main gun has three configs: APFSDS, HE, Canister, all set to Group = MainGun.
; Firing any shell type puts the others on cooldown (ammo count remains unchanged).
Delay = 5
;Firing interval (unit: 1/20 second. Lower value = higher rate of fire)
ReloadTime = 80
;Reload time (unit: 1/20 second. Lower value = faster reload)
;※ If reload time is set to 0, ensure Round > 0.
Round = 100
;Ammo capacity per load (Set to 0 or leave empty for infinite)
SoundVolume = 3
;Firing volume (Values ≥1.0 play at max volume. Set <1.0 to reduce volume)
SoundPitch = 1.0
;Sound pitch (0.0~1.0)
SoundPitchRandom = 0.1
;Random pitch variation range (e.g., SoundPitch=0.8 + this value 0.2 → actual pitch 0.6~0.8)
SoundDelay = 1
;Rapid-fire sound delay (prevents sounds from fast-firing weapons like M134 from overlapping others)
Sound = rocket_snd
;Sound filename (no extension. If not specified, defaults to weaponname_snd.ogg)
LockTime = 20
;Missile lock-on time (Higher value = slower lock)
RidableOnly = true
;Can only lock onto targets when the player is riding a vehicle.
ProximityFuseDist = 1.0
;Missile proximity fuse distance (1.0 = explodes when target is within 1 meter)
RigidityTime = 0
;Number of ticks delay after missile launch before homing starts (default 7)
Accuracy = 1
;Unguided projectile spread error (Higher value = less accurate)
Bomblet = 25
;Number of submunitions released (for cluster bombs, etc.)
BombletSTime = 5
;Submunition release delay (ticks)
BombletDiff = 0.7
;Submunition spread range
ModeNum = 2
;Number of weapon modes (X key to cycle, only effective for these types):
; MachineGun2 → Switch to High Explosive (requires Explosion>0)
; TVMissile → Switch to regular guidance (non-missile camera view)
; ATMissile → Switch to Top Attack mode
; Rocket → Switch to Airburst (releases sub-bombs in air)
; Currently only supports 1 or 2 modes.
Piercing = 2
;Maximum number of blocks the projectile can pierce through.
;Current version causes multiple explosions; each number represents one explosion.
HeatCount = 20
;Heat generated per shot.
MaxHeatCount = 150
;Maximum heat capacity.
FAE = true
;Fuel-Air Explosive (Thermobaric) switch (true enables)
;Note: This type of bomb does not destroy blocks.
ModelBullet = bullet
ModelBomblet = cbc
;Projectile model files:
; Example: loads models/bullets/bullet.obj + textures/bullets/bullet.png
; Submunition model: models/bullets/cbc.obj + textures/bullets/cbc.png
Destruct = true
;Vehicle self-destructs after use (Only effective when Type=Bomb and the vehicle is a drone helicopter)
Gravity = -0.04
GravityInWater = 0.0
;Projectile gravity acceleration (Positive=up, Negative=down. Larger absolute value = faster fall)
;GravityInWater is gravity in water.
GuidedTorpedo = true
;Torpedo guidance switch:
; true=Guided (flies to designated coordinates)
; false=Straight-running (moves straight after entering water)
TrajectoryParticle = flame
;Projectile trail particle effect type (missile trail, etc.):
; none None
; explode Explosion particles
; flame Flame particles
; hugeexplosion Large explosion particles
; largeexplode Big explosion particles
; largesmoke Large smoke particles
; smoke Smoke particles
;※ Particle parameter deprecated in 1.0.0, use AddMuzzleFlash / AddMuzzleFlashSmoke instead.
TrajectoryParticleStartTick = 10
;Delay in ticks before trajectory particles start generating.
DisableSmoke = true
;Disable weapon movement dust effect (not firing effect).
AddMuzzleFlash = 0.5, 0.20, 1, 150,254,219,184
;Parameters: Distance from source, Size, Duration, A,R,G,B (RGBA color)
;★Note: May not display correctly if firing interval (Delay) ≈ 5!
AddMuzzleFlashSmoke = 2.2, 1, 5.0, 2.0, 15, 180,250,245,240
;Parameters: Distance from source, Count, Size, Range, Duration, A,R,G,B
;★Note: May not display correctly if firing interval (Delay) ≈ 5!
SetCartridge = cartridge, 0.0, 0, 0, 2.00, -0.04, 0.40
;Cartridge ejection settings:
; SetCartridge = Model name, Initial velocity, Yaw offset, Pitch offset, Model scale, Gravity, Bounce
; Model name: all lowercase, half-width characters.
; Initial velocity: 0 = vertical drop.
; Yaw offset: Positive = eject left, Negative = eject right.
; Pitch offset: Positive = eject down, Negative = eject up.
; Model scale: Display scale.
; Gravity: Falling speed.
; Bounce: Collision bounce strength.
MaxAmmo = 40
;Maximum ammo capacity for the vehicle.
SuppliedNum = 10
;Amount of ammo received per supply action.
Item = 3, iron_ingot
Item = 4, gunpowder
Item = 2, redstone
;Items required for supply (only vanilla items supported).
;Example explanation:
;MaxAmmo=40, SuppliedNum=10
;One supply consumes Iron Ingot x3 + Gunpowder x4 + Redstone x2 → yields 10 ammo.
;To fully resupply 40 ammo, total consumption required: Iron Ingot x12 + Gunpowder x16 + Redstone x8.
BulletColor = 255, 255, 255, 255 ;RGBA Projectile color (in air)
BulletColorInWater = 255, 25, 25, 75 ;RGBA Projectile color (in water)
SmokeColor = 230, 200, 20, 80 ;RGBA Smoke color
SmokeSize = 2.0 ;Smoke size
SmokeMaxAge = 500 ;Smoke duration (ticks)
DisplayMortarDistance = true
;Display projectile impact point distance.
FixCameraPitch = true
;Lock camera vertical angle to 0 degrees.
CameraRotationSpeedPitch = 0.3
;Camera pitch rotation speed multiplier (Lower value = finer control).
DispenseItem = flint_and_steel
;Use item at impact point (Example: Flint and Steel)
;Valid items: water_bucket can extinguish fire/lava.
DispenseRange = 4
;Item effect range (unit: blocks).
Recoil = 1.1
;Recoil intensity.
RecoilBufCount = 40, 5
;Recoil parameters = Total recoil duration (ticks), Recoil process multiplier.
; Longer total duration = more sustained recoil.
; Higher multiplier = more intense recoil.
Target = monsters/others
;Targetable entities (supports multiple, / separated):
; planes Planes
; helicopters Helicopters
; vehicles Ground vehicles
; players Players
; monsters Monsters
; others Other entities
; block Block marking (This mode overrides other targets).
Length = 100
;Marking distance (unit: blocks).
Radius = 45
;Marking cone angle (45 = 45° cone).
MarkTime = 10
;Marking duration (seconds).
====================================== Updated 2025.10.8, parameters below are added by MCHeli-Reforged =====================================
flakParticlesCrack = 10
;Number of block break particles generated.
;Default=10
numParticlesFlak = 3
;Number of white smoke particles generated.
;Default=3
flakParticlesDiff = 0.3
;Spread of generated block break particles, recommended values 0.1 (rifle bullet) ~ 0.6 (anti-tank rifle).
;Default=0.3
hitSound = ""
;Sound effect when projectile hits. Add the corresponding audio filename after the = sign.
;Default=none
hitSoundIron = "hit_metal"
;Sound effect when projectile hits metal. Add the corresponding audio filename after the = sign.
;Default=hit_metal
railgunSound = "railgun"
;Charging sound effect for railgun type weapons.
;Default=railgun
;*Railgun charge time parameter: locktime = 20
hitSoundRange = 100
;Range for hit sound propagation.
;Default=100
isHeatSeekerMissile = true
;Whether it is an infrared missile, can be distracted by flares.
;Default=true
isRadarMissile = false
;Whether it is a radar missile, can be distracted by chaff.
;Default=false
maxDegreeOfMissile = 60
;Maximum seeker gimbal limit for the missile. Beyond this angle, the missile loses guidance.
;Default=60
tickEndHoming = -1
;Number of ticks after the missile loses lock before it stops homing. -1 means permanent lock.
;Default=-1
maxLockOnRange = 300
;Maximum lock-on range. Affected by vehicle's Stealth parameter. Actual lock range ≈ maxLockOnRange*(1-Stealth).
;Default=300
maxLockOnAngle = 10
;Aircraft radar maximum lock angle, can be thought of as FoV. Conversion formula with field of view radius r and distance d: r = d * tan(FoV / 2). maxLockOnAngle corresponds to FoV in the formula.
;Default=10
pdHDNMaxDegree = 180
;Velocity Gate Radar maximum angle. Beyond this angle, lock is lost. (Can also simulate rear-aspect IR missile attacks) (Bug suspected, only works for IR and semi-active radar missiles).
;Default=1000
pdHDNMaxDegreeLockOutCount = 10
;Velocity Gate Radar lockout count. After exceeding max angle, missile loses lock after this many ticks. (Bug suspected, not working).
;Default=10
antiFlareCount = -1
;Missile flare resistance duration. -1 means no resistance.
;Default=-1
lockMinHeight = 25
;Radar missile multipath clutter detection height. Target below this height causes radar missile to lose lock. (Only for AAMissile weapon type).
;Default=25
passiveRadar = false
;Whether it is a semi-active radar missile, requires continuous illumination (Left-click to fire, Right-click to lock and maintain illumination on target).
passiveRadarLockOutCount = 20
;Semi-active radar missile lock loss countdown after losing illumination. (Bug suspected, not working).
;Default=20
laserGuidance = false
;Enable laser guidance for TV missiles.
;Default=false
hasLaserGuidancePod = true
;Whether a laser targeting pod is present. true=can guide laser in free look, false=laser guidance direction is tied to aircraft nose.
;Default=true
enableOffAxis = true
;Allow off-boresight launch for AAMissile and ATMissile.
;Default=true
turningFactor = 0.1
;Missile maneuverability parameter. Smaller value = smoother maneuver. Value of 1 = original MCH missile maneuverability. Recommended value 0.25. (Note: Value should not be too small, or missile may fail to hit).
;Default=0.5
enableChunkLoader = false
;Whether to enable chunk loader. Ammunition can load chunks autonomously. (Experimental, suspected not to work on Uranium core servers).
;Default=false
activeRadar = false
;Whether it is an active radar missile, automatically tracks target after launch.
;Default=false
scanInterval = 20
;Active radar missile scan interval (Scans for targets within lock range every X ticks. If an enemy is found, it will track).
;Default=20
weaponSwitchCount = 0
;Weapon switch cooldown time.
;Default=0
weaponSwitchSound = ""
;Weapon switch sound effect.
;Default=none
recoilPitch = 0.0
;Weapon vertical recoil.
;Default=0.0
recoilYaw = 0.0
;Weapon horizontal recoil (fixed direction).
;Default=0.0
recoilPitchRange = 0.0
;Weapon random vertical recoil (Recoil 2 + rndRecoil 0.5 == 1.5-2.5 Recoil range).
;Default=0.0
recoilYawRange = 0.0
;Weapon random horizontal recoil.
;Default=0.0
recoilRecoverFactor = 0.8
;Weapon recoil recovery speed.
;Default=0.8
speedFactor = 0
;Speed change per tick. <0 decelerates, >0 accelerates.
;Default=0
speedFactorStartTick = 0
;Tick count after launch when the speed multiplier takes effect. speedFactorStartTick = 20 means speed change starts 20 ticks after launch.
;Default=0
speedFactorEndTick = 0
;Tick count after launch when the speed multiplier effect ends. speedFactorEndTick = 80 means speed change ends 80 ticks after launch.
;Default=0
speedDependsAircraft = false
;Whether speed depends on the launching aircraft. Final speed = aircraft current speed + projectile initial Acceleration + speedFactor*(speedFactorEndTick - speedFactorStartTick).
;Default=false
canLockMissile = false
;Whether it can lock onto missile entities.
;Default=false
enableBVR = false
;Enable Beyond Visual Range radar (requires server-side usage).
;Default=false
minRangeBVR = 300
;Minimum range for BVR target acquisition functionality.
;Default=300
predictTargetPos = true
;Whether the missile can predict entity position. (Not recommended, not very effective).
;Default=true
numLockedChaffMax = 2
;Maximum number of chaff locks. Exceeding this causes missile to fly straight. (Currently bugged, seems to only work when aircraft faces missile and deploys chaff).
;Default=2
explosionDamageVsLiving = 1
explosionDamageVsPlayer = 1
explosionDamageVsPlane = 1
explosionDamageVsVehicle = 1
explosionDamageVsTank = 1
explosionDamageVsHeli = 1
explosionDamageVsShip = 1
;Explosion damage multiplier against different entity types. Value of 2 = 2x explosion damage.
;Default=1
canBeIntercepted = false
;Whether the projectile entity can be intercepted. Recommended to set true for rocket and missile type weapons, false for conventional weapons.
;Default=false
canAirburst = false
;Whether programmable airburst functionality can be set (Right-click on a block to set airburst distance).
;Default=false
explosionAirburst
;Explosion radius when airburst is triggered, unit same as 'explosion'.
;If not set separately, defaults to the value of 'explosion'.
crossType = 0
;Custom HUD field for indicating crosshair/reticle HUD.
;Default=none
hasMortarRadar = false
;Whether it has artillery/mortar radar.
;Default=false
mortarRadarMaxDist = -1
;Artillery radar maximum display radius. Should be greater than the maximum range of the indirect fire weapon. (For indirect fire weapons, first measure max range at 45° elevation, then set the radar display radius).
;Default=-1
markerRocketSpawnNum = 5
;Number of bombs spawned by markerRocket.
;Default=5
markerRocketSpawnDiff = 15
;Spread of bombs spawned by markerRocket.
;Default=15
markerRocketSpawnHeight = 200
;Spawn height of bombs spawned by markerRocket.
;Default=200
markerRocketSpawnSpeed = 5
;Initial speed of bombs spawned by markerRocket.
;Default=5
nukeyield = 100
;Whether the weapon is an HBM nuclear weapon. =100 means nuclear blast radius is 100.
;Default=none
ExplosionType=hbmNT_Bomb
;Whether the weapon uses HBM bomb explosion effects.
;Default = none
ExplosionType=hbmNT_Shell
;Whether the weapon uses HBM artillery shell explosion effects.
;Default = none
effectyield = 10
;Blast radius for HBM conventional explosion effects (requires using ExplosionType=hbmNT_Shell or ExplosionType=hbmNT_Bomb).
;Value 1-4: small effect, 5-8: medium effect, ≥9: large effect.
;Default = none
NukeEffectOnly=true
;Enable HBM nuclear explosion effect without block destruction (requires nukeyield).
;Default = false
DisableDestroyBlock=true
;Enable HBM explosion effects without block destruction (requires using ExplosionType=hbmNT_Shell or ExplosionType=hbmNT_Bomb).
;Default = true

2016/04/17

;***********************************************************************************
;■ 武器配置文件 weapons/***.txt, sound/***_snd.ogg
;***********************************************************************************

;★ 重要 ★
;武器配置文件可在不关闭Minecraft的情况下重新加载。
;进入载具 → 按R键打开补给界面 → MOD选项 → 开发 → 重载所有武器
;此操作会重新加载所有武器（包括便携武器）。

;添加新武器需两个文件（全小写）：
; ・在weapons文件夹添加武器配置文件（.txt）
; ・在sound文件夹添加同名音效文件（格式：武器名_snd.ogg）
; 例如武器 abc 需要 weapons/abc.txt 和 sound/abc_snd.ogg
;※0.9.4+版本音效文件不再必须

;部分数值参数有上下限约束

DisplayName = M134 米尼岗机枪
;显示名称 ※请勿使用全角字符，仅限半角英数字及符号

Type = MachineGun1
;武器类型（可选以下其一）：
;	MachineGun1  固定朝向机枪（如 M134）
;	MachineGun2  随玩家视角转向机枪（如 M230）
;	Torpedo      鱼雷（入水后自动追踪目标，如 Mk46）
;	CAS          近距空中支援（如 A-10）
;	Rocket       固定朝向无制导火箭（如 Hydra70 / SNEB68mm）
;	ASMissile    空地导弹（打击地面坐标，如 AGM119）
;	AAMissile    空对空导弹（追踪空中生物，如 AIM92）
;	TVMissile    发射后玩家操控导弹（如 AGM114[TV]）
;	ATMissile    反坦克导弹（追踪地面生物，如 AGM114）
;	Bomb         垂直投放炸弹（如 CBU-100）
;	MkRocket     标记火箭（引导炮火打击落点，如 Hydra 70mm M264RP）
;	Dummy        虚拟武器（仅显示文字，不可用）
;	Smoke        烟幕弹（生成航迹云，如 White Smoke）
;	Dispenser    投射器（在落点使用物品，如 Water Dispenser）
;	TargetingPod 目标指示器（标记生物/玩家/方块，如 targeting_pod_block）
;	Railgun 电磁炮（需要蓄力发射）

Power = 8
;基础伤害值，1伤害=1滴血=半颗心

DamageFactor = tank, 2.0
;伤害倍率：
; 参数1：目标类型（player=玩家，heli/helicopter=直升机，plane=固定翼，tank=坦克/汽车，vehicle=地面载具）
; 参数2：伤害倍率（例：Power=10 + 倍率3.4 = 34点伤害）
;可添加多行配置不同目标的倍率

Acceleration = 4.0
;弹体速度（大部分武器上限4.0，MachineGun1/2和Rocket可至100.0，速度过高会导致弹体震颤）

AccelerationInWater = 4.0
;鱼雷水下速度（上限4.0）

VelocityInWater = 0.5
;水下加速度（每Tick乘此值调整速度）

Explosion = 0
;落地爆炸威力（0=无爆炸，1=等同于火焰弹威力）
ExplosionInWater = 0
;水下爆炸威力
ExplosionBlock = 0
;爆炸方块破坏力（0=不破坏方块）
ExplosionAltitude = 10
;最低起爆高度（距离地面≤10米时爆炸）

DelayFuse = 30
;延时引信：弹体存活Tick数（落地后计时）
;若Explosion非0，弹体消失时爆炸

Bound = 0.4
;弹跳强度（需配合DelayFuse使用，否则落地即爆）

TimeFuse = 30
;定时引信：弹体存活Tick数（发射后计时）
;若Explosion非0，弹体消失时爆炸

Flaming = false
;是否在落点散布火焰（仅当Explosion>0时生效）

Sight = MoveSight
;屏幕准星类型：
;	MoveSight   随载具移动的准星
;	MissileSight 目标锁定准星（AAMissile/ATMissile必须使用此类型）
;	None        无准星

Zoom = 4.2, 9.2
;仅限便携武器：默认倍率（逗号分隔可设多档，Z键切换）

Group = MainGun
;武器分组：
; 同组武器中任一件开火会触发全组装填
; 例：坦克主炮分设穿甲弹(APFSDS)、高爆弹(HE)、霰弹(Canister)三个配置文件均设 Group = MainGun
;     发射任意弹种后，其他弹种同步进入装填（弹药数不减）

Delay = 5
;开火间隔（单位：1/20秒，值越小射速越高）

ReloadTime = 80
;装填耗时（单位：1/20秒，值越小越快）
;※ 装填时间设为0时需确保装弹数>0

Round = 100
;装弹量（设为0或不填表示无限）

SoundVolume = 3
;开火音量（≥1.0时按最大音量播放，如需降低请设<1.0）

SoundPitch = 1.0
;音调（0.0~1.0）

SoundPitchRandom = 0.1
;音调随机浮动范围（例：SoundPitch=0.8 + 此值0.2 → 实际音调0.6~0.8）

SoundDelay = 1
;连发音效延迟（防M134等速射武器覆盖其他声音）

Sound = rocket_snd
;音效文件名（无需扩展名，不指定时默认加载 武器名_snd.ogg）

LockTime = 20
;导弹锁定耗时（值越大锁定越慢）

RidableOnly = true
;仅玩家乘坐载具时可锁定目标

ProximityFuseDist = 1.0
;导弹近炸引信距离（1.0=目标进入1米范围时爆炸）

RigidityTime = 0
;导弹发射后开始追踪的延迟Tick数（默认7）

Accuracy = 1
;非制导弹药散布误差（值越大越不准）

Bomblet = 25
;子母弹展开数量（用于集束炸弹等）
BombletSTime = 5
;子弹展开延迟时间（Tick）
BombletDiff = 0.7
;子弹散布范围

ModeNum = 2
;武器模式数（X键切换，仅以下类型生效）：
; MachineGun2 → 切换高爆弹（需Explosion>0）
; TVMissile   → 切换常规制导（非导弹视角）
; ATMissile   → 切换攻顶模式（Top Attack）
; Rocket      → 切换空爆弹（空中释放子炸弹）
; 当前仅支持1或2种模式

Piercing = 2
;方块穿透次数上限
;现版本会导致多次爆炸，每个数值代表1次爆炸

HeatCount = 20
;单次开火增加的热量值
MaxHeatCount = 150
;热量上限

FAE = true
;燃料空气炸弹开关（true启用）
;注：此类炸弹不破坏方块

ModelBullet = bullet
ModelBomblet = cbc
;弹体模型文件：
; 示例：加载 models/bullets/bullet.obj + textures/bullets/bullet.png
; 子弹模型：models/bullets/cbc.obj + textures/bullets/cbc.png

Destruct = true
;使用后载具自毁（仅限Type=Bomb且为无人机直升机时生效）

Gravity = -0.04
GravityInWater = 0.0
;弹体重力加速度（正值向上，负值向下，绝对值越大下落越快）
;GravityInWater为水下重力

GuidedTorpedo = true
;鱼雷制导开关：
; true=制导（飞向指定坐标）
; false=直航（入水后直线前进）

TrajectoryParticle = flame
;弹道粒子特效类型（导弹尾迹等）：
; none          无
; explode       爆炸粒子
; flame         火焰粒子
; hugeexplosion 大型爆炸粒子
; largeexplode  大爆炸粒子
; largesmoke    大烟雾粒子
; smoke         烟雾粒子
;※ Particle参数在1.0.0弃用，改用 AddMuzzleFlash / AddMuzzleFlashSmoke

TrajectoryParticleStartTick = 10
;弹道粒子开始生成的延迟Tick数

DisableSmoke = true
;禁用武器移动扬尘特效（非开火特效）

AddMuzzleFlash  =  0.5,       0.20,  1,  150,254,219,184
;参数：距发射源距离, 尺寸, 持续时间, A,R,G,B（颜色RGBA）
;★注意：开火间隔≈5时可能无法正常显示！

AddMuzzleFlashSmoke  =  2.2,       1,    5.0,   2.0,  15,  180,250,245,240
;参数：距发射源距离, 数量, 尺寸, 范围, 持续时间, A,R,G,B
;★注意：开火间隔≈5时可能无法正常显示！

SetCartridge = cartridge, 0.0, 0, 0, 2.00, -0.04, 0.40
;抛壳设置：
; SetCartridge = 模型名, 初速, 偏航角, 俯仰角, 模型缩放, 重力, 弹跳
; 模型名：全小写半角名称
; 初速：0=垂直下落
; 偏航角：正值左抛，负值右抛
; 俯仰角：正值下抛，负值上抛
; 模型缩放：显示比例
; 重力：下坠速度
; 弹跳：碰撞反弹强度

MaxAmmo = 40
;载具最大携弹量
SuppliedNum = 10
;单次补给获得弹药数
Item =  3, iron_ingot
Item =  4, gunpowder
Item =  2, redstone
;补给所需物品及数量（仅支持原版物品）

;示例说明：
;MaxAmmo=40, SuppliedNum=10
;单次补给消耗铁锭x3+火药x4+红石x2 → 获得10发弹药
;补满40发需累计消耗：铁锭x12+火药x16+红石x8

BulletColor        = 255, 255, 255, 255 ;RGBA弹体颜色（空中）
BulletColorInWater = 255,  25,  25,  75 ;RGBA弹体颜色（水下）

SmokeColor  = 230, 200, 20, 80 ;RGBA烟雾颜色
SmokeSize   = 2.0   ;烟雾尺寸
SmokeMaxAge = 500   ;烟雾存续时间（Tick）

DisplayMortarDistance = true
;显示弹道落点距离

FixCameraPitch = true
;锁定摄像机垂直角度为0度

CameraRotationSpeedPitch = 0.3
;摄像机俯仰角转速倍率（值越小区分度越高）

DispenseItem = flint_and_steel
;在落点使用物品（示例：打火石）
;有效物品：水桶(water_bucket)可扑灭火焰/岩浆

DispenseRange = 4
;物品作用范围（单位：方块）

Recoil = 1.1
;后坐力强度

RecoilBufCount = 40, 5
;后坐参数 = 后坐总时长(Tick), 后坐过程倍率
; 总时长越长后坐越持久
; 倍率越高后坐越剧烈

Target = monsters/others
;可标记目标（支持多选，/分隔）：
; planes       固定翼
; helicopters  直升机
; vehicles     地面载具
; players      玩家
; monsters     怪物
; others       其他生物
; block        方块标记（此模式会覆盖其他目标）

Length = 100
;标记距离（单位：方块）

Radius = 45
;标记范围角度（45=45°锥形范围）

MarkTime = 10
;标记持续时间（秒）

======================================2025.10.8更新，以下为MCHeli-Reforged新增的参数=====================================
flakParticlesCrack = 10
;生成的方块破碎粒子数量
;默认值=10

numParticlesFlak = 3
;生成的白色烟雾粒子数量
;默认值=3
 
flakParticlesDiff = 0.3;
;生成的方块破碎粒子扩散，推荐值0.1(步枪子弹) ~ 0.6(反坦克步枪)
;默认值=0.3

hitSound = ""
;弹体命中时的音效，=号后添加相应的音频文件名
;默认值=无

hitSoundIron = "hit_metal"
;弹体击中金属物体时的音效，=号后添加相应音频文件名
;默认=hit_metal

railgunSound = "railgun"
;railgun类型武器的蓄力音效
;默认值=railgun
;*电磁炮蓄力时间参数：locktime = 20

hitSoundRange = 100
命中音效的传播距离;
;默认值=100
 
isHeatSeekerMissile = true
;是否为红外弹，会受到热焰弹干扰
;默认值=true
 
isRadarMissile = false
;是否为雷达弹，会受到箔条干扰
;默认值=false
 
maxDegreeOfMissile = 60
;弹药导引头最大导引角度，超过该角度导弹不制导
;默认值=60
 
tickEndHoming = -1
;导弹脱离锁定后在多少时间（tick）会脱锁，-1为永远锁定
;默认值=-1
 
maxLockOnRange = 300
;最大锁定距离。会受载具Stealth参数影响，实际锁定距离约等于maxLockOnRange*(1-Stealth)
;默认值=300
 
maxLockOnAngle = 10
;机载雷达最大锁定角度，可理解为FoV。与视场半径r，距离d的换算公式为r = d * tan(FoV / 2)。maxLockOnAngle就相当于公式中的FoV
;默认值=10
 
pdHDNMaxDegree = 180
;速度门雷达最大角度，超过此角度将脱锁 (也可用于模拟红外弹尾后攻击)(疑似存在bug，只对红外弹和半主动雷达弹生效)
;默认值=1000
 
pdHDNMaxDegreeLockOutCount = 10
;速度门雷达脱锁间隔，超过最大角度后，在该tick后导弹脱锁(疑似存在bug，不生效)
;默认值=10
 
antiFlareCount = -1
;导弹抗干扰时长，-1为不抗干扰
;默认值=-1
 
lockMinHeight = 25
;雷达导弹多径杂波检测高度，目标低于这个高度将使雷达弹脱锁(仅对AAmissile武器类型有用)
;默认值=25
 
passiveRadar = false
;是否为半主动雷达弹，需要持续引导(左键发射，右键锁定敌机持续引导)
 
passiveRadarLockOutCount = 20
;半主动雷达弹脱离引导后脱离锁定倒计时(疑似有bug，不生效)
;默认值=20
 
laserGuidance = false
;对TV导弹启用激光制导
;默认值=false

hasLaserGuidancePod = true
;是否有激光吊舱，true=可以自由视角引导激光，false=激光引导方向和机头指向绑定
;默认值=true

enableOffAxis = true
;允许离轴射击AAmissile和ATmissile
;默认值=true
 
turningFactor = 0.1
;导弹机动参数，数值越小机动越平滑，值设为1时为原版MCH导弹机动性，推荐值为0.25(注意，该数值不宜过小，否则可能会使得导弹打不中人)
;默认值=0.5
 
enableChunkLoader = false
;是否启用区块加载器，弹药可自主加载区块(试验功能，疑似Uranium核心服务端不生效)
;默认值=false
 
activeRadar = false
;是否为主动雷达弹，发射后自动追踪目标
;默认值=false

scanInterval = 20
;主动雷达弹 扫描间隔(每隔一定tick，对锁定范围内的目标扫描一次，若有敌机，则会追踪敌机)
;默认值=20
 
weaponSwitchCount = 0
;武器切换冷却时间
;默认值=0
 
weaponSwitchSound = ""
;武器切换音效
;默认值=无
 
recoilPitch = 0.0
;武器垂直后坐力
;默认值=0
 
recoilYaw = 0.0
;武器水平后坐力（固定方向）
;默认值=0
 
recoilPitchRange = 0.0
;武器随机垂直后坐力 (Recoil 2 + rndRecoil 0.5 == 1.5-2.5 Recoil range)
;默认值=0
 
recoilYawRange = 0.0
;武器随机水平后坐力
;默认值=0
 
recoilRecoverFactor = 0.8
;武器后坐力恢复速度
;默认值=0.8
 
speedFactor = 0 
;每tick速度增加数值，小于0减速，大于0加速
;默认值=0
 
speedFactorStartTick = 0
;每tick的速度乘数生效时长，speedFactorStartTick = 20=在发射20tick后开始速度变化
;默认值=0
 
speedFactorEndTick = 0
;每tick的速度乘数结束时间,speedFactorEndTick = 80=在发射80tick后结束速度变化
;默认值=0
 
speedDependsAircraft = false
;速度是否跟随载机，最终速度 = 载机当前speed + 弹药初始Acceleration+speedFactor*(speedFactorEndTick-speedFactorStartTick)
;默认值=false
 
canLockMissile = false
;是否可以锁定导弹实体
;默认值=false
 
enableBVR = false
;启用超视距雷达(需要在服务端使用)
;默认值=false
 
minRangeBVR = 300
;超视距索敌功能最小启用距离
;默认值=300
 
predictTargetPos = true
;导弹是否可以预测实体位置(不好用，不推荐)
;默认值=true
 
numLockedChaffMax = 2
;锁定箔条的最大次数，超过此次数导弹将变为直射状态（目前有bug，疑似只有战机正面对准导弹抛洒箔条时才能生效）
;默认值=2
 
explosionDamageVsLiving = 1
explosionDamageVsPlayer = 1
explosionDamageVsPlane = 1
explosionDamageVsVehicle = 1
explosionDamageVsTank = 1
explosionDamageVsHeli = 1
explosionDamageVsShip = 1
;对不同实体类型的爆炸伤害倍率,数值为2=2倍爆炸伤害
;默认值=1


canBeIntercepted = false
;弹药实体是否可以被拦截，推荐rocket和missile类型武器设置为true，常规武器设置为false
;默认=false

canAirburst = false
;是否可以设定可编程空爆功能(对准方块右键装订空爆距离)
;默认=false

explosionAirburst
;触发空爆时的爆炸范围，单位等同于explosion
;如不单独设定默认=explosion的数值

crossType = 0
;hud自定义字段，用于指示准星hud
;默认=无
 
hasMortarRadar = false
;是否有炮兵雷达
;默认=false
 
mortarRadarMaxDist = -1
;炮兵雷达最大显示半径，应大于曲射武器的最大射程(对于曲射武器建议先在45度仰角情况下测量最大射程，然后再设置炮兵雷达的显示半径)
;默认=-1

markerRocketSpawnNum = 5
;markerRocket召唤的炸弹数量
;默认值=5

markerRocketSpawnDiff = 15
;markerRocket召唤的炸弹散布
;默认值=15

markerRocketSpawnHeight = 200
;markerRocket召唤的炸弹的生成高度
;默认值=200

markerRocketSpawnSpeed = 5
;markerRocket召唤的炸弹生成时的速度
;默认值=5

nukeyield = 100
;武器是否为HBM核弹，=100时核弹破坏半径为100
;默认值=无

ExplosionType=hbmNT_Bomb
;武器爆炸特效是否采用HBM炸弹爆炸特效
;默认值 = 无

ExplosionType=hbmNT_Shell
;武器爆炸特效是否采用HBM火炮爆炸特效
;默认值 = 无

effectyield = 10
;启用HBM常规爆炸特效时武器的破坏半径（需搭配ExplosionType=hbmNT_Shell/ExplosionType=hbmNT_Bomb使用）
;值=1-4时为小规模特效，5-8时为中型特效，≥9时为大型特效
;默认值 = 无

NukeEffectOnly=true
;启用HBM核爆炸特效时不破坏方块（需搭配nukeyield使用）
;默认值 = false

DisableDestroyBlock=true
;启用HBM爆炸特效时不破坏方块（需搭配ExplosionType=hbmNT_Shell/ExplosionType=hbmNT_Bomb使用）
;默认值 = true

​​2016/04/17​​
;​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​*​
;■ 武器設定ファイル weapons/​​.txt, sound/​​_snd.ogg
;​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​​*​
;★ 重要 ★
;武器設定ファイルはMinecraftを終了せずに再読み込みできます。
;ビークル搭乗 → Rキーで補給画面を開く → MODオプション → 開発 → 全武器リロード
;この操作で全ての武器（携帯武器を含む）が再読み込みされます。
;新しい武器を追加するには2つのファイル（全て小文字）が必要です：
; ・weaponsフォルダに武器設定ファイル（.txt）を追加
; ・soundフォルダに同名のサウンドファイル（形式：武器名_snd.ogg）を追加
; 例：武器 abc には weapons/abc.txt と sound/abc_snd.ogg が必要
;※バージョン0.9.4以降、サウンドファイルは必須ではなくなりました
;一部の数値パラメータには上限・下限の制約があります。
DisplayName = M134 ミニガン
;表示名 ※全角文字は使用不可、半角英数字及び記号のみ使用可
Type = MachineGun1
;武器タイプ（以下のいずれかから選択）：
; MachineGun1 固定方向機銃（例：M134）
; MachineGun2 プレイヤー視点連動機銃（例：M230）
; Torpedo 魚雷（水中進入後自動追跡、例：Mk46）
; CAS 近接航空支援（例：A-10）
; Rocket 固定方向無誘導ロケット（例：Hydra70 / SNEB68mm）
; ASMissile 空対地ミサイル（地上座標攻撃、例：AGM119）
; AAMissile 空対空ミサイル（空中生物追跡、例：AIM92）
; TVMissile 発射後プレイヤー操縦ミサイル（例：AGM114[TV]）
; ATMissile 対戦車ミサイル（地上生物追跡、例：AGM114）
; Bomb 垂直投下爆弾（例：CBU-100）
; MkRocket 標定ロケット（着弾点へ砲撃誘導、例：Hydra 70mm M264RP）
; Dummy ダミー兵器（文字表示のみ、使用不可）
; Smoke スモーク弾（航跡雲生成、例：White Smoke）
; Dispenser ディスペンサー（着弾点でアイテム使用、例：Water Dispenser）
; TargetingPod 目標指示器（生物/プレイヤー/ブロック標識、例：targeting_pod_block）
; Railgun レールガン（チャージ発射必要）
Power = 8
;基本ダメージ値、1ダメージ=ハート半個分
DamageFactor = tank, 2.0
;ダメージ倍率：
; パラメータ1：目標タイプ（player=プレイヤー, heli/helicopter=ヘリコプター, plane=固定翼機, tank=戦車/車両, vehicle=地上ビークル）
; パラメータ2：ダメージ倍率（例：Power=10 + 倍率3.4 = 34ダメージ）
;複数行追加で異なる目標への倍率を設定可能
Acceleration = 4.0
;弾体速度（大半の武器は最大4.0、MachineGun1/2とRocketは100.0まで可能、速度過多で弾体震え発生）
AccelerationInWater = 4.0
;魚雷水中速度（最大4.0）
VelocityInWater = 0.5
;水中加速度（1ティック毎にこの値を乗算して速度調整）
Explosion = 0
;着弾爆発威力（0=爆発無し、1=ファイヤーボール同等威力）
ExplosionInWater = 0
;水中爆発威力
ExplosionBlock = 0
;爆発ブロック破壊力（0=ブロック破壊無し）
ExplosionAltitude = 10
;最低起爆高度（地面から≤10メートルで爆発）
DelayFuse = 30
;遅延信管：弾体存続ティック数（着弾後計時）
;Explosionが0でない場合、弾体消滅時に爆発
Bound = 0.4
;跳弾強度（DelayFuse設定必須、否则着弾即爆）
TimeFuse = 30
;定时信管：弾体存続ティック数（発射後計時）
;Explosionが0でない場合、弾体消滅時に爆発
Flaming = false
;着弾点で炎を散布するか（Explosion>0時のみ有効）
Sight = MoveSight
;画面照準タイプ：
; MoveSight ビークル連動照準
; MissileSight 目標ロック照準（AAMissile/ATMissile必須）
; None 照準無し
Zoom = 4.2, 9.2
;携帯武器専用：デフォルトズーム倍率（カンマ区切りで複数段階設定、Zキー切替）
Group = MainGun
;武器グループ：
; 同グループ内いずれかの武器発射で全グループ再装填
; 例：戦車主砲にAPFSDS、HE、Canisterの3設定ファイル全て Group = MainGun 設定
; 任意の弹種発射後、他弹種も同時に再装填（弾数減らず）
Delay = 5
;発射間隔（単位：1/20秒、値越小射速越高）
ReloadTime = 80
;再装填時間（単位：1/20秒、値越小速い）
;※ 装填時間0設定時は弾数>0を確認要
Round = 100
;装弾数（0または未設定で無限）
SoundVolume = 3
;発射音量（≥1.0で最大音量再生、音量下げる場合<1.0設定）
SoundPitch = 1.0
;音程（0.0~1.0）
SoundPitchRandom = 0.1
;音程ランダム変動範囲（例：SoundPitch=0.8 + 此値0.2 → 实际音程0.6~0.8）
SoundDelay = 1
;連発音遅延（M134等速射武器他音声上書き防止）
Sound = rocket_snd
;サウンドファイル名（拡張子不要、未設定時デフォルト：武器名_snd.ogg）
LockTime = 20
;ミサイルロックオン時間（値大なる程ロック遅い）
RidableOnly = true
;プレイヤービークル搭乗時のみ目標ロック可能
ProximityFuseDist = 1.0
;ミサイル近接信管作動距離（1.0=目標1メートル圏内で爆発）
RigidityTime = 0
;ミサイル発射後追跡開始遅延ティック数（デフォルト7）
Accuracy = 1
;無誘導弾薬散布誤差（値大なる程精度低い）
Bomblet = 25
;子弾展開数（クラスター爆弾等用）
BombletSTime = 5
;子弾展開遅延時間（ティック）
BombletDiff = 0.7
;子弾散布範囲
ModeNum = 2
;武器モード数（Xキー切替、以下タイプでのみ有効）：
; MachineGun2 → 榴弾切替（要Explosion>0）
; TVMissile → 通常誘導切替（ミサイル視点非使用）
; ATMissile → トップアタックモード切替
; Rocket → 空中炸裂弾切替（空中子爆弾放出）
; 現在1或2モードのみ対応
Piercing = 2
;ブロック貫通回数上限
;現バージョン複数爆発発生、各数値1回爆発対応
HeatCount = 20
;1発射毎増加熱量
MaxHeatCount = 150
;熱量上限
FAE = true
;燃料気化爆弾（熱圧爆弾）スイッチ（true有効）
;注：此爆弾ブロック破壊無し
ModelBullet = bullet
ModelBomblet = cbc
;弾体モデルファイル：
; 例：models/bullets/bullet.obj + textures/bullets/bullet.png 読込
; 子弾モデル：models/bullets/cbc.obj + textures/bullets/cbc.png
Destruct = true
;使用後ビークル自爆（Type=Bomb且ドローンヘリ時のみ有効）
Gravity = -0.04
GravityInWater = 0.0
;弾体重力加速度（正値=上向、負値=下向、絶対値大なる程落下速い）
;GravityInWater水中重力
GuidedTorpedo = true
;魚雷誘導スイッチ：
; true=誘導（指定座標へ飛行）
; false=直進（水中進入後直進）
TrajectoryParticle = flame
;弾道粒子効果タイプ（ミサイル尾煙等）：
; none 無し
; explode 爆発粒子
; flame 炎粒子
; hugeexplosion 大型爆発粒子
; largeexplode 大爆発粒子
; largesmoke 大煙粒子
; smoke 煙粒子
;※ Particle参数1.0.0非推奨、AddMuzzleFlash / AddMuzzleFlashSmoke 使用
TrajectoryParticleStartTick = 10
;弾道粒子生成開始遅延ティック数
DisableSmoke = true
;武器移動土煙効果無効（発射特效非該当）
AddMuzzleFlash = 0.5, 0.20, 1, 150,254,219,184
;参数：発射源距離, 尺寸, 持続時間, A,R,G,B（色RGBA）
;★注意：発射間隔≈5時正常表示不可能！
AddMuzzleFlashSmoke = 2.2, 1, 5.0, 2.0, 15, 180,250,245,240
;参数：発射源距離, 数量, 尺寸, 範囲, 持続時間, A,R,G,B
;★注意：発射間隔≈5時正常表示不可能！
SetCartridge = cartridge, 0.0, 0, 0, 2.00, -0.04, 0.40
;薬莢排出設定：
; SetCartridge = モデル名, 初速, 偏角, 俯角, モデル縮尺, 重力, 跳弾
; モデル名：全角小文字名称
; 初速：0=垂直落下
; 偏角：正値=左投、負値=右投
; 俯角：正値=下投、負値=上投
; モデル縮尺：表示比率
; 重力：落下速度
; 跳弾：衝突反発強度
MaxAmmo = 40
;ビークル最大携行弾数
SuppliedNum = 10
;1回補給獲得弾数
Item = 3, iron_ingot
Item = 4, gunpowder
Item = 2, redstone
;補給必要物品及数量（バニラ物品対応）
;示例説明：
;MaxAmmo=40, SuppliedNum=10
;1回補給鉄インゴットx3+火薬x4+レッドストーンx2消費 → 10発弾薬獲得
;満タン40発累計消費：鉄インゴットx12+火薬x16+レッドストーンx8
BulletColor = 255, 255, 255, 255 ;RGBA弾体色（空中）
BulletColorInWater = 255, 25, 25, 75 ;RGBA弾体色（水中）
SmokeColor = 230, 200, 20, 80 ;RGBA煙色
SmokeSize = 2.0 ;煙尺寸
SmokeMaxAge = 500 ;煙存続時間（ティック）
DisplayMortarDistance = true
;弾道着弾点距離表示
FixCameraPitch = true
;カメラ垂直角度0度固定
CameraRotationSpeedPitch = 0.3
;カメラ俯仰角回転速度倍率（値小なる程区分度高）
DispenseItem = flint_and_steel
;着弾点物品使用（例：火打石）
;有効物品：水バケツ(water_bucket)炎/溶岩消火可
DispenseRange = 4
;物品作用範囲（単位：ブロック）
Recoil = 1.1
;反動強度
RecoilBufCount = 40, 5
;反動参数 = 反動総時間(ティック), 反動過程倍率
; 総時間長い程反動持続
; 倍率高い程反動激烈
Target = monsters/others
;標的可能目標（複数選択可、/区切り）：
; planes 固定翼機
; helicopters ヘリコプター
; vehicles 地上ビークル
; players プレイヤー
; monsters モブ
; others 其他生物
; block ブロック標識（此モード他目標上書き）
Length = 100
;標的距離（単位：ブロック）
Radius = 45
;標的範囲角度（45=45°円錐範囲）
MarkTime = 10
;標的持続時間（秒）
====================================== 2025.10.8 更新、以下 MCHeli-Reforged 追加参数 =====================================
flakParticlesCrack = 10
;生成ブロック破壊粒子数
;デフォルト=10
numParticlesFlak = 3
;生成白煙粒子数
;デフォルト=3
flakParticlesDiff = 0.3
;生成ブロック破壊粒子拡散、推奨値0.1(小銃弾) ~ 0.6(対戦車銃)
;デフォルト=0.3
hitSound = ""
;弾体命中時音效、=号後相应音声ファイル名追加
;デフォルト=無し
hitSoundIron = "hit_metal"
;弾体金属物体命中時音效、=号後相应音声ファイル名追加
;デフォルト=hit_metal
railgunSound = "railgun"
;railgun类型武器チャージ音效
;デフォルト=railgun
;*レールガンチャージ時間参数：locktime = 20
hitSoundRange = 100
;命中音效伝播距離
;デフォルト=100
isHeatSeekerMissile = true
;赤外線誘導弾可否、フレア妨害受ける
;デフォルト=true
isRadarMissile = false
;レーダー誘導弾可否、チャフ妨害受ける
;デフォルト=false
maxDegreeOfMissile = 60
;弾薬シーカー最大誘導角度、此角度超えると誘導不能
;デフォルト=60
tickEndHoming = -1
;ミサイルロック解除後何ティックで誘導停止、-1は永久ロック
;デフォルト=-1
maxLockOnRange = 300
;最大ロックオン距離。ビークルStealth参数影響、实际ロック距離≈maxLockOnRange*(1-Stealth)
;デフォルト=300
maxLockOnAngle = 10
;機上レーダー最大ロック角度、FoVと理解可。視野半径r、距離d換算式：r = d * tan(FoV / 2)。maxLockOnAngleは公式中FoV相当
;デフォルト=10
pdHDNMaxDegree = 180
;速度ゲートレーダー最大角度、此角度超えるとロック解除（赤外線弾後方攻撃模擬也可）（不具合疑、赤外線弾とセミアクティブレーダー弾のみ有効）
;デフォルト=1000
pdHDNMaxDegreeLockOutCount = 10
;速度ゲートレーダーロック解除間隔、最大角度超えた後、此ティック後ミサイルロック解除（不具合疑、無効）
;デフォルト=10
antiFlareCount = -1
;ミサイルフレア抵抗時間、-1は無抵抗
;デフォルト=-1
lockMinHeight = 25
;レーダーミサイル多重経路雑音検出高度、目標此高度未満でレーダー弾ロック解除（AAmissile武器タイプのみ有効）
;デフォルト=25
passiveRadar = false
;セミアクティブレーダー弾可否、継続照射必要（左クリック発射、右クリック目標ロック継続照射）
passiveRadarLockOutCount = 20
;セミアクティブレーダー弾照射中断後ロック解除カウントダウン（不具合疑、無効）
;デフォルト=20
laserGuidance = false
;TVミサイル対しレーザー誘導有効
;デフォルト=false
hasLaserGuidancePod = true
;レーザー標定ポッド有無、true=自由視点誘導可、false=レーザー誘導方向機首方向連動
;デフォルト=true
enableOffAxis = true
;AAmissileとATmissileのオフボアサイト射撃許可
;デフォルト=true
turningFactor = 0.1
;ミサイル機動性参数。値小なる程機動滑らか。値1=原版MCHミサイル機動性。推奨値0.25（注：値小さ過ぎると命中不能可能性）
;デフォルト=0.5
enableChunkLoader = false
;チャンクローダー有効可否、弾薬自律的チャンク読込（実験的機能、Uraniumコアサーバー無効疑）
;デフォルト=false
activeRadar = false
;アクティブレーダー弾可否、発射後自動追跡
;デフォルト=false
scanInterval = 20
;アクティブレーダー弾 走査間隔（一定ティック毎、ロック範囲内目標走査、敵機発見時追跡）
;デフォルト=20
weaponSwitchCount = 0
;武器切替クールダウン時間
;デフォルト=0
weaponSwitchSound = ""
;武器切替音效
;デフォルト=無し
recoilPitch = 0.0
;武器垂直反動
;デフォルト=0.0
recoilYaw = 0.0
;武器水平反動（固定方向）
;デフォルト=0.0
recoilPitchRange = 0.0
;武器ランダム垂直反動 (Recoil 2 + rndRecoil 0.5 == 1.5-2.5 Recoil range)
;デフォルト=0.0
recoilYawRange = 0.0
;武器ランダム水平反動
;デフォルト=0.0
recoilRecoverFactor = 0.8
;武器反動回復速度
;デフォルト=0.8
speedFactor = 0
;1ティック毎速度増加数値、<0減速、>0加速
;デフォルト=0
speedFactorStartTick = 0
;速度乗数発効開始時間、speedFactorStartTick = 20=発射20ティック後速度変化開始
;デフォルト=0
speedFactorEndTick = 0
;速度乗数効果終了時間、speedFactorEndTick = 80=発射80ティック後速度変化終了
;デフォルト=0
speedDependsAircraft = false
;速度発射機依存可否、最終速度 = 発射機現在速度 + 弾薬初期Acceleration+speedFactor*(speedFactorEndTick-speedFactorStartTick)
;デフォルト=false
canLockMissile = false
;ミサイル実体ロック可能可否
;デフォルト=false
enableBVR = false
;超視距レーダー有効（サーバー側使用必要）
;デフォルト=false
minRangeBVR = 300
;超視距索敵機能最小作動距離
;デフォルト=300
predictTargetPos = true
;ミサイル実体位置予測可否（非推奨、効果薄）
;デフォルト=true
numLockedChaffMax = 2
;チャフロック最大回数、此回数超えるとミサイル直進状態（現在不具合、戦機正面ミサイル向けチャフ投擲時のみ有効疑）
;デフォルト=2
explosionDamageVsLiving = 1
explosionDamageVsPlayer = 1
explosionDamageVsPlane = 1
explosionDamageVsVehicle = 1
explosionDamageVsTank = 1
explosionDamageVsHeli = 1
explosionDamageVsShip = 1
;異なる実体タイプ対する爆発ダメージ倍率,数値2=2倍爆発ダメージ
;デフォルト=1
canBeIntercepted = false
;弾薬実体迎撃可能可否、rocketとmissile类型武器true設定推奨、常规武器false設定推奨
;デフォルト=false
canAirburst = false
;プログラマブル空中炸裂機能設定可能可否（ブロック対し右クリック炸裂距離設定）
;デフォルト=false
explosionAirburst
;空中炸裂時爆発範囲、単位explosion同等
;個別設定無い場合デフォルト=explosion数値
crossType = 0
;HUDカスタム字段、照準HUD指示用
;デフォルト=無し
hasMortarRadar = false
;砲兵レーダー有無
;デフォルト=false
mortarRadarMaxDist = -1
;砲兵レーダー最大表示半径、曲射武器最大射程より大設定要（曲射武器先ず45度仰角最大射程測定後、砲兵レーダー表示半径設定推奨）
;デフォルト=-1
markerRocketSpawnNum = 5
;markerRocket召喚爆弾数
;デフォルト=5
markerRocketSpawnDiff = 15
;markerRocket召喚爆弾散布
;デフォルト=15
markerRocketSpawnHeight = 200
;markerRocket召喚爆弾生成高度
;デフォルト=200
markerRocketSpawnSpeed = 5
;markerRocket召喚爆弾生成時速度
;デフォルト=5
nukeyield = 100
;武器HBM核兵器可否、=100時核爆発半径100
;デフォルト=無し
ExplosionType=hbmNT_Bomb
;武器爆発特效HBM爆弾爆発特效採用可否
;デフォルト = 無し
ExplosionType=hbmNT_Shell
;武器爆発特效HBM火砲爆発特效採用可否
;デフォルト = 無し
effectyield = 10
;HBM常规爆発特效有効時武器破壊半径（ExplosionType=hbmNT_Shell/ExplosionType=hbmNT_Bomb使用要）
;値=1-4小規模特效、5-8中規模特效、≥9大規模特效
;デフォルト = 無し
NukeEffectOnly=true
;HBM核爆発特效有効時ブロック破壊無し（nukeyield使用要）
;デフォルト = false
DisableDestroyBlock=true
;HBM爆発特效有効時ブロック破壊無し（ExplosionType=hbmNT_Shell/ExplosionType=hbmNT_Bomb使用要）
;デフォルト = true
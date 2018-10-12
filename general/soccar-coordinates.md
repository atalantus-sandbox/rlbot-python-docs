# Soccar Coordinates

Rocket League is made in Unreal Engine, which means any dimensions will be in unreal units \(uu\).

### Basic Dimensions

**WARNING:** Note that, the X axis is left and it is not the normal cartesian layout.

Rocket League uses a coordinate system \(X,Y,Z\), where Z is upwards. Note also that **negative Y is towards Blue's goal \(team 0\)**.

* Floor: 0
* Center field: \(0, 0\)
* Side wall: 4096
* Back wall: 5120
* Ceiling: 2044
* Goal height: 642.775
* Goal center-to-post: 892.755

![](https://imgur.com/hrHKLnh.png)

### Boost Pads

Small boost pads:

* 28 in total.
* Gives 12 boost.
* Takes 4 seconds to refresh.

Big boost pads:

* 6 in total.
* Gives 100 boost.
* Takes 10 seconds to refresh.
* The pads with a z-component of 73.0 are the big pads. Mirror these coordinates to get all 6:
  * Midfield: \(3584, 0\)
  * Corner: \(3072, 4096\)

The coordinates of the 34 boost pads \(in the order that RLBot uses\):

![](https://i.imgur.com/HGuoLyt.png)

```text
[    0.0, -4240.0, 70.0] (0)
[-1792.0, -4184.0, 70.0] (1)
[ 1792.0, -4184.0, 70.0] (2)
[-3072.0, -4096.0, 73.0] (3)
[ 3072.0, -4096.0, 73.0] (4)
[- 940.0, -3308.0, 70.0] (5)
[  940.0, -3308.0, 70.0] (6)
[    0.0, -2816.0, 70.0] (7)
[-3584.0, -2484.0, 70.0] (8)
[ 3584.0, -2484.0, 70.0] (9)
[-1788.0, -2300.0, 70.0] (10)
[ 1788.0, -2300.0, 70.0] (11)
[-2048.0, -1036.0, 70.0] (12)
[    0.0, -1024.0, 70.0] (13)
[ 2048.0, -1036.0, 70.0] (14)
[-3584.0,     0.0, 73.0] (15)
[-1024.0,     0.0, 70.0] (16)
[ 1024.0,     0.0, 70.0] (17)
[ 3584.0,     0.0, 73.0] (18)
[-2048.0,  1036.0, 70.0] (19)
[    0.0,  1024.0, 70.0] (20)
[ 2048.0,  1036.0, 70.0] (21)
[-1788.0,  2300.0, 70.0] (22)
[ 1788.0,  2300.0, 70.0] (23)
[-3584.0,  2484.0, 70.0] (24)
[ 3584.0,  2484.0, 70.0] (25)
[    0.0,  2816.0, 70.0] (26)
[- 940.0,  3310.0, 70.0] (27)
[  940.0,  3308.0, 70.0] (28)
[-3072.0,  4096.0, 73.0] (29)
[ 3072.0,  4096.0, 73.0] (30)
[-1792.0,  4184.0, 70.0] (31)
[ 1792.0,  4184.0, 70.0] (32)
[    0.0,  4240.0, 70.0] (33)
```

**NOTE:** Some boost pad locations varies from map to map. It is recommended to use the [FieldInfo](https://github.com/RLBot/RLBotPythonExample/wiki/Input-and-Output-Data#field-info), if you want to have the correct locations for any map.

### Spawn Locations

| Kickoff | Blue | Orange |
| :--- | :--- | :--- |
| Right corner | loc: \(-1952, -2464\), yaw: 0.25 pi | loc: \(1952, 2464\), yaw: -0.75 pi |
| Left corner | loc: \(1952, -2464\), yaw: 0.75 pi | loc: \(-1952, 2464\), yaw: -0.25 pi |
| Back right | loc: \(-256.0, -3840\), yaw: 0.5 pi | loc: \(256.0, 3840\), yaw: -0.5 pi |
| Back left | loc: \(256.0, -3840\), yaw: 0.5 pi | loc: \(-256.0, 3840\), yaw: -0.5 pi |
| Far back center | loc: \(0.0, -4608\), yaw: 0.5 pi | loc: \(0.0, 4608\), yaw: -0.5 pi |

**NOTE:** The right and left corner kickoff locations varies from map to map.

* ChampionsField, Farmstead, StarbaseArc, DFHStadium, SaltyShores, and Wasteland: \(±1952, ±2464\).
* Mannfield, BeckwithPark, AquaDome, NeoTokyo, and UtopiaColiseum: \(±2048, ±2560\).
* UrbanCentral: \(±1920, ±2432\).

| Demolished | Blue | Orange |
| :--- | :--- | :--- |
| Right corner | loc: \(-2688, -4608\), yaw: 0.5 pi | loc: \(2688, 4608\), yaw: -0.5 pi |
| Left corner | loc: \(2688, -4608\), yaw: 0.5 pi | loc: \(-2688, 4608\), yaw: -0.5 pi |

### Elevation of Objects at Rest

* Ball: 92.75 \(its radius\)
* Octane: 16.5
* Merc: 17.01

### Physics

* Gravity: 650 uu/s^2
* Max car speed: 2300 uu/s
* Regular speed \(Forward and backwards\), no boost: 1400 uu/s
* Ball coefficient of restitution: 60% \(it loses 40% of the component of its velocity that's toward the surface\)
* Jumping from flat ground
  * This only applies to the first jump, not the double jump
  * Jumping results in acceleration towards the roof of your car, whatever its orientation.
  * On the first physics tick, an instantaneous velocity increase of ~300 uu/s
  * As long as the button is held \(up to 200ms\), continuous acceleration of ~1400 uu/s^2 \(not including gravity\)


# Asset Naming Conventions

* **Case**: use PascalCase by default
* Base Asset Name - `Prefix_BaseAssetName_Variant_Suffix`
* Example: Static Mesh (01) => SM_Rock_01

## Main

| Asset Type           | Prefix | Suffix    | Notes                                  |
|----------------------|--------|-----------|----------------------------------------|
| Level / Scene        | *      |           | IE`Levels/A4_C17_Parking_Garage.unity` |
| Level (Persistent)   |        | _P        |                                        |
| Level (Audio)        |        | _Audio    |                                        |
| Level (Lighting)     |        | _Lighting |                                        |
| Level (Geometry)     |        | _Geo      |                                        |
| Level (Gameplay)     |        | _Gameplay |                                        |
| Probe (Reflection)   | RP_    |           |                                        |
| Probe (Light)        | LP_    |           |                                        |
| Volume               | V_     |           |                                        |
| Trigger Area         |        | _Trigger  |                                        |
| Material             | M_     |           |                                        |
| Static Mesh          | SM_    |           |                                        |
| Skeletal Mesh        | SK_    |           |                                        |
| Texture              | T_     | _?        | See [Textures](#anc-textures)          |
| Visual Effects       | VFX_   |           |                                        |
| Particle System      | PS_    |           |                                        |
| Light                | L_     |           |                                        |
| Camera (Cinemachine) | CM_    |           | Virtual Camera                         |

### 3D Models (FBX Files)

| Asset Type    | Prefix | Suffix | Notes |
|---------------|--------|--------|-------|
| Characters    | CH_    |        |       |
| Vehicles      | VH_    |        |       |
| Weapons       | WP_    |        |       |
| Static Mesh   | SM_    |        |       |
| Skeletal Mesh | SK_    |        |       |
| Skeleton      | SKEL_  |        |       |
| Rig           | RIG_   |        |       |

### Models (3ds Max)

**Case**: this is the only lowercase (to differentiate them from their FBX export).

| Asset Type    | Prefix | Suffix      | Notes                                   |
|---------------|--------|-------------|-----------------------------------------|
| Mesh          |        | _mesh_lod0* | Only use LOD suffix if model uses LOD's |
| Mesh Collider |        | _collider   |                                         |

### Animations

| Asset Type | Prefix | Suffix | Notes |
| -------------------- | ------ | ------ | ----- |
| Animation Clip | A_     | | |
| Animation Controller | AC_    | | |
| Avatar Mask | AM_    | | |
| Morph Target | MT_    | | |

## Artificial Intelligence

| Asset Type        | Prefix       | Suffix  | Notes                          |
|-------------------|--------------|---------|--------------------------------|
| AI / NPC          | AI_          | _NPC    | *Npc could be pawn of CH_ !AI_ |
| Behavior Tree     | BT_          |         |                                |
| Blackboard        | BB_          |         |                                |
| Decorator         | BTDecorator_ |         |                                |
| Service           | BTService_   |         |                                |
| Task              | BTTask_      |         |                                |
| Environment Query | EQS_         |         |                                |
| EnvQueryContext   | EQS_         | Context |                                |

## Prefabs

| Asset Type        | Prefix | Suffix | Notes                         |
|-------------------|--------|--------|-------------------------------|
| Prefab            |        |        |                               |
| Prefab Instance   | I      |        |                               |
| Scriptable Object |        |        | Assigned "SO" label in Editor |

## Materials

| Asset Type            | Prefix | Suffix | Notes |
|-----------------------|--------|--------|-------|
| Material              | M_     |        |       |
| Material Instance     | MI_    |        |       |
| Physical Material     | PM_    |        |       |
| Material Shader Graph | MSG_   |        |       |
| Physical Material     | PM_    |        |       |

## Textures

| Asset Type                      | Prefix | Suffix | Notes                                                   |
|---------------------------------|--------|--------|---------------------------------------------------------|
| Texture                         | T_     |        |                                                         |
| Texture (Base Color)            | T_     | _BC    | Diffuse / Albedo     	                                  |
| Texture (Metallic / Smoothness) | T_     | _MS    |                                                         |
| Texture (Normal)                | T_     | _N     |                                                         |
| Texture (Alpha)                 | T_     | _A     |                                                         |
| Texture (Height)                | T_     | _H     |                                                         |
| Texture (Ambient Occlusion)     | T_     | _AO    |                                                         |
| Texture (Emissive)              | T_     | _E     |                                                         |
| Texture (Mask)                  | T_     | _M     |                                                         |
| Texture (Packed)                | T_     | _*     | See notes below about [packing](#anc-textures-packing). |
| Texture Cube                    | TC_    |        |                                                         |
| Media Texture                   | MT_    |        |                                                         |
| Render Target                   | RT_    |        |                                                         |
| Cube Render Target              | RTC_   |        |                                                         |
| Texture Light Profile           | TLP_   |        |                                                         |

## Rendering

| Asset Type                      | Prefix | Suffix | Notes |
|---------------------------------|--------|--------|-------|
| Universal Render Pipeline Asset | URP_   |        |       |
| HD Render Pipeline Asset        | HDRP_  |        |       |
| Post Process Volume Profile     | PP_    |        |       |
| Particle System                 | PS_    |        |       |

## Audio

| Asset Type     | Prefix | Suffix | Notes                                                           |
|----------------|--------|--------|-----------------------------------------------------------------|
| Audio Clip     | A_     |        |                                                                 |
| Audio Mixer    | MIX_   |        |                                                                 |
| Dialogue Voice | DV_    |        |                                                                 |
| Audio Class    |        |        | No prefix/suffix. Should be put in a folder called AudioClasses |

## User Interface

| Asset Type       | Prefix | Suffix | Notes |
|------------------|--------|--------|-------|
| User Interface   | UI_    |        |       |
| Font             | Font_  |        |       |
| Texture (Sprite) | T_     | _GUI   |       |

### Links

[Unity Style Guide](https://raw.githubusercontent.com/justinwasilenko/Unity-Style-Guide/master/README.md)

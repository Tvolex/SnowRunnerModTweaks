# SnowRunner Mod Structure and XML Guide

## Active mod

`FrameFlex-Steering-Camera` is the working mod. Its `[media]` directory mirrors
SnowRunner's content paths. Preserve these relative paths when adding or
changing files so the game resolves the intended truck or addon definition.

`Original/[media]` is a read-only copy of vanilla files for comparison. Do not
edit it.

## What is inside `[media]`

- `classes/trucks/` contains base-game truck definitions.
- `classes/trucks/addons/` contains shared addon definitions, including the
  big/minicranes and Cat 745C log bunk.
- `_dlc/<dlc-id>/classes/trucks/` contains truck definitions for that DLC.
  DLC-specific addons are often in its `addons/` subfolder; truck-specific
  configurations can be in a `<truck>_tuning/` subfolder.
- `.xml` files are game-readable definitions. `.bak` and `.bak.bak` files are
  backups, not active mod definitions.
- Models, textures, sounds, and other referenced game assets are not bundled
  here; XML references generally point to assets supplied by SnowRunner.

## Main truck XML sections

| Section or parameter | What it controls |
|---|---|
| `Truck` / `TruckData` | Truck identity, type, compatible equipment, wheels, and camera definitions. |
| `Wheels` and `_templates/Wheel` | Wheel positions and reusable wheel settings, including steering angle and steering response. |
| `SteeringRack` and steering constraints | Steering behavior. Existing tie-rod hinge `MinLimit` and `MaxLimit` set its travel range. |
| `Camera` / `Cockpit` | First-person camera position, view limits, zoom offsets, mirrors, and related interior view behavior. |
| `PhysicsModel` / `Body` | Physical bodies, their mass, model frames, collision behavior, and body hierarchy. |
| `Constraint` | The connection between bodies. `Type`, `AxisLocal`, `MinLimit`, and `MaxLimit` define its kind, orientation, and permitted movement. |
| `Motor` `Damping` / `Spring` | Response of a spring-type joint. Together they affect how readily the connected frame twists and how strongly it resists or settles that movement. |
| `GameData` | Garage/shop information, unlocks, addon compatibility, sockets, and other gameplay metadata. |
| `Socket` / `InstallSocket` | Where equipment can be mounted and which addon type can attach there. |

Frame flex is controlled by the truck's existing cabin-to-frame hinge or
cabin-twist joint. Its `MinLimit` and `MaxLimit` bound the twist; its
`Damping` and `Spring` affect the joint's motion and resistance. The effect
depends on the particular truck and the interaction of these settings. Only
the relevant existing joint should be tuned; do not create a new joint or
change unrelated suspension, cabin, or accessory constraints.

## Main addon XML sections

| Section or parameter | What it controls |
|---|---|
| `TruckAddon` | Declares the equipment addon. |
| `PhysicsModel`, `Body`, and `Mass` | Physical bodies and the addon mass contributing to the equipped vehicle. Nested crane sections and anchors can each have their own mass. |
| `PoweredConstraints` | Player-triggered groups and chains for deploying, folding, or operating equipment. |
| `ControlledIK` | Movement of articulated equipment. `CoeffEndMovementSpeedOY` controls vertical movement; `CoeffEndMovementSpeedXZ` controls horizontal movement. The `WithLoad` variants apply when carrying a load. |
| `ControlledConstraints` / `SpeedMult` | Speed multiplier for a named powered constraint, such as the log-lift grapple rotation. |
| `Motor` `Force` / `Tau` | Actuator strength and response for powered joints; these are distinct from body mass and movement coefficients. |
| `LoadArea` | Cargo type, capacity region, and placement bounds for cargo carried by an addon. |
| `CraneSourceSocket`, `CraneSocket`, and `InstallSocket` | Crane attachment point or the location/type used to mount an addon. |
| `GameData` / `AddonType` | Shop display, unlocks, sounds, and equipment category. |

For a log-lift claw, identify the `GrapplerBase` constraint in
`ControlledConstraints` to adjust claw rotation speed. The separate
`LeftGrappler` and `RightGrappler` constraints control opening and closing; do
not change them when the request is rotation-only.

## Editing boundaries

- For mod changes, edit only the specifically requested files in
  `FrameFlex-Steering-Camera`; keep all paths and unrelated settings intact.
- Read matching vanilla XML under `Original/[media]` when a vanilla comparison
  is needed, but never modify it.
- Preserve formatting with targeted edits. Avoid replacing complete truck or
  addon files when only selected attributes need to change.
- Check that XML remains well-formed and that only requested parameters changed.

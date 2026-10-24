# SnowRunner Mod Working Guide

## Goal

Tune SnowRunner truck frames to flex naturally, retain truck-specific handling, and configure steering and cameras without disturbing unrelated mod settings.

## Folders and edit boundaries

Inspect the repository before each task because folders may move. When present:

- `FrameFlex` is the active mod and the only folder to edit for frame, steering, or camera changes.
- `FrameFlexOldMod` is a read-only reference for frame-joint limits and original stiffness.
- `CameraMod` is a read-only source for camera configuration.

Never replace a whole active truck XML with a file from a reference mod. Preserve all unrelated settings, editing only the requested attributes or complete camera element.

## Frame-flex configuration

The target is an existing chassis-to-cabin or cabin-twist `Hinge` constraint in the truck's physics model. Some trucks use a `Twist` template. Do not alter unrelated cabin dampers, props, mirrors, or accessory joints, and do not add a hinge where none exists.

For a truck with a matching `FrameFlexOldMod` file:

- Copy `MinLimit` and `MaxLimit` exactly from the corresponding old-mod cabin/twist hinge.
- Set motor values between the current active value and old-mod value using geometric interpolation:
  - `Damping = round(current_Damping^0.50 * old_Damping^0.50)`
  - `Spring = round(current_Spring^0.35 * old_Spring^0.65)`
- The spring is blended farther toward the old value to resist quick flex on unloaded bumps; damping moves halfway toward the old value to temper motion under heavy cargo.
- Do not apply wheelbase multipliers or substitute a global coefficient. Calculate each truck from its own matching joint values.
- Preserve the old mod's limit strings and round motor values to the nearest integer.

If values are zero, negative, missing, or the joint cannot be matched unambiguously, do not guess; leave it unchanged and report it. Never edit `FrameFlexOldMod`.

## Steering configuration

Classify trucks from `TruckType` and, for ambiguous `HEAVY_DUTY` trucks, wheelbase and default tire:

- `SCOUT` -> Scout.
- `HIGHWAY` -> road/highway.
- `HEAVY_DUTY` -> road/highway only when the XML wheelbase span is at most 6.3 game units and the default tire name contains `highway` or `road`; otherwise heavy.
- `OFFROAD`, `HEAVY`, and remaining `HEAVY_DUTY` -> heavy/offroad.

Apply these settings to the front steering definitions in `_templates/Wheel` and to existing local tie-rod/steering constraints:

| Category | Front steering angle target | Tie-rod `MinLimit` / `MaxLimit` | `SteerSpeed` | `BackSteerSpeed` |
|---|---:|---:|---:|---:|
| Road/highway | 48 | -22 / 22 | 0.045 | 0.030 |
| Heavy/offroad | 38 | -16 / 16 | 0.035 | 0.020 |
| Scout | 44 | -18 / 18 | Keep current value if already above 0.035 | Keep current value if already above 0.020 |

For angles, compare against the truck's original steering definition: if its absolute angle exceeds the category target, add 4 degrees to its absolute value and preserve its sign; otherwise use the category target. Apply tie-rod limits only to existing steering tie rods; do not create missing constraints. Leave scout steering speeds unchanged when already above the stated minimums.

## Camera configuration

For matching truck files, copy the complete `<Camera>...</Camera>` element from `CameraMod` into the corresponding `FrameFlex` file. Match files by relative path and require exactly one camera element in both files. Replace only that element, including nested camera positions and settings; preserve all text outside it. Do not edit `CameraMod`.

If a counterpart is missing, the camera count is unexpected, or matching is ambiguous, leave the destination unchanged and report the reason rather than guessing.

## Safe editing and validation

- Read the affected source and destination XML before editing.
- Use targeted text-span edits rather than XML serialization that reformats files.
- Keep edits within `FrameFlex` and within the exact requested XML blocks/attributes.
- Parse all edited XML files after changes.
- Confirm values against their requested source/configuration and verify that unrelated text and files remain unchanged.
- Report skipped or ambiguous files explicitly.

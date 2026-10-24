# SnowRunner Handling Tweaks

Truck-specific frame, steering, and camera tuning, plus lighter and slower
truck-mounted cranes and a lighter Cat 745C log bunk.

## Frame flex

Existing cabin/frame joints are tuned on 59 of 63 trucks to make a proper
leaning. Four trucks without a suitable adjustable joint are unchanged.

**Changed:** frame-joint `Damping`, `Spring`, and hinge limits where an
adjustable joint exists. Unrelated joints are left alone.

## Steering

Steering angles and response are tuned by truck category:

| Category | Target angle | Tie-rod limits | Minimum steer / return speed |
|---|---:|---:|---:|
| Road/highway | 48° | -22 to 22 | 0.045 / 0.030 |
| Heavy/offroad | 38° | -16 to 16 | 0.035 / 0.020 |
| Scout | 44° | -18 to 18 | 0.035 / 0.020 |

**Changed:** front steering angles, steering and return speeds, and existing
tie-rod limits. If an original angle is already above its target, it is
increased by 4° while preserving its sign. Scout speeds already above their
minimum are retained; missing tie-rod constraints are not added.

## First-person camera

**Changed:** truck-specific cockpit camera position, look limits, zoom offsets,
and leaning/rear-view behavior. The wider first-person look/lean range lets the
view move farther outside the cabin as the truck leans.

## Cranes and log bunk

**Changed:**

- Big- and minicrane body/support `Mass` values are halved.
- Cat 745C log-bunk body mass is reduced from `1,000` to `500`.
- Crane horizontal movement coefficients are halved, including the
  with-load coefficients.
- Log-lift grapple rotation speed is reduced by 50% (`SpeedMult` `.03` to
  `.015`; Mack Pinnacle `.01` to `.005`) across all nine included variants.
- Grapple open/close speed, crane motor forces, travel limits, vertical
  movement, and cargo definitions are unchanged.

Keep the `[media]` folder structure when installing.

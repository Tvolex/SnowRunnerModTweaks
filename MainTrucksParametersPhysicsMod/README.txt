SNOWRUNNER HANDLING TWEAKS

Truck-specific frame, steering, and camera tuning, plus lighter and slower
truck-mounted cranes and a lighter Cat 745C log bunk.

INSTALLATION

This pack is divided into five numbered parts. Apply them in sequence so each
set of changes is added to the game's archive.

1. Open the downloaded mod archive in WinRAR; leave it compressed.

2. Locate SnowRunner's client folder. Depending on your installation, it is:
   SnowRunner\en_us\preload\paks\client
   or
   SnowRunner\preload\paks\client

3. Before editing, copy initial.pak and shared.pak out of the client folder to
   a separate, safe location. Keep those backups outside the client folder.
   Renamed .pak files left alongside the originals can cause text-display
   problems.

4. Open client\initial.pak in WinRAR. In the mod archive, navigate to
   TvolexSnowRunnerPack.

5. For each folder listed below, open it and add its [media] folder to
   initial.pak. Complete each transfer before moving on, and use this order:
   1.Engines
   2.Gearboxes
   3.Suspension
   4.NewFriction
   5.MainTrucksParametersPhysicsMod

6. Keep the original backup files safe. To undo the installation, restore those
   backups to the client folder.

FRAME FLEX

Existing cabin/frame joints are tuned on 59 of 63 trucks to make a proper
leaning. Four trucks without a suitable adjustable joint are unchanged.

Changed: frame-joint Damping, Spring, and hinge limits where an adjustable
joint exists. Unrelated joints are left alone.

STEERING

Steering angles and response are tuned by truck category:

Category       Target angle   Tie-rod limits   Minimum steer / return speed
Road/highway   48 degrees     -22 to 22        0.045 / 0.030
Heavy/offroad  38 degrees     -16 to 16        0.035 / 0.020
Scout          44 degrees     -18 to 18        0.035 / 0.020

Changed: front steering angles, steering and return speeds, and existing
tie-rod limits. If an original angle is already above its target, it is
increased by 4 degrees while preserving its sign. Scout speeds already above
their minimum are retained; missing tie-rod constraints are not added.

Changed: SteeringCastor is kept between 10 and 15 degrees for every steering
axle in the original set of tuned truck definitions; trucks without an
explicit castor value use 10 degrees. The additional engine-response
definitions retain their Original steering setup.

ENGINE RESPONSE

Changed: heavy-duty, heavy, and off-road trucks use more deliberate startup
and engine response settings. The category values are minimum EngineStartDelay
/ ExhaustStartTime and maximum Responsiveness:

Category       Start delay   Exhaust timing   Responsiveness
Heavy duty     1.2           1.1              0.22
Heavy          1.8           1.5              0.15
Off-road       1.4           1.2              0.18


FIRST-PERSON CAMERA

Changed: truck-specific cockpit camera position, look limits, zoom offsets,
and leaning/rear-view behavior. The wider first-person look/lean range lets the
view move farther outside the cabin as the truck leans.

CRANES AND LOG BUNK

Changed:
- Big- and minicrane body/support Mass values are halved.
- Cat 745C log-bunk body mass is reduced from 1,000 to 500.
- Crane horizontal movement coefficients are halved, including the with-load
  coefficients.
- Log-lift grapple rotation speed is reduced by 50% (SpeedMult 0.03 to 0.015;
  Mack Pinnacle 0.01 to 0.005) across all nine included variants.
- Grapple open/close speed, crane motor forces, travel limits, vertical
  movement, and cargo definitions are unchanged.

U357 WHEEL COMPATIBILITY

The originally tuned truck definitions include compatibility entries for the
wheel classes in the separate mod-u357 pack. Install that pack as well to use
those wheel options.
Its off-road and mud tires are tuned to Soft with Body/Asphalt/Substance
friction values of 1.25 / 0.35 / 2.5; the highway tires remain stiff and keep
their original friction values. The friction and softness values are also
listed in the affected tire descriptions.

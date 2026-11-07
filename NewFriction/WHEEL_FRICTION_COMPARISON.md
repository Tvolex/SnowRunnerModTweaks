# Wheel friction and softness comparison

The friction values below are the shared wheel-type defaults from the
`trucks.xml` templates. Values are listed as **Body / Asphalt / Substance**.
Individual tire classes can override these defaults.

| Wheel type | Vanilla friction | NewFriction friction | Vanilla softness profiles | NewFriction softness profiles |
|---|---:|---:|---|---|
| Scout off-road | 2.0 / 1 / 1.2 | 1.25 / 0.5 / 1.2 | Varies by tire class | Varies by tire class |
| Scout mud tires | 3.0 / 0.5 / 1.6 | 1.25 / 0.35 / 1.85 | Varies by tire class | Varies by tire class |
| Scout highway | 0.8 / 2 / 0.2 | 0.85 / 3 / 0.5 | Varies by tire class | Varies by tire class |
| Scout chains | 2.0 / 0.9 / 1.1 | 0.45 / 0.2 / 2.6 | Varies by tire class | Varies by tire class |
| Scout studs | Not defined in vanilla defaults | 1.5 / 2 / 0.5 | Not defined in vanilla defaults | Varies by tire class |
| Scout all-terrain | 1 / 1.0 / 1.0 | 1.4 / 3 / 1 | Varies by tire class | Varies by tire class |
| Off-road | 3.0 / 0.8 / 1.5 | 1.25 / 0.5 / 1.3 | Varies by tire class | Varies by tire class |
| Mud tires | 2.0 / 0.5 / 2.0 | 1.25 / 0.35 / 1.85 | Varies by tire class | Varies by tire class |
| Highway | 1.0 / 3.0 / 0.2 | 0.55 / 5 / 0.3 | Varies by tire class | Varies by tire class |
| Heavy mud tires | 1.7 / 0.5 / 3.0 | 1.25 / 0.35 / 2.1 | Varies by tire class | Varies by tire class |
| Chains | 3.0 / 1.2 / 1.3 | 0.45 / 0.2 / 2.4 | Varies by tire class | Varies by tire class |
| All-terrain | 1.5 / 1.5 / 1.0 | 0.7 / 3 / 1 | Varies by tire class | Varies by tire class |

Softness is selected by individual tire classes, so it does not have one
universal value per friction type. The following shared softness presets show
the vanilla and NewFriction template parameters (**RadiusOffset /
SoftForceScale**):

| Softness preset | Vanilla | NewFriction |
|---|---:|---:|
| Stiff | 0.02 / 0.32 | 0.0291 / 0.175 |
| Soft | 0.03 / 0.12 | 0.0319 / 0.130 |
| ScoutStiff | 0.02 / 0.32 | 0.0306 / 0.150 |
| ScoutSoft | 0.1 / 0.2 | 0.0325 / 0.120 |
| ScoutDefault | 0.025 / 0.24 | 0.0313 / 0.140 |
| Average | 0.025 / 0.24 | 0.0300 / 0.160 |

Tire-class definitions may select or override these shared presets, so check
the individual wheel class when comparing a specific tire. Chain friction
values above omit the separate ice-friction parameter.


# Formal Analysis and Refinement (FAR)

In steps:

1. Identify the errors
2. Handle the errors with proof

## Types of errors

| Type       | Nature    | Typical Trigger            | Typical Example                             |
| ---------- | --------- | -------------------------- | ------------------------------------------- |
| Corrective | Reactive  | A failure is detected      | Fixing a program that produces wrong output |
| Adaptive   | Proactive | The environment changes    | Porting the system to new hardware          |
| Perfective | Proactive | An improvement opportunity | Restructuring code for readibility          |
| Preventive | Proactive | An anticipated future risk | A software-rejuvenation restart cycle       |
## Model Checker example ("SPIN")

Although preferable, this example cannot be used on big architectures. Its better to divide & conquer, in order to focus on one thing only, and then using Model checking here.
# Heavy Dark Mesons
[https://arxiv.org/abs/1809.10184](https://arxiv.org/abs/1809.10184)

 - Graham D. Kribs
 - Adam Martin
 - Bryan Ostdiek
 - Tom Tong

This website contains the UFO files for the phenomenological models used in the above paper to study collider constraints on Heavy Dark Mesons.

The model files are contained within the directory "UFO_FILES"


# Instructions
The value of the couplings depends on the value of the dark meson masses, as well as the number of dark colors. In order for everything to remain consistent, it is important that the couplings are explicitly computed after making any changes. This can be done within MadGraph using the
`update dependent`.

For example, to include both the Drell-Yan and resonant production of the charged pions, do:
```
import model Gaugephobic_SU2L
generate p p > dp+ dp- QED<=4 NP<=4 
output ExampleDarkMeson
```
After launching and selecting the options for showering and detector simulation, the user can use:
```
set PionMass 400
set FermionEta 0.45
set NDark 4
update dependent
compute_widths rho0 rho+ --body_decay=2
compute_widths dp0 dp+ --body_decay=3
```

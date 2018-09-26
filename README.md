# Heavy Dark Mesons
[https://arxiv.org/abs/18XX.XXXXX](https://arxiv.org/abs/18XX.XXXXX)

 - Graham D. Kribs
 - Adam Martin
 - Bryan Ostdiek
 - Tom Tong

Please note that at this point, the website is still under construction. The model files supplied here are correct, but the parameterization is not quite the same as in the paper. We will update very soon. Thank you for your patience.


This website contains the UFO files for the phenomenological models used in the above paper to study collider constraints on Heavy Dark Mesons.

# Parameters
There are a few different parameters that are common or different between the models. For a phenomenological study, the user should only need to alter the following:
  - mpi (PionMass): mass of the dark pion.
  - ƞ (FermionEta): mass ratio of dark pions to dark rho. We use benchmark values of 0.25, 0.45, and 0.55.
 - $N_D$ (NDark): the number of dark colors. The benchmark value is 4.

 For now, the differences between the models should be viewed as hard coded, and should not be changed.

# Particles
Each of the models contains a triplet pion (charged and neutral). Only the models with mixing with the SU(2) gauge bosons have a charged rho coded in. The SU(2)R model only has a neutral rho in the UFO files.
## SU(2)L models
 - Charged rho (rho+): 9000006
 - Neutral rho (rho0): 9000005
 - Charged pion (dp+): 9000007
 - Neutral pion (dp0): 9000008

## SU(2)R models
 - Charged rho (rho+): 9000006
 - Neutral rho (rho0): 9000005
 - Charged pion (dp+): 9000007
 - Neutral pion (dp0): 9000008



# Instructions
The value of the couplings depends on the value of the dark meson masses, as well as the number of dark colors. In order for everything to remain consistent, it is important that the couplings are explicitly computed after making any changes. This can be done within MadGraph using the
`update dependent`.

For example, to include both the Drell-Yan and resonant production of the charged pions, do:
```
import model Gaugephobic_SU2L
generate p p > dp+ dp- QED<=2 NP<=2
output ExampleDarkMeson
```
After launching and selecting the options for showering and detector simulation, the user can use:
```
set PionMass 400
set FermionEta 0.45
set NDark 4
update dependent
compute_widths 9000007 9000008 --body_decay=2
compute_widths 9000006 9000005 --body_decay=3
```

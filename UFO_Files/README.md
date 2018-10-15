# Heavy Dark Mesons
[https://arxiv.org/abs/1809.10184](https://arxiv.org/abs/1809.10184)

 - Graham D. Kribs
 - Adam Martin
 - Bryan Ostdiek
 - Tom Tong

This website contains the UFO files for the phenomenological models used in the above paper to study collider constraints on Heavy Dark Mesons.

# Parameters
There are two sets of UFO models. The first is called "FromPaper", and it contains the parameterizations from the paper. Namely these are:
 - mpi (PionMass): mass of the dark pion.
 - ƞ (FermionEta): mass ratio of dark pions to dark rho. We use benchmark values of 0.25, 0.45, and 0.55.
 - $N_D$ (NDark): the number of dark colors. The benchmark value is 4.
 - VPi: controls the coupling between the dark pions and the standard model particles.
 - Ƹ (Xi): suppression of the gauge-higgs couplings of the dark pions. This is set to 1.0 in the gaugephilic modes and cannot be changed. The gaugephobic modes have this as a free parameter that must be set by the user.

The other set of UFO models are specific to certain implementations of heavy dark mesons. The gaugephobic ones are designed after "Stealth Dark Matter" [https://arxiv.org/abs/1503.04203]. Please contact us with any questions. Lastly, as an example of a gaugephilic model, we include a model where the dark pions are related to electroweak symmetry breaking, similar to "Induced Electroweak Symmetry Breaking" [https://arxiv.org/abs/1411.6023]. Our parameterizations are slightly different than those papers.

# Particles
Each of the models contains a triplet pion (charged and neutral). Only the models with mixing with the SU(2) gauge bosons have a charged rho coded in. The SU(2)R model only has a neutral rho in the UFO files.
## SU(2)L models
 - Charged rho (rho+): 9000006
 - Neutral rho (rho0): 9000005
 - Charged pion (dp+): 9000007
 - Neutral pion (dp0): 9000008

## SU(2)R models
<!-- - Charged rho (rho+): 9000006 -->
 - Neutral rho (rho0): 9000005
 - Charged pion (dp+): 9000006
 - Neutral pion (dp0): 9000007



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

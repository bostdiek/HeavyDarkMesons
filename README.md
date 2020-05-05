# Heavy Dark Mesons
“Dark Mesons at the LHC,” [JHEP, 1907, 133 (2019) doi:10.1007/JHEP07(2019)133](https://link.springer.com/article/10.1007/JHEP07(2019)133) [[arXiv:1809.10184 [hep-ph]]](https://arxiv.org/abs/1809.10184).


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

# Citations
Please cite as
```
@article{Kribs:2018ilo,
    author = "Kribs, Graham D. and Martin, Adam and Ostdiek, Bryan and Tong, Tom",
    title = "{Dark Mesons at the LHC}",
    eprint = "1809.10184",
    archivePrefix = "arXiv",
    primaryClass = "hep-ph",
    doi = "10.1007/JHEP07(2019)133",
    journal = "JHEP",
    volume = "07",
    pages = "133",
    year = "2019"
}
```

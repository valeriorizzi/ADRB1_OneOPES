# OneOPES on ADRB1 (Beta-1 adrenergic receptor)

This repository contains the input files and computational setup used for the simulations described in:

> [Enhanced Sampling and Tailored Collective Variables Yield Reproducible Free Energy Landscapes of Beta‑1 Adrenergic Receptor Activation](https://doi.org/10.1021/acs.jctc.5c00600)

## Repository content

The repository contains the necessary files to reproduce the OneOPES simulations we carried out on both apo ADRB1 and adrenaline-bound ADRB1 (holo-ADRB1) complexes.

The main directories include:

- `apoADRB1`: input files for apo/ADRB1 (with unprotonated D2.50)
- `apoADRB1_ASPH`: input files for apo/ADRB1 (with protonated D2.50)
- `apoADRB1_NA`: input files for apo/ADRB1 (in which we sample both GPCR activation and NA-D2.50 binding process)
- `holoADRB1`: input files for adrenaline-bound/ADRB1

Each directory contains the necessary input files to run the simulations, including:

- system topology files
- GROMACS binary run input files (`.tpr`)
- PLUMED input files (`plumed.dat`)
- reference structures (`.pdb`)
- additional files required for the simulations

## Running the simulations

The simulations are organized as 8 parallel replicas (i.e., 0 to 7) and can be run using a command similar to:

```
mpirun -n 8 gmx_mpi mdrun -s prd.tpr -deffnm prd -notunepme -pin on -multidir ./0 ./1 ./2 ./3 ./4 ./5 ./6 ./7 -hrex -replex 5000 -plumed plumed.dat
```

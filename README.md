# Why3 and Proving A* Automatically
This repository is code developed as part of a Bachelor's research project: "Why3 and Proving A* Automatically - A Case Study of Why3 as a Tool for Automated Software Verification". The project aimed to implement and verify the A* algorithm using Why3. An electronic version of this thesis is available at https://repository.tudelft.nl/.

A more user-friendly format of the proof can be seen in [astar.html](Redefinition/astar.html) file (generated using Why3's [doc](https://www.why3.org/doc/manpages.html#the-doc-command) command). 

## Prerequisites
To run the code, you will need the following versions of software:

- Why3 1.8.0
- Alt-Ergo 2.6.2
- CVC5 1.2.1
- Eprover 2.0
- Z3 4.15.0

Installing Why3, its IDE, and Alt-Ergo can be done using Opam with the command:
```
opam install why3 why3-ide alt-ergo
```

## Reproducing Reuslts
The implementation can be viewed in Why3's IDE by running the following command in the [Redefinition](Redefinition) folder:
```
why3 ide astar.mlw
```
This also shows the proof stored in that subfolder: [why3session.xml](Redefinition/astar/why3session.xml)`. The proof can be replayed using the command:
```
why3 replay astar
```
In the paper, "Why3 and Proving A* Automatically - A Case Study of Why3 as a Tool for Automated Software Verification," available at https://repository.tudelft.nl/, we detail how to generate some statistics on our proof in the "Reproducibility" subsection 6.1. 

To get the number of uses per type of logical transformation, run the following command from the [Redefinition](Redefinition) folder:
```
why3 session info --session-stats ./ astar |
grep -oE ’transformation ␣+[a-zA -Z_]+’ |
grep -oE ’[a-zA -Z_]+$’ |
sort |
uniq -c |
sort -nr
```

To get statistics on each prover, run the following command from the [Redefinition](Redefinition) folder:
```
why3 session info --provers-stats ./ astar
```

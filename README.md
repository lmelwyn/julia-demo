
## Simple 1D QM julia example

### Introduction

The file qmbs1d.jl contains a short program to numerically calculate the bound state energies 
of a quantum particle experiencing the potential V(x) in an infinite well. The potential 
function V(x) need not to be known analytically, but for some potentials exact solutions are 
known, e.g. for the harmonic potential centered in the well. In this case there is a close to 
perfect agreement between the results of the analytical and numerical results validating the 
code and its execution. 

In the code we used anonymous functions to define the basis set, unicode character in function
definitions, and the simple metafunction interface to parallel and distributed tasks for 
workload distribution on many-core and multi-node setups. 


### Howto run 

Install julia on your local laptop, or install docker and pull the julia container 
docker.io/julia/julia:0.4.1, or just login and use http://juliabox.org. Then just 
run  

```
julia -p<number of cores> qmbs1d.jl 
```
## 

The julia language already contains the needed linear algebra diagonalization routines and the problem therefore 
reduces to the construction of the Hamiltonian matrix, H, with elements Hij = < i |H0 + V| j >,  which are 
calculated by distributing the compute tasks on the available cores. 

For a real and symmetric Hamiltonian only (n^2+n)/2 components need to be calculated and then mirror the remaining elements across the matrix diagonal. 

For more details, e.g. see [Am. J. Phys. 77, 253 (2009)](http://scitation.aip.org/content/aapt/journal/ajp/77/3/10.1119/1.3042207), (http://arxiv.org/pdf/0806.3051) 


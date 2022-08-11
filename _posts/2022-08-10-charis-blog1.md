---
layout: page 
title: When Lennard-Jones Meets Monte Carlo  
author: Charis Liao
---

# A Road Map to Measuring 
There are different levels of measurement in Science. From macro level to micro level and even molecular level. In general physics classes, students usually measure different forces by throwing a ball and measuring the distance. However, it will be extremely difficult to use the same kind of measuring method in the molecular level. Therefore, we have to rely on molecular stimulations to calculate the statistical mechanics of the systems. 

# Monte Carlo & Lennard-Jones Potential 

Lennard-Jones Potential is a fantastic example of needing molecular stimulations to calculate the potential energy between two particles. One of the methods that has been widly used in computational science is the Monte Carlo method. It could be used to evaluate integrals (or evaluate an area under the curve). To apply the Monte Carlo method on a statistical mechanics model: 

⟨Q⟩ = $\int_v$ Q($r^N$) $\rho$($r^N$)$dr^N$  

Q = the thermodynamic quantity of interest (system potential energy)
$\rho$($r^N$) = probability density  
V = volume of configuration space

Since the thermodynamic system (LJ Potential) of interest actually involves high dimensional integrals and are dominated by a relatively small region of configurational space, having **importantce sampling** and an **acceptance criteria** (Metropolis Criterion) could help generating sample coordinates from the desired equibilbrium probability density and a standard for accepting generated positions.  

# Translating Words to Code - Tips and tricks to decrease the runtime of a Monte Carlo Stimulation  

It is not surprised to implement multiple "for loops" to compare every single particle pair; however, having nested for loops will increase the runtime of our stimulation. At this point, we should ask ourselves, how can we avoid useless calculations and improve runtime? 

A simple answer to the above question would be to only compare the particle of interest with other pariticles in the system instead of comparing all possible particle pairs. This would lower the number of computation from n choose 2 permutations to n-1 times. 

# RDF - The Radial Distribution Function 

Theoretically, the distribution for pariticles should be uniform; however, by applying the radial distribution there will be a "r" and "dr" that would affect the probability of finding a particle. By counting the number of particles that fall within the dr range, and divide it with the volume and density, we would be able to derive g(r) (probability of finding a particle at a distance r from another tagged particle). The probability fluctuate, but as dr gets larger, more particles will fall within the accepted range, which is the reason why eventually, the function will converge to one. 

If we plot the function, we would see different graphs for solid, liquid, and gas. This is becuase Solids have regular, periodic structures, with molecules fluctuating near their lattice positions, but gases do not, and liquids do not maintain a constant structure and lose all of their long-range structure. Radial distribution function converge to one for liquids and gases because with a large r, molecules become independent and the density become really bulky. In a molecular simulation, you will typically calculate the RDF for each individual frame, then average them. This might be due to the likelihood of certain configurations are more likely, but we can't ignore the other configurations as well. 










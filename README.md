## Tutorials on Symbolic-Numeric Programming using Julia for ChEs, BioChEs, and EnvEs (CBEEs)

### What is symbolic-numeric programming?

As described in more detail in Ref. 1 given below, all mechanistic engineering models start as a set of symbolic equations, possibly produced by pencil and paper or, in more recent times, by symbolic software such as Mathematica or Maple. Then, in a subsequent step, this symbolic representation is transformed (often manually) into numerical code and finally compiled into performant machine code. However, there is much to be gained by combining these steps so that the symbolic and numeric representations of a model co-exist in a single environment. When this is done, these two representations can inform each other and co-evolve synergistically when needed. This strategy, termed symbolic-numeric programming, yields new approaches for creating and using models and more efficient final compiled code. 

### The Julia approach, and why it is preferred

This repository introduces the tutorial user to symbolic-numeric programming using the free and open-source [Julia](https://julialang.org/) programming language. Julia is a relatively new programming language (version 1.0 was released in 2018) that was created at MIT and that provides an unequaled combination of programming ease and computational speed. Taking the Python language for comparison, in the Python ecosystem user-created script is written in pure Python, libraries are generally written in a language that that is more performant (such as Fortan, C, C++, or Rust), and the Python interpreter is written in C. This approach has two basic shortcomings: (1) the Python interpreter is slow, which reduces the speed of the entire system and (2) additional inefficiencies occur when information passes between software components written in different computer languages. In constrast, in Julia all components of the ecosystem are written in a single language, which is native Julia, and Just-in-time (JIT) compiling to machine code is used instead of an interpreter. In addition, JIT compiling is made very efficient using multiple dispatch, which is a paradigm not present in Python. This structure leads to high levels of library composability and compatibility, high compiler efficiency, and high computational speed. This structure also makes Julia especially suitable for symbolic-numeric programming where several different libraries need to function together harmoniously and efficiently, and this also makes Julia ideal for teaching and learning since someone only needs to know the Julia language in order to examine a software system at all levels from top to bottom. A final benefit is that all Julia users are potential contributors to the Julia software development community since someone only needs to know Julia to fully participate in all aspects of developing a software project. 

### The central role of the ModelingToolkit.jl library

The tutorials shown here also emphasize using the Julia software package [ModelingToolkit.jl](https://docs.sciml.ai/ModelingToolkit/stable/) (MTK) in order to combine symbolic and numeric approaches for solving problems (see Refs. 2 and 3). MTK provides an efficient user interface that seemlessly coordinates relevant packages such as [Symbolics.jl](https://docs.sciml.ai/Symbolics/stable/), which is a fast computer algebra system, and [DifferentialEquations.jl](https://docs.sciml.ai/DiffEqDocs/stable/), which is a state-of-the-art package for numerical solutions of differential equations. As mentioned above, combining symbolic and numeric approaches enables more effective solution methods and more efficient compiled numerical code. For example, as will be demonstrated later, this approach makes it simple to efficiently generate a symbolic Jacobian when solving nonlinear algebraic equations even when the system is very large. In many cases this yields the fastest numerical code for this type of problem. Furthermore, due to MTK's many automated features, this modeling approach can be accomplished by someone with modest mathematical and numerical modeling skills. Finally MTK can be used for either causal or acausal modeling, in contrast to [Modelica](https://modelica.org/), which is strictly acausual, and [Simulink](https://www.mathworks.com/products/simulink.html), which is strictly causal.   

### Additional considerations

The tutorials shown here are especially tailored for chemical, biochemical and environmental engineers (CBEEs), and are also geared toward persons who already know the Matlab programming language since the syntaxes for Julia and Matlab have many similarities, even they ultimately function very differently. 

In the typical university curricula for undergraduate and graduate students, computational problems are formulated so that they are "toy" in nature and essentially any computational platform will suffice for their solution. In contrast, this tutorial is aimed at realistic, real-world, and large-scale applications where computational efficiency is important. This tutorial is especially aimed at the common situation where someone is using a typical laptop or desktop personal computer and needs to achieve the performance of a high-end workstation.       

Several on-line tutorials already exist that cover symbolic-numeric computing using MTK. Examples include the tutorial on Julia's Scientific Machine Learning website located [here](https://docs.sciml.ai/ModelingToolkit/stable/tutorials/acausal_components/), and the tutorial associated with the MIT course titled [Composable System Modeling and its Compilation](https://docs.sciml.ai/ModelingToolkitCourse/dev/). However, none of these previous tutorials have the focus of this tutorial, and many are somewhat short on using effective pedagogical methods to make learning easy (or at least easier!) for the neophyte. The tutorials here seek to address these needs. So, fasten your seatbelts, hold on to your hats, and join us for an exciting ride in the Julia language ecosystem.

### Julia package built upon ModelingToolkit.jl (MTK)

There are many Julia software packages that are built directly upon MTK, or which closely interoperate with MTK, to take advantage its features including symbolic-numeric programming. Selected examples are shown below. 

#### Examples of packages incorporating MTK that are relevant to CBEEs (in alphabetical order)

| Software | Purpose| License Type|
|  ---  |  ---  |  ---  |
|[Aerosol.jl](https://aerosol.earthsci.dev/stable/)| Modeling of atmospheric aerosols| Free and open source|
|[Catalyst.jl](https://docs.sciml.ai/Catalyst/stable/)| Modeling of chemical and biochemical reaction networks (see Ref. 4)| Free and open source|
|[CellMLToolkit.jl](https://docs.sciml.ai/CellMLToolkit/stable/)| Convert a CellML model of a biological cell (in XML format) into a ModelingToolkit.jl representation| Free and open source|
|[DataDrivenDiffEq.jl](https://docs.sciml.ai/DataDrivenDiffEq/stable/)| Automatically find the system of governing symbolic equations that corresponds to a dataset| Free and open source|
|[Dyad](https://www.hpcwire.com/off-the-wire/juliahub-launches-dyad-for-ai-driven-engineering-and-system-modeling/)| A declarative, physical modeling language that compiles into a ModelingToolkit.jl representation and permits AI-assisted industrial modeling| Free for non-commercial use, a monthly fee otherwise|
|[EnvironmentalTransport.jl](https://transport.earthsci.dev/dev/)| Modeling environmental mass transfer processes| Free and open source|  
|[MethodOfLines.jl](https://docs.sciml.ai/MethodOfLines/stable/)| Solving PDEs using the Method of Lines| Free and open source |
|[ModelingToolkitNeuralNets.jl](https://docs.sciml.ai/ModelingToolkitNeuralNets/stable/)| Embed a neural network inside a ModelingToolkit equation system| Free and open source|
|[MomentClosure.jl](https://sciml.github.io/MomentClosure.jl/dev/)| Solve differential equations in term of the moments of the time functions (e.g., mean, variance, etc.) as opposed to the time functions themselves (see Ref. 5)| Free and open source|
|[NeuralPDE.jl](https://docs.sciml.ai/NeuralPDE/stable/)| Solving PDEs using Physics Informed Neural Networks (PINNs)| Free and open source|
|[NumCME.jl](https://voduchuy.github.io/NumCME.jl/dev/)| Chemical Master Equation approach for simulating biochemical reaction networks| Free and open source|
|[ProcessSimulator.jl](https://github.com/SciML/ProcessSimulator.jl/blob/sigle-phase-approach/README.md)| Simulation of chemical processes (such as a vapor-liquid equilibrium flash etc.) (see Ref. 6)| Free and open source|
|[StructuralIdentifiability.jl](https://docs.sciml.ai/StructuralIdentifiability/stable/)| Determine whether parameters in an ODE model can be identified using data| Free and open source|
|[Thetis.jl](https://datinfo.gitlab.io/Thetis.jl/stable/)| Modeling of wastewater treatment processes such as activated sludge processes| Free and open source|

#### Examples of packages incorporating MTK in other areas (in alphabetical order)

| Software | Purpose| License Type|
|  ---  |  ---  |  ---  |
|[CirculatorySystemModels.jl](https://ts-cubed.github.io/CirculatorySystemModels.jl/stable/)| Modeling of circulatory blood flow| Free and open source|
|[Neuroblox](https://www.neuroblox.ai/)| Computational neuroscience and psychiatry (see Ref. 7)| Free for non-commercial use, a monthly fee otherwise|
|[PumasAI](https://pumas.ai/)| Pharmacometrics with machine learning| Free for non-commercial use, a monthly fee otherwise |
|[SymBoltz.jl](https://hersle.github.io/SymBoltz.jl/stable/)| Solving the Einstein-Boltzmann equation in cosmology (see Ref. 8)| Free and open source| 
|[Wildlandfire.jl](https://fire.earthsci.dev/dev/)| Modeling wildland fires| Free and open source|

In addition to general applications of MTK, this tutotial also includes the specific use of Catalyst.jl and DataDrivenDiffEq.jl from the first table above since symbolic-numeric programming is central to the operation of these two packages. This tutorial also briefly considers the use of ProcessSimulator.jl and Thetis.jl from the first table above. Although these two packages are in a relatively early stage of development, they nevertheless show the future of chemical and wastewater process simulation since they are free and open source, fully differentiable, highly performant, easily customizable, highly composible with other libraries, and able to bridge symbolic and numeric representations to enhance the modeling. More generally, since all of the above software packages have MTK as their foundation, familiarity with MTK greatly facilitates their use.  

### References

1.  S. Gowda, [Symbolic-numeric programming in scientific computing](https://dspace.mit.edu/entities/publication/185c3adf-eb94-4acf-9e77-f66cb773b71b), PhD thesis, MIT, 2024.

2.  S. Gowda, [High-performance symbolics-numerical via multiple dispatch](https://dl.acm.org/doi/10.1145/3511528.3511535), ACM Commun. Computer Algebra, vol. 55, 92-96, 2021. 

3.  Y. Ma et al., [ModelingToolkit: A composable graph transformation system for equation-based modeling](https://arxiv.org/abs/2103.05244), ArXiv:2103.05244v3, 2022.

4.  T.E. Loman et al., [Catalyst: Fast and flexible modeling of reaction networks](https://pmc.ncbi.nlm.nih.gov/articles/PMC10584191/), PLOS Computational Biology, e1011530, 2023.

5.  A. Sukys et al., [MomentClosure.jl: Automated moment closure approximations in Julia](https://academic.oup.com/bioinformatics/article/38/1/289/6309452) Bioinformatics, vol. 38, 289-290, 2022.

6.  V. V. Santana et al., [ProcessSimulator.jl: A symbolic-numeric open-source framework for process simulation in Julia language](https://psecommunity.org/LAPSE:2026.0385), Systems and Control Transactions, vol. 5, 1439-1444, 2026.

7.  D. Hofmann et al., [Increasing spectral dynamic causal modeling (sDCM) flexibility and speed by leveraging ModelingToolkit and automated differentiation](https://pmc.ncbi.nlm.nih.gov/articles/PMC12330849/), Imaging Neuroscience, vol. 3, 2025

9.  H. Sletmoen, [SymBoltz.jl: A symbolic-numeric, approximation free, and differentiable linear Einstein-Boltzmann solver](https://www.aanda.org/articles/aa/full_html/2026/03/aa57450-25/aa57450-25.html), Astronomy and Astrophysics, vol. 707, A128, 2026. 

### Links to tutorial sections:

Part 1: Setup

&nbsp;&nbsp;&nbsp;&nbsp;[Installing and using Julia](https://github.com/dougfrey/Julia_tutorials_for_ChEs/blob/main/Part%201%3A%20Setup/Installing_and_Using_Julia.md)
  
&nbsp;&nbsp;&nbsp;&nbsp;[Installing and using Jupyter](https://github.com/dougfrey/Julia_tutorials_for_ChEs/blob/main/Part%201%3A%20Setup/Installing_and_Using_Jupyter_Notebooks.md)

Part 2: Background Information

&nbsp;&nbsp;&nbsp;&nbsp;[Description of ModelingToolkit.jl (MTK)](https://github.com/dougfrey/Tutorials_on_Julia_for_ChEs_and_BioChEs/blob/main/Part%202%3A%20Background%20Information/Description_of_ModelingToolkit.md)

&nbsp;&nbsp;&nbsp;&nbsp;[Summary of Programming Concepts Used](https://github.com/dougfrey/Tutorials_on_Julia_for_ChEs_and_BioChEs/blob/main/Part%202%3A%20Background%20Information/Summary_of_Programming_Concepts_Used.md)

&nbsp;&nbsp;&nbsp;&nbsp;Working with Vectors

&nbsp;&nbsp;&nbsp;&nbsp;Macros, Types and Fields

Part 3: Solving Nonlinear Algebraic Equations

&nbsp;&nbsp;&nbsp;&nbsp;[Solvers Used](https://github.com/dougfrey/Tutorials_on_Julia_for_ChEs_and_BioChEs/blob/main/Part%203%3A%20Solving%20Nonlinear%20Algebraic%20Equations/1_Solvers_Used.md)

&nbsp;&nbsp;&nbsp;&nbsp;[Problem to be Solved: Ion-Exchange Equilibrium](https://github.com/dougfrey/Tutorials_on_Julia_for_ChEs_and_BioChEs/blob/main/Part%203%3A%20Solving%20Nonlinear%20Algebraic%20Equations/2_Problem_to_be_Solved--Ion_Exchange_Equilibrium.md)

&nbsp;&nbsp;&nbsp;&nbsp;Basic Approach

&nbsp;&nbsp;&nbsp;&nbsp;Working with Indices

&nbsp;&nbsp;&nbsp;&nbsp;Highly Nonlinear Systems

&nbsp;&nbsp;&nbsp;&nbsp;Large Systems

Part 4: Optimization

Part 5: ODEs and DAEs

Part 6: Catalyst.jl

Part 7: DataDrivenDiffEq.jl

Part 8: Introduction to CellMLToolkit.jl, ProcessSimulator.jl and Thetis.jl

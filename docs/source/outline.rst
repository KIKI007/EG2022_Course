Outline
=======

.. _outline:

Introduction (25 mins)
--------------------------------

**Presenter**: Peng Song

Peng will first introduce the presenters.
He will then introduce the definition of assemblies, ubiquitous of assemblies in many applications, and advantages of assemblies compared with monolithic objects. 
The technical content of his talk will start by explaining the importance of computation in analysis, design, and fabrication of assemblies, outlining the key challenges, and motivating why computer graphics would play a central role in addressing these challenges. 
He will then define **computational assemblies** as an emerging research area that studies computational techniques for analyzing, designing, and fabricating assemblies.
After that, he will introduce the learning goal of the tutorial:
attendees should understand the main motivations for computational assemblies, feel equipped to start their own research work in this area, or to make use of existing research results to assist their design and fabrication process.
Finally, he will define scope for the tutorial, and introduce the tutorial outline as well topics to be covered by each presenter. 


Computational Analysis of Assemblies (45 mins)
-------------------------------------------------------

**Presenter**: Peng Song

In this section, Peng will present and explain computational methods to analyze different aspects of assemblies.
%He will also introduce the relevant technical basics that audience must understand to do work in computational assemblies.
Peng will first give an overview of various aspects of assemblies that are relevant to design and fabrication (e.g., aesthetics, packing efficiency), and then take a deep dive into four fundamental aspects of assemblies (i.e., parts fabricability, parts joining, assembly planning, and structural stability).
One of the key insights that Peng will share is that there are many different ways to abstract assemblies in computers, and a suitable abstraction/representation of assemblies can significantly simplify and/or speed-up the computational analysis algorithm.
%he will present and classify the state-of-the-art approaches to address the analysis problem, as well as discuss their strengths and limitations.
%For each of the four aspects of assemblies, Peng will introduce the formulation of computational analysis problem, the problem nature, and challenges to solve the problem.

Peng will start with computational analysis of parts fabricability.
He will introduce the most widely used digital fabrication techniques such as 3D printing and CNC milling, emphasize the geometric constraints associated with each fabrication technique, and explain computational methods that analyze to what degree the geometric constraints are satisfied by a given part shape.
Secondly, Peng will classify existing parts joining approaches and focus on those based on integral joints.
He will explain that the goal of an integral joint is to restrict the relative movement of two associated parts, and the ability of joining parts can be quantified by the allowed motion space of one part relative to the other.
Thirdly, Peng will classify assembly plans according to their inherent features, illustrate the assembly plans with intuitive visual examples, and introduce computational algorithms to find these assembly plans :cite:p:`Wang-2021-AssemblySurvey`, :cite:p:`Ghandi-2015-AssemblyPathPlanningReview`. 
He will introduce **assembly-by-disassembly** as an important strategy for assembly planning since parts in an assembled state have far more precedence and motion constraints than in a disassembled state.
Fourthly, Peng will introduce the equilibrium method to analyze whether a given assembly is structurally stable under known external forces.
Due to  the static-kinematic duality, structural stability can be analyzed either in the force space :cite:p:`Whiting-2009-ModelMasonry` or the motion space :cite:p:`Wang-2021-MOCCA`. 
However, the motion-based approach has a significant advantage of identifying if a given assembly is globally interlocking (i.e., equilibrium under arbitrary external forces) :cite:p:`Wang-2019-TopoLock`, which cannot be achieved by the force-based approach. 
Finally, Peng will outline directions for the future and examine the open problems around computational analysis of assemblies such as functionality analysis.

BREAK (10 mins)
----------------------------------------------

Computational Design of Assemblies (45 mins)
----------------------------------------------

**Presenter**: Ziqi Wang

In this section, Ziqi will introduce the computational methods to design assemblies with various forms and functionalities. He will first summarize the challenges of manual design to emphasize the importance of computational approaches. He will give a brief overview of typical assembly design problems and their primary objectives (e.g., assemblability, structural stability, aesthetics). His presentation then will mainly focus on designing assemblies that are structurally stable and assemblable. Typical examples include assemblies in equilibrium :cite:p:`Whiting-2009-ModelMasonry`, assemblies with lateral stability :cite:p:`Wang-2019-TopoLock`, and globally interlocking assemblies :cite:p:`Song-2012-InterCubes`, :cite:p:`Wang-2018-DESIA`. One of the main algorithmic design principles is to use proper data structures to represent assemblies in different scenarios. A well-chosen representation can reduce design variables' redundancy and improve the algorithm's performance. 

He will begin with the classic trial-and-error algorithms for creating structurally stable assemblies. This method keeps generating new designs until one of them passes the stability analysis explained in the first part of this course. However, this approach could be highly inefficient, especially when the set of feasible solutions is only a fraction of the entire design space, e.g., when designing globally interlocking assemblies. Rule-based algorithms are introduced to address this challenge :cite:p:`Song-2012-InterCubes`, :cite:p:`Song-2015-Interlock`. When adding a new part to the assembly, strict rules must be followed to maintain the structural stability of the assembly. These rules could eliminate potential solutions. To allow the algorithm to explore a larger design space, He will present the gradient-based algorithm :cite:p:`Whiting-2012-OptimizeMasonry`, :cite:p:`Wang-2021-MOCCA`, which quantitively measures the structural stability and optimize the parts' shape to improve such measurement. In particular, he will demonstrate one effective strategy, the motion-guided design algorithms :cite:p:`Wang-2021-MOCCA`. Instead of optimizing the assemblies' geometry, the motion-guided method optimizes the motion restriction imposed by contacts between parts in a conceptual way. The method then finds corresponding contacts' geometry to satisfy the motion restriction requirements. This method decouples the motion and geometry, improving the algorithmic efficiency, and is flexible in handling various applications.

Computational Fabrication of Assemblies (45 mins)
--------------------------------------------------

**Presenter**: Marco Livesu

In this section Marco will discuss algorithms that aim to decompose a complex shape in order to meet geometric or semantic restrictions imposed by fabrication hardware. Two prominent examples that fall in this category are methods that split multi-color or multi-material objects into an assembly of uniform sub-objects, and algorithms that decompose geometrically intricate objects into parts with simpler geometry, such as height fields (e.g. for subtractive CNC milling or molding) or quasi height fields (e.g. for 3D printing with minimal overhangs).

The section will start with an introduction on the most widely used fabrication techniques, such as 3D printing, CNC milling and molding. Particular emphasis will be given to the geometric and material constraints that are peculiar of each fabrication paradigm, because these constraints define the space of all and only shapes that can be fabricated with a certain hardware. 
%Indeed, given a machine and a target object, fabrication can be successful only if the object lives within the shape space defined by the available hardware.

Methods that operate by splitting an object into simpler parts always strive for **minimal** decompositions, that is, they want to create the minimum number of sub-pieces such that all input constraints are fulfilled. As for many other domain decomposition problems, this often leads to NP-Hardness, which is mitigated by the adoption of heuristic approaches that do not offer theoretical guarantees, and that mostly differentiate to each other for their ability to land in **good** local minima that correspond to practically useful solutions. 

Marco will firstly discuss the most typical constraints considered by current methods, connecting them with practical problem and specific features of fabrication hardware. Secondly, the most prominent decomposition heuristics will be analyzed and compared to each other, putting side by side surface and volumetric methods, methods based on boolean operators and methods based on clustering. Interesting cross relations between decomposition strategies and the type of constraints they support will also be discussed and emphasized.

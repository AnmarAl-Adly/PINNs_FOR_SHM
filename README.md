# PINNs_For_SHM

Physics-InformedNeuralNetworks(PINNs)for structural health monitoring: A case study for Kirchhoff-Love Plates
Physics-informed neural networks (PINNs), which are a recent development and incorporate physics-based knowledge into neural networks (NNs) in the form of constraints (e.g., displacement and force boundary conditions, governing equations) or loss function, offer promise for generating digital twins of physical systems and processes. However, applications to structural health monitoring (SHM)  as challenges related to modelling the governing physics – e.g., through partial differential equations (PDEs), and consideration of different types of loading - are still unresolved. In this paper, we investigate approaches to address these challenges using a simple structural system, a square concrete slab modelled as a Kirchhoff-Love plate under uniformly distributed loads ($UDLs$), as a case study. We train and test our models to explore how knowledge of the structure boundary conditions along with measured data can help generate accurate models of the structural system. Satisfaction of these boundary conditions, which can be expressed as derivatives of deformations and computed through automatic differentiation, is enforced through loss function. The relationship between plate deformations and loading is also enforced using loss function. The effectiveness of enforcing the structure boundary conditions on neural networks under different loading conditions, shedding light on their performance under varying scenarios and cases, is examined. Results show that the modelling of the structure boundary conditions enables the PINNs to approximate the behaviour of the structure without requiring satisfaction of the governing PDEs across the whole domain of the plate.
## Synthetic Sensor Data Measurement
The following table presents a summary of the measured data values and their corresponding locations.
| Sensor No.     |Coordinates (x, y) m |                                                                   
| -------------  | ------------------- |                                                    
| S1             |(2,2)|                                                     
| S2             |(1,1)|                                       
| S3             |(3,1)|                                                                
| S4             |(1,3)|                     
| S5             |(3,3)|       
| S6             |(2,1)|
| S7             |(2,3)|
| S8             |(1,2)|
| S9             |(3,2)|


## Case Study Sceniros 
A series of predefined scenarios are examined in depth. The examination is divided into two major parts. The first part evaluates the performance of a model under the conditions of five scenarios. These scenarios are distinguished by the varying number of measurements, ranging from one to nine in each case. For this part of the study, a key structure parameter kept constant throughout is $UDLs$. The second part of the examination takes a different approach. Instead of maintaining $UDLs$ as a constant parameter, it becomes a variable input within NNs. This part aims to comprehend how varying $UDLs$ influence the predictions made by the NNs. This shift towards considering $UDLs$ as inputs rather than constants brings us closer to real-world scenarios where the measured data often obtained under varying and unknown load conditions, increasing the relevance of this section of the study to SHM applications.


[Go to synthetic sensor data](syntheticsensordata/)

[Go to Cases under different UDLs](CasesunderdifferentUDLs/)

| Scenario      |Loss Function  |                                                      Cases         |Sensor No.     |               
| ------------- | ------------- |                                                      ------------- | ------------- |
| Performance of NNs ModeL – SN1           |$\mathcal{L}_D$|                                                     Case 0         |No measured data included|
| NNs Informed with Displacement Constrains - SN2        |$\mathcal{L}_W+\mathcal{L}_D$|                                       Case 1         |S1|
| NNs Informed with Force Constrains - SN3           |$\mathcal{L}_m +\mathcal{L}_D$|                                      Case 2         |S1, S2, S3, S4, S5|                           
|Displacement and Force Constrains Informed Neural Networks - SN4         |$\mathcal{L}_W + \mathcal{L}_m +\mathcal{L}_D$|                      Case 3         |S1, S2, S3, S4, S5, S6, S7, S8, S9|
|Physics-informed Neural Networks (PINNs)- SN5           |$\mathcal{L}_f + \mathcal{L}_W + \mathcal{L}_m +\mathcal{L}_D$|       ----          |-------|



# PINNs_For_SHM

Physics-informed neural networks (PINNs), which are a recent development and incorporate physics-based knowledge into neural networks (NNs) in the form of constraints (e.g., displacement and force boundary conditions, governing equations) or loss function, offer promise for generating digital twins of physical systems and processes. \textcolor{red} {Although recent research has begun to address the challenges associated with employing PINNs for structural health monitoring (SHM), significant issues remain unresolved, particularly with respect to modelling the governing physics through partial differential equations (PDEs) under temporally variable loading and evaluating PINN capability for dealing with aspects such as measurement noise and non-ideal boundary conditions that arise in real-world structures.} This paper investigates potential solutions to these challenges. Specifically, the paper will examine the performance of PINNs that enforce a structure's boundary conditions and utilises sensor data from a limited number of locations within it. Satisfaction of these boundary conditions, which can be expressed as derivatives of deflections and computed through automatic differentiation, is achieved through an additional term in the loss function. We also examine a PINN's ability to predict deflections and internal forces for loads that have not been included in the training data-sets. Three case studies are utilised to demonstrate and evaluate the proposed ideas. Case Study (1) assumes a constant uniformly distributed load (UDL) and analyses several setups of PINNs for four distinct simulated measurement cases obtained from a finite element model.  In Case Study (2), the UDL is included as an input variable for the NNs.  Results from these two case studies show that the modelling of the structure's boundary conditions enables the PINNs to approximate the behaviour of the structure without requiring satisfaction of the governing PDEs across the whole domain of the plate. In Case Study (3), we explore the efficacy of PINNs in a setting resembling real-world conditions, wherein the simulated measurement data incorporates deviations from idealised boundary conditions and contains measurement noise. Results illustrate that PINNs can effectively capture the overall physics of the system while managing deviations from idealised assumptions and data noise.}

## Development of PINNs
![alt text](https://github.com/AnmarAl-Adly/PINNs_FOR_SHM/blob/main/fig5.jpg)
Schematic of Physics-Informed Neural Networks (PINNs).
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

[Go to synthetic sensor data](syntheticsensordata/)

## Case Studies Sceniros
A series of predefined scenarios are examined in depth. The examination is divided into three major case studies.
## Case Study 1: 
The first part of this study evaluates the performance of a model under the conditions of five scenarios. These scenarios are distinguished by the varying number of measurements, ranging from one to nine in each case. For this part of the study, a key structure parameter kept constant throughout is $UDLs$. 

[Go to the case study 1](./Case%20study_1/SN5)

## Case Study 2:
The second part of the examination takes a different approach. Instead of maintaining $UDLs$ as a constant parameter, it becomes a variable input within NNs. This part aims to comprehend how varying $UDLs$ influence the predictions made by the NNs. This shift towards considering $UDLs$ as inputs rather than constants brings us closer to real-world scenarios where the measured data often obtained under varying and unknown load conditions, increasing the relevance of this section of the study to SHM applications.

[Go to the case study 2](./Case%20study_2)

## Case Study 3: 
This case study thus considers two additional layers of complexity, namely semi-rigid connections and data affected by noise. Our aim is to evaluate the adaptability and performance of PINNs in two scenarios: with and without the presence of the PDEs that govern the system

[Go to the case study 3](.Case%20study_3/SN4)

![alt text](https://github.com/AnmarAl-Adly/PINNs_FOR_SHM/blob/main/SNR.png)
Effect of SNR on the quality of deflection 𝑤noise data.

## Table1. Summary of the loss function scenarios and cases employed in the study.

| Scenario      |Loss Function  |                                                      Cases         |Sensor No.     |               
| ------------- | ------------- |                                                      ------------- | ------------- |
| Performance of NNs ModeL – SN1           |$\mathcal{L}_D$|                                                     Case 0         |No measured data included|
| NNs Informed with Displacement Constrains - SN2        |$\mathcal{L}_W+\mathcal{L}_D$|                                       Case 1         |S1|
| NNs Informed with Force Constrains - SN3           |$\mathcal{L}_m +\mathcal{L}_D$|                                      Case 2         |S1, S2, S3, S4, S5|                           
|Displacement and Force Constrains Informed Neural Networks - SN4         |$\mathcal{L}_W + \mathcal{L}_m +\mathcal{L}_D$|                      Case 3         |S1, S2, S3, S4, S5, S6, S7, S8, S9|
|Physics-informed Neural Networks (PINNs)- SN5           |$\mathcal{L}_f + \mathcal{L}_W + \mathcal{L}_m +\mathcal{L}_D$|       ----          |-------|


### Questions about the study

Email Anmar Al-Adly at aa1224@exeter.ac.uk .

## License

[![License: CC BY 4.0](https://img.shields.io/badge/license-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

This work is licensed under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).

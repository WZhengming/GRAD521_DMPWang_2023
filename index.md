# Research Overview

The research project we are currently working with is entitled Large-Scale Net-Shape Oxide Dispersion Strengthened (ODS) Component Manufacturing for Harsh Environments via Oxide Doping in Laser Directed Energy Deposition (LDED). This project is related to material science, mechanical engineering, and chemical engineering. Our team are entirely working on material science part, specifically, computational work. Due to excellent mechanical properties, ODS alloys are widely used in harsh environments, like nuclear reaction container. However, conventional ODS manufacturing steps are expensive and time-consuming. Therefore, the overall goal of this project is to develop a hybrid LDED oxide-doping additive manufacturing approach that makes net-shape component in a single step. This new technique is expected to reduce fabrication cost by 50% and energy consumption by 30%. The goal for our simulation is to develop an integrated model that can predict the particle size distribution in the as-built ODS sample with process parameters (laser power, scan speed, etc.) used in the experiment, which can further reduce the experimental cost. The experiment team will give us the particle size distribution in their samples to verify and correct our model in the beginning stage. Later our model should be able to predict the results without conducting experiment.

# Data Description

The data will be collected and analyzed in different software. We will collect a lot of datasets for this research:

3D model: A 3D model will be created in AutoCAD or downloaded from Flow3D website in a .stl file that will be the input for Flow3D.

Laser power and scan speed: They are the simulation conditions for Flow3D so they are metadata. They will be recorded in a .csv file.

Temperature: Flow3D will simulate the LDED process and generate a .f3d file that includes simulation results, such as velocity, temperature, in a 3D model. The .f3d file will be analyzed in Flow3D post-processing to get the temperature as a function of time at a concerned point. This temperature profile will be exported as a .csv file.

INCAR, KPOINT, POSCAR, POTCAR: We will create these files as inputs for Vienna Ab initio Simulation Package (VASP). They are all plain text files.

Diffusivity: VASP will generate a plain text file, called XDATCAR, that includes the position of all atoms in the sample. This file will be read in Ovito to calculate the displacement of certain atoms as a function of simulation steps. The displacement and simulation steps will be saved as a XYZ file. Then the XYZ file will be analyzed in Matlab to calculate the diffusivity that will be manually recorded in a .csv file as a numerical data. The diffusivity will be calculated at different temperatures. Therefore, we need the temperature data from Flow3D. 

Sample behavior: Some .png figure and .avi videos will also be exported from Ovito to demonstrate how atoms move in the sample.

Binding energy: Another plain text file OUTCAR will be created by VASP as well. The OUTCAR will be imported to Matlab directly. The numerical energy data will be read and recorded in a .csv file. The Binding energy will also be calculated at different temperatures. 

Fortran90 code: This is metadata for implementing temperature, diffusivity, and binding energy to simulate particles evolution in the sample.

Matlab code: This is metadata for analyzing outputs from Fortran90 and VASP.

Particle size distribution: Some binary files that include time steps and size and position of atoms will be exported from Fortran90 code and analyzed in Matlab. Finally, the output from the Matlab is a .png figure that shows the model with particles and a histogram of particle sizes. A .avi video will also be made in Matlab to show the particles evaluation. 

Experimental data: The experiment team will share the particle size distribution in experimental samples with us for comparison and verification our simulation results.

Therefore, the total data created in this research will be 2-3TB.

# Roles and responsibilities

In our research project, my PI has developed the data management plan for our and will be the primary person responsible for ensuring the DMP is implemented correctly. I will be responsible for most data management roles in our research project with the PI’s guidance. It’s my responsibilities to generate and collect the data (temperature and plain text files) from the software (Flow3D and VASP), while the PI and I will be responsible for maintaining the software and ensuring the data quality is acceptable for later analysis. Later, I will manage and analyze the data with Matlab and Fortran code that I have created, and generate the data (diffusivity, binding energy and particle size distribution) that we need to achieve the aims of this project. Furthermore, it will be my responsibility to share data and communicate with the experiment groups. Finally, the PI and I will archive and preserve our data generated in this project. 

There are 3 graduate students who are from 3 groups working in this project. If someone left the project, his PI would handle the data and find another graduate student to take over the responsibilities. Because we will update and share the data weekly, if someone left, it will not affect the project.

Our project is funded by the government, so our data will be publicly available after this project. Since the data is not sensitive or confidential according to OSU’s classification, we will share the data through Box. 

# Data standards and metadata

Basically, I will collect three datasets from three parts of my research project. They are the data from Flow3D software, VASP software, and Fortran code, so I will make three sub-folders for them. The name of them will be Flow3D, VASP, and Fortran.

Flow3D: I only need one .stl file as the input for Flow3D, so I will name it as ‘LPBF_3Dmodel.stl’. Some .f3d files that includes simulation results, such as velocity, temperature will be generated by the software. Since only one version of them will be preserved, I don’t need any version control strategy for this part. Their file names will be in ‘LaserPower_ScanSpeed.f3d’. The Laser power and scan speed are the simulation conditions. Later, those .f3d files will be analyzed in Flow3D post-processing, and the results, like time and temperature, with their units will be recorded in one ‘Flow3DResults.xlsx’ file. Each spread sheet corresponds to each .f3d file and has the name ‘LaserPower_ScanSpeed’ as well. I only need a Readme.text in this folder to explain how to use and analyze the data, which version of the software was used, and what the file names mean.

VASP: Some plain text files INCAR, KPOINT, POSCAR, POTCAR will be made and XDATCAR will be generated for each sample, so I will make a lot of sub-folders for all samples. The name of the folder will be ‘SampleSize_SampleCondition’. The version control strategy is not required for this part as well because I will have only one version of data for each sample. Some .png figures and .avi videos may be exported from Ovito and saved in the corresponding folders with a name ‘SampleState_PhysicalTime’. Two Matlab .m files, ‘Diffusivity’ and ‘BindEnergy’, will be created as the metadata to calculate diffusivity and binding energy. The Matlab code includes the variables, units, equations and steps used for analysis and calculation. The results from Matlab code will be saved in ‘Diffusivity.csv’ and ‘BindingEnergy.csv’ respectively. Again, a Readme.text may be enough for this folder. It will include the information about the version of software, sub-folders’ name.

Fortran: Some sub-folders will be created in this folder for different purposes of the simulation. Those sub-folders will be named as ‘BreifDescriptionOfSystem’. Inside each sub-folder, the Fortran code will be named as ‘BreifDescriptionOfSystem_YYYY_MM_DD’ and have the varibles, units, and equations for the simulation. The version of it will be manually controlled based on updated date. All results of the simulation will be saved as ‘VariableName’, and only the latest version will be archived in the sub-folder. Later, one Matlab code, called ‘read_data.m’, will be created to read and analyze the results from Fortran code. In this metadata, the variables, units, equations, and step-by-step instruction will be provided to generate the particle size distribution data which will be saved as ‘BreifDescriptionOfSystem.png’ and ‘BreifDescriptionOfSystem.avi’ in each sub-folder. The Fortran and Matlab code have enough explanation and comments to show other people how to use them, so I don’t need to make any additional note.

# Storage and security

For the data generated by our group, I will save the data on both OSU’s high performance computing cluster (HPC) and my laptop. OSU IT team will be responsible for preserving the data on HPC. The PI has the ownership of the folder on HPC where I retain the data, so he will have the access to the data even after I graduate. The PI will also download the data to his laptop. Additionally, I will save one copy of the data in a solid-state drive as well to ensure that we have a backup copy of the data in case I lost or broke my laptop. Therefore, my PI and I will have at least 4 copies of our data. All data archiving and preservation will be done manually. I need to manually create some sub-folders on HPC for different simulation jobs and download them to my laptop. Therefore, I need PuTTY to connect to HPC, perform simulations, and manage the data on HPC. After that, I will download the data to my laptop by using WinSCP. We will not use any network drive or cloud system for data storage in this project.

# Access and data sharing
# Archiving and preservation

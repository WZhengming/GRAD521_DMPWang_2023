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
# Data standards and metadata
# Storage and security
# Access and data sharing
# Archiving and preservation

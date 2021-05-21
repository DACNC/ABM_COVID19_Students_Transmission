# ABM_COVID19_Students_Transmission

- *David Alvarez Castro.* PhD student in Geospatial Systems CDT, Newcastle University (contact d.alvarez2@newcastle.ac.uk).
- *Alistair Ford.*  Lecturer in Geospatial Data Analytics and Policy Academy Fellow, Newcastle University.


This is the GitHub repository containing the GAMA code developed and GIS open data to simulate geospatial case-scenarios of the transmission of COVID-19 between students living at student accommodation.

This project was developed as part of the Thesis in Master of Research in Geospatial Data Science, at Newcastle University (academic year 2019-2020).

### Perspective views of the 3D ABM simulation
![alt text](https://user-images.githubusercontent.com/57093439/119123528-8dc63480-ba27-11eb-9571-2e757a9be69e.png)
Perspective view of the ABM, when students are located at home at the beginning of the outbreak (top left) and their daily interactions during the outbreak (bottom left and right), showing different infectious status (Susceptible (green), Exposed (yellow), Infective (red), Recovered (blue)). Contains Ordnance Survey data © Crown copyright and database right 2020.


## Requirements
- This code was developed using GAMA Platform, version 1.8 (released on the 31st of July, 2019) (https://gama-platform.github.io/download).
- It is required to install Java 8x64.
- Environmental variables should be updated as follow: PATH variable should contain an option pointing to folder: ../Java/jre1.8.0_171/bin


## Installation
To install GAMA platform, follow steps from GAMA website:
- https://gama-platform.github.io/wiki/InstallationAndLaunching


## GAMA codes
Once GAMA platform is installed and Workspace folder is set up, the following two models should be stored in folder "models":

- 3D_epidemic_pedestrian_ABM_single_simulation.gaml
- 3D_epidemic_pedestrian_ABM_batch_mode.gaml

The first one runs the code once. GUI can be used, where the user can set up the initial parameters (left hand side of the screen), start the simulation and see how agents behave in real time (central part of the screen) and obtain real time information about the evolution of the infectious disease (right hand side of the screen).

The second one runs the code as a batch, simulating in parallel several simulations at the same time. Initial parameters are defined in the code and results are only shown when all simulations are finished.  

## GIS datasets
GIS data has to be located in folder "includes".
- Buildings: Dataset 'OS MasterMap Building Height Attribute’ was collected from Ordnance Survey section on the Digimap website (https://digimap.edina.ac.uk/os). Academic registration is required to obtain this data. This dataset has to be split in two based on paper explanations: 
	- Buildings_with_interactions.shp
	- Buildings_no_interactions_only.shp
- Footpaths: This dataset was developed from the ‘OS OpenMap Local roads’ layer (Ordnance Survey). It is open-source and can be found in this repository ("GIS datasets" folder).
- Students: Dataset containing the students living at student accommodation, located at specific acommodation (3D position) and with individual daily routines set up in the attribute table. It is open-source and can be found in this repository ("GIS datasets" folder).
- Statics: This dataset contains static agents (e.g., any unanimated element in the environment that can transmit an infectious disease when has been in close contact with an infective agent). These agents were located inside buildings based on assumed probability of interaction, the likelihood to be infected by them when in contact, and the approximate number of times students interact with them, in each type of building. It is open-source and can be found in this repository ("GIS datasets" folder).
- Dynamics: This dataset contains dynamic agents (e.g., any person that can interact with students in their daily routines and static agents). They were located inside buildings. These agents do not follow any daily routine and are always moving randomly inside the building they were located. It is open-source and can be found in this repository ("GIS datasets" folder).
- Project scale boundary: dataset identifying the area of the project. It is open-source and can be found in this repository ("GIS datasets" folder).


**For more information about the attribute tables of each described GIS dataset , please refer to Appendix B in the paper.**


## Output data
The following files are generated once simulation is finished:
- ABM_SEIR_values_per_day.csv: this file contains the evolution in time of the disease. It shows the number of Susceptible, Exposed, Infective and Recovered students per day. When plotting this data in a chart, it is possible to identify the duration of the disease in the environment, when Exposed and Infective peak values were reached and the speed in the evolution based on the slopes of the curves.
- Agents_after_simulations.csv: this file contains individual information of eve-ry student in the model, recording their status related to the disease (S-E-I-R), and time and location (x, y, z coordinates in EPSG 27700) of infection and by whom in the case of infection. This information allows spatial analysis of in-fection, identifying the places where most infections occurred 
- Transmission_list.csv: this file contains information about how the disease was transmitted between agents recording the ID value and the ID value of the agent that infected them for each Student, Dynamic and Static agent. This in-formation allows tracking the transmission of the disease between agents
- Initial_data_and_parameters.txt: this file contains the initial input data and parameter values set up by the user before running the simulation. This file is useful to keep track of the parameters used in each simulation. 

The attribute table of each described output file can be consulted in the Appendix C of the paper.

These files are generated in folder "results".


## Assumptions and limitations

- Simulations are run with one-minute time steps starting on the 14th of March 2020. 
- There is no differentiation of agents in terms of age or gender, and all accommodation is identical. 
- All students return to their original accommodation each night. 
- Students are assumed to be aged between 18 and 30 years, and as such deaths were not consid-ered in the model as deaths from COVID-19 are almost zero in this age group 
- Asymptomatic cases are not considered




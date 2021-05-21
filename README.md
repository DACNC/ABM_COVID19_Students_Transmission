# ABM_COVID19_Students_Transmission

This is the GitHub repository containing the GAMA code developed and open data to simulate geospatial case-scenarios of the transmission of COVID-19 between students living at student accommodation.

This project was developed as part of the Thesis in Master of Research in Geospatial Data Science, at Newcastle University (academic year 2019-2020).

## Requirements:
- This code was developed using GAMA Platform, version 1.8 (released on the 31st of July, 2019) (https://gama-platform.github.io/download).
- It is required to install Java 8x64.
- Environmental variables should be updated as follow: PATH variable should contain an option pointing to folder: ../Java/jre1.8.0_171/bin


## Installation
To install GAMA platform, follow steps from following GAMA website:
- https://gama-platform.github.io/wiki/InstallationAndLaunching


## GAMA codes
Once GAMA platform is installed and Workspace folder is set up, the following two models should be stored in folder "models":

- 3D_epidemic_pedestrian_ABM_single_simulation.gaml
- 3D_epidemic_pedestrian_ABM_batch_mode.gaml

The first one runs the code once. GUI can be used, where the user can set up the initial parameters (left hand side of the screen), start the simulation and see how agents behave in real time (central part of the screen) and obtain real time information about the evolution of the infectious disease (right hand side of the screen).

The second one runs the code as a batch, simulating in parallel several simulations at the same time. Initial parameters are defined in the code and results are only shown when all simulations are finished.  

## GIS data
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


Once simulations are finished results will be allocated in folder "results"


## Assumptions and limitations:

- Simulations are run with one-minute time steps starting on the 14th of March 2020. 
- There is no differentiation of agents in terms of age or gender, and all accommodation is identical. 
- All students return to their original accommodation each night. 
- Students are assumed to be aged between 18 and 30 years, and as such deaths were not consid-ered in the model as deaths from COVID-19 are almost zero in this age group 
- Asymptomatic cases are not considered

https://user-images.githubusercontent.com/57093439/119123528-8dc63480-ba27-11eb-9571-2e757a9be69e.png
Image contains Ordnance Survey data © Crown copyright and database right 2020.


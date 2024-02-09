# Master thesis
## Impact of Grid Infrastructure Limits on Electric Vehicle Charging Access for California Households
*Berkeley, February 2024*

This repository contains all the codes, figures, and some raw data tables used in the study ['Impact of Grid Infrastructure Limits on Electric Vehicle Charging Access for California Households'](https://github.com/louisrosset/MP_Grid_limits_EV_charging/files/14219976/240209_Grid_limits_EV_charging.pdf). ICA data tables could not be uploaded due to their large volume. The files are organized into folders numbered 1 through 7, each corresponding to a different stage of the analysis.

A diagram illustrating the architecture of the repository is displayed at the end of the README file.

***

All the R and python files in this repository are briefly described below.

**01_demodata.Rmd**
- Gathers demographic information for census block groups in California.
- Census data, downloaded through the [Census Bureau](https://data.census.gov/), are from the "American Community Survey, ACS 5-Year Estimates"
- [CalEnviroScreen](https://oehha.ca.gov/media/downloads/calenviroscreen/report/calenviroscreen40reportf2021.pdf) data are from CalEnviroScreeen 4.0 results
- Output: bgCAcensusCES.csv

**02_cpolys.Rmd**
- Pulls in circuit polygon data (outputs from ArcGIS) and analyzes outcomes of spatial processing.
- SCE inputs: SCE_ICAall_cspoly.csv, SCE_ICAall_cpolybg.csv, SCE_ICAall_ctotpoly.csv
- PG&E inputs: PGE_ICA23_cspoly.csv, PGE_ICA23_cpolybg.csv, PGE_ICA23_cpolybg_ICAavail, PGE_ICA23_ctotpoly.csv, PGE_subs.csv
- Demographic data inputs: bgCAcensusCES.csv
- Outputs: PGE_all.csv, PGE_ICAall.csv, PGE_ICAallreal.csv, SCE_ICAall.csv, SCE_ICAallreal.csv

**03_features.Rmd**
- Assembles and cleans features to be used in regression runs.
- Inputs: PGE_all.csv, PGE_ICAall.csv, SCE_ICAall.csv, bgCAcensusCES.csv
- Outputs: PGE_ICAalldemo.csv, PGE_ICAalldemoreal.csv, SCE_ICAalldemo.csv, SCE_ICAalldemoreal.csv

**04_allocation.Rmd**
- Assigns hosting capacity to households.
- Inputs: PGE_ICAalldemo.csv, PGE_ICAalldemoreal.csv, SCE_ICAalldemo.csv, SCE_ICAalldemoreal.csv
- PG&E outputs: PGE_ICAalldemoalloc.csv,  PGE_ICAalldemorealalloc.csv,  PGE_ICAalldemotrees.csv,  PGE_ICAalldemotrees_real.csv
- SCE outputs: SCE_ICAalldemoalloc.csv, SCE_ICAalldemorealalloc.csv, SCE_ICAalldemotrees.csv, SCE_ICAalldemotrees_real.csv

**05_access.Rmd**
- Calculates overall household access and evaluates household access based on the sizes of residential buildings.
- There is three other variants of this code, focusing on: access by all county, access by most populated counties, vehicles access.
- Inputs: PGE_ICAalldemoalloc.csv, SCE_ICAalldemoalloc.csv
- Outputs: Fig. 3.2, Fig. 3.3, Fig. 4.2, Fig. A.2, Tab. 3.1, Tab. A.6

**05_access_scenarios.Rmd**
- Projects scenarios of charging demand and analyses household access for each scenario and considering the residential building sizes
- Outputs: Fig. 5.1, Fig. A.8, Tab. 5.1, Tab. A.7, Tab. A.8

**06_analysis.Rmd**
- Analyzes the relationships among various service, infrastructure, and demographic features in relation to the hosting capacity.
- three other variants of this code, focusing on: (1) same relationships but at a county level and (2) relationships between proportion of multi-unit dwellings and demographic features. 
- Outputs: Fig. 3.5, Fig. 4.1, Fig. A.6, Fig. A.9, Fig. A.10

**07_regression.ipynb**
- Calculates accuracy of linear and random forest (RF) regression models for hosting capacity prediction
- Assesses all variable importance as predictors

**07_regression_plot.Rmd**
- Generates plots of the results produced by the Python notebook '07_regression.ipynb'.
- Calculates the interactions between all variables using iterative random forest (iRF) models. More information on iRF in [Basu et al., 2018](http://dx.doi.org/10.1073/pnas.1711236115).
- Outputs: Fig. 3.4, Fig. A.3, Tab. A.5

![Repository architecture diagram](https://github.com/louisrosset/MP_Grid_limits_EV_charging/blob/master/Code_architecture_diagram.png "Repository architecture diagram")

# Master thesis
## Impact of Grid Infrastructure Limits on Electric Vehicle Charging Access for California Households
Berkeley, February 2024


***

**01_demodata.Rmd**
- Gathers demographic information for census block groups in California.
- Census data, downloaded through the Census Bureau, are from the "American Community Survey, ACS 5-Year Estimates"
- CalEnviroScreen data are from CalEnviroScreeen 4.0 results
- Output: bgCAcensusCES.csv

**02_cpolys.Rmd**
- Pulls in circuit polygon data (outputs from ArcGIS) and analyzes outcomes of spatial processing
- SCE inputs: SCE_ICAall_cspoly.csv, SCE_ICAall_cpolybg.csv, SCE_ICAall_ctotpoly.csv
- PG&E inputs: PGE_ICA23_cspoly.csv, PGE_ICA23_cpolybg.csv, PGE_ICA23_cpolybg_ICAavail, PGE_ICA23_ctotpoly.csv, PGE_subs.csv
- Demographic data inputs: bgCAcensusCES.csv
- Outputs: PGE_all.csv, PGE_ICAall.csv, PGE_ICAallreal.csv, SCE_ICAall.csv, SCE_ICAallreal.csv

**03_features.Rmd**
- Assembles and cleans features to be used in regression runs
- Inputs: PGE_all.csv, PGE_ICAall.csv, SCE_ICAall.csv, bgCAcensusCES.csv
- Outputs: PGE_ICAalldemo.csv, PGE_ICAalldemoreal.csv, SCE_ICAalldemo.csv, SCE_ICAalldemoreal.csv

**04_allocation.Rmd**
- Assigns hosting capacity to households
- Inputs: PGE_ICAalldemo.csv, PGE_ICAalldemoreal.csv, SCE_ICAalldemo.csv, SCE_ICAalldemoreal.csv
- PG&E outputs: PGE_ICAalldemoalloc.csv,  PGE_ICAalldemorealalloc.csv,  PGE_ICAalldemotrees.csv,  PGE_ICAalldemotrees_real.csv
- SCE outputs: SCE_ICAalldemoalloc.csv, SCE_ICAalldemorealalloc.csv, SCE_ICAalldemotrees.csv, SCE_ICAalldemotrees_real.csv

**05_access.Rmd**
- Calculates overall household access and evaluates household access based on the sizes of residential buildings
- There is different variants of this code, focusing on: access by all county, access by most populated counties, vehicles access.
- Inputs: PGE_ICAalldemoalloc.csv, SCE_ICAalldemoalloc.csv
- Outputs: Fig. 3.2, Fig. 3.3, Fig. 4.2, Fig. A.1, Tab. A.5

**05_access_scenarios.Rmd**
- Projects scenarios of charging demand and analyses household access for each scenario and considering the residential building sizes
- Outputs: Fig. 5.1, Tab. A.6

**06_analysis.Rmd**
- Analyzes the relationships among various service, infrastructure, and demographic characteristics in relation to the hosting capacity
- Outputs: Fig. 3.5, Fig. 4.1, Fig. A.5

**07_regression.ipynb**
- Calculates accuracy of linear and random forest (RF) regression models for hosting capacity prediction
- Assesses all variable importance as predictors

**07_regression_plot.Rmd**
- Generates plots of the results produced by the Python notebook '07_regression.ipynb'
- Calculates the interactions between all variables using iterative random forest (iRF) models 
- Outputs: Fig. 3.4, Fig. A.2, Tab. A.4

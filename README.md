# Master thesis
## Impact of Grid Infrastructure Limits on Electric Vehicle Charging Access for California Households
Berkeley, February 2024

#### 01_demodata
01_demodata.Rmd
- Gathers demographic information for census block groups in California.
- Census data, downloaded through the Census Bureau, are from the "American Community Survey, ACS 5-Year Estimates"
- CalEnviroScreen data are from CalEnviroScreeen 4.0 results

#### 02_cpolys
02_cpolys.Rmd
- Pulls in circuit polygon data (outputs from ArcGIS) and analyzes outcomes of spatial processing
- Key SCE inputs: SCE_ICAall_cspoly.csv, SCE_ICAall_cpolybg.csv, SCE_ICAall_ctotpoly.csv
- Key PG&E inputs: PGE_ICA23_cspoly.csv, PGE_ICA23_cpolybg.csv, PGE_ICA23_cpolybg_ICAavail, PGE_ICA23_ctotpoly.csv, PGE_subs.csv
- Other key inputs: bgCAcensusCES.csv
- Key outputs: PGE_all.csv, PGE_ICAall.csv, PGE_ICAallreal.csv, SCE_ICAall.csv, SCE_ICAallreal.csv

#### 03_features
03_features.Rmd
- Assembles and cleans features to be used in random forest and linear and logistic regression runs
- Key inputs: PGE_all.csv, PGE_ICAall.csv, SCE_ICAall.csv, bgCAcensusCES.csv
- Key outputs: PGE_ICAalldemo.csv, PGE_ICAalldemoreal.csv, SCE_ICAalldemo.csv, SCE_ICAalldemoreal.csv

#### 04_allocation
04_allocation.Rmd
- Assigns hosting capacity to households
- Key inputs: PGE_ICAalldemo.csv, PGE_ICAalldemoreal.csv, SCE_ICAalldemo.csv, SCE_ICAalldemoreal.csv
- Key PG&E outputs: PGE_ICAalldemoalloc.csv,  PGE_ICAalldemorealalloc.csv,  PGE_ICAalldemotrees.csv,  PGE_ICAalldemotrees_real.csv
- Key SCE outputs: SCE_ICAalldemoalloc.csv, SCE_ICAalldemorealalloc.csv, SCE_ICAalldemotrees.csv, SCE_ICAalldemotrees_real.csv

#### 05_access
05_access.Rmd
- Calculates grid access for households served by PG&E and SCE, considering residential building sizes
- Key inputs: PGE_ICAalldemoalloc.csv, SCE_ICAalldemoalloc.csv
- Key outputs: TO COMPLETE

05_access_county_all.Rmd
- Calculates grid access for households considering residential building sizes, for all counties

05_access_county_focus.Rmd
- Calculates grid access for households for specific counties considering residential building sizes

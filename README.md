# BC Chronic Disease Dashboard

<!-- badges: start -->
[![Lifecycle:Dormant](https://img.shields.io/badge/Lifecycle-Dormant-ff7f2a)](https://github.com/bcgov/repomountie/blob/master/doc/lifecycle-badges.md)

The BC Chronic Disease Registry (CDR) is a data product that captures
information about the rate of new and persistent cases of chronic
diseases across the province. Age-standardized rates of disease are
studied for different regions, including HAs (Health Authorities) and
CHSAs (Community Health Service Areas), as well as for demographic
variables such as sex.

In this project we aim to create an interactive dashboard that will
allow users of all technical expertise to explore and visualize spatial
and temporal information of the disease rates in the data, and to
develop an analysis pipeline that will describe the temporal trends in
the data.

### Usage

Our data product is currently available for internal use only. Please
contact the CDR Working Group to request access to the data. To re-run
the analysis and run the dashboard, please ensure that R (version 4.2.0)
and RStudio are installed, then follow the respective instructions
below.

#### Modelling

1.  Clone this Github repository.
2.  Create a folder named “data” in the root directory of the
    repository. Download and save the “Data_T\_CHSA” inside this “data”
    folder.
3.  Open the `opho-cdr-shiny.Rproject` file in RStudio. Run the
    following command in the R console to install the package
    dependencies or manually as listed below: `renv::restore()`
4.  Run the following command using the command line/terminal from the
    root directory of the project: `make all`
5.  To view the temporal model visualizations in a Shiny document, check
    that results have been output to “results/model”. Run the following
    command in the R console:
    `rmarkdown::run('src/model/02_visualize.Rmd')`
6.  To view the Joinpoint Regression results, check that results have
    been output to “results/model”. To veiw the method paper, run the
    following command in the R console:
    `rmarkdown::run('src/joinpoint/joinpoint_method.rmd')`

#### Dashboard

1.  Clone this Github repository
2.  Create a `data/` directory within the `src/dashboard/` director, and
    save the original and modeled data inside in folders named “raw” and
    “model” respectively. The data inside the `raw` folder should be
    saved from the “Data_MFT_HA_CHSA” dataset, and the data inside the
    `model` folder should be saved from running the Models (Both
    Temporal and Joinpoint Regression) above. The folder structure
    should look as follows:

<!-- -->

    .
    ├── ...
    ├── src                                  
    │   ├── dashboard                         
    |   │   ├── data                              
    |   │   |   ├── model                         # Modeled Data from Modelling
    |   │   |   |   ├── HSCPrevalence  
    |   │   |   |   |   ├── AMI_EPI.csv 
    |   │   |   |   |   ├── ASTHMA_EPI.csv 
    |   │   |   |   |   └── ...
    |   │   |   |   ├── IncidenceRate 
    |   │   |   |   |   ├── ALZHEIMER_DEMENTIA.csv 
    |   │   |   |   |   ├── AMI.csv 
    |   │   |   |   |   └── ...
    |   │   |   |   └── LifePrevalence 
    |   │   |   |   |   ├── ALZHEIMER_DEMENTIA.csv 
    |   │   |   |   |   ├── AMI.csv 
    |   │   |   |   |   └── ...
    |   │   |   |   └── joinpoint_for_shiny_df.fst
    |   │   |   |   └── joinpoint_results.csv
    |   │   |   └── raw                            # Original Data from "Data_MFT_HA_CHSA'
    |   │   |       ├── HSCPrevalence 
    |   │   |       |   ├── AMI_EPI.csv 
    |   │   |       |   ├── ASTHMA_EPI.csv 
    |   │   |       |   └── ...
    |   │   |       ├── IncidenceRate 
    |   │   |       |   ├── ALZHEIMER_DEMENTIA.csv 
    |   │   |       |   ├── AMI.csv 
    |   │   |       |   └── ...
    |   │   |       └── LifePrevalence 
    |   │   |           ├── ALZHEIMER_DEMENTIA.csv 
    |   │   |           ├── AMI.csv 
    |   │   |           └── ... 
    │   |   └── ...  
    │   └──  ...                                 
    └── ...

1.  Run the following command using the command line/terminal from the
    root directory of the project:

<!-- -->

    shiny::runApp('src/dashboard')

### Dependencies

-   R version 4.2.0 and R packages:

    -   here=1.0.1
    -   tidyverse=1.3.1
    -   ggplot2=3.3.6
    -   R-INLA=22.05.07
    -   docopt=0.7.1
    -   shiny=1.7.1
    -   shinyjs=2.1.0
    -   plyr=1.8.7
    -   leaflet=2.1.1
    -   sp=1.4-7
    -   rgdal=1.5-32
    -   plotly=4.10.0
    -   scales=1.2.0
    -   shinycssloaders=1.0.0
    -   rgeos=0.5-9
    -   shinyWidgets=0.7.0
    -   DT=0.23
    -   shinyBS=0.61.1
    -   fANCOVA=0.6-1
    -   segmented=1.6-0
    -   broom=0.8.0
    -   modelr=0.1.8
    -   purrr=0.3.4
    -   fst=0.9.8

-   GNU make 3.81

### Project Status

### Getting Help or Reporting an Issue

To report bugs/issues/feature requests, please file an
[issue](https://github.com/bcgov/opho-cdr-shiny/issues/).

### How to Contribute

If you would like to contribute, please see our
[CONTRIBUTING](CONTRIBUTING.md) guidelines.

Please note that this project is released with a [Contributor Code of
Conduct](CODE_OF_CONDUCT.md). By participating in this project you agree
to abide by its terms.

### License

    Copyright 2022 Province of British Columbia

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and limitations under the License.

------------------------------------------------------------------------

*This project was created using the
[bcgovr](https://github.com/bcgov/bcgovr) package.*

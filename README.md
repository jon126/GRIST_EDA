# GRIST_EDA
Backend implementation of Grants RESTful (GRIST) API from Europe PMC for data analysis of awarded grants in life sciences in UK/EU.

## Aim:
This project aims to source data about awarded grants in the life sciences and to conduct analysis on this data.

## Data Source:
Grants RESTFul (GRIST) API from Europe PMC.
This provides coverage of funding from BBSRC UK; CRUK; NIHR; ERC; MRC UK; Wellcome Trust; WHO and more.
API Documentation: https://europepmc.org/GristAPI

## Workflow

1) Input search term of interest
2) Python3's urllib will interface withe GRIST API to spit out .json file for each 25 results from search term
3) SQLite3 database will be used to cache each .json file for each page
4) Once all .json files have been cached, Python3 will run through each .json file & strip out details from each grant entry and store them in a Numpy array with each row reflecting separate ID:
- Full Name
- Institution Name
- Institution Department
- Start Date
- End Date
- Grant Title
- Grant Abstract
- Grant Source
- Grant Type
- Grant Worth + Currency

5) Once, Numpy array has been constructed as so, it will be converted to a tsv named with the particular 'search term' used which can then be read into a tibble in R.

6) Analysis of that particular 'search term' data can then be carried out to answer the following questions:
- Who is the most well-funded for that 'search term' & when?
- Which research institution is most well-funded for that 'search term' and when?
- How much money has that 'search term' been funded in the past 2,5,10 years?


7) Comparative analysis can also be conducted between tibbles for 'search terms'
- How much money per grant is awarded between the different 'search terms'?
- How much total money is awarded over the years for different 'search terms'?
- How many grants have been awarded over the years for different 'search terms'?

8) Data will be outputted in the form of a flexdashboard::flex_dashboard or as part of frontend of Shiny web app.

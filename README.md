# TaxiDataTools
To extract relevant taxi data for NYC Yellow Cabs databases with Julia

## First step: Download and Merging
- Download a year of data at https://uofi.app.box.com/NYCtaxidata
- Put the 12 monthly zips inside a *data* folder
- Use **merging_dataset.sh** to create CSVs with fares and trips : just applying http://hafen.github.io/taxi/. It will also run steps 2 and 3 automatically.

## Second step: Only keeping what is needed.
We are only interested in the following information:
- GPS Coordinates of pick-up and drop-off
- Time and date of pick-up and drop-off
- Total fare of the ride and tip
- Rides from Manhattan to Manhattan only.

Use **data_transform.jl** to remove anything that is not needed, and to only select rides from Manhattan to Manhattan.

## Third step: Converting to binary files for faster computations
**to_JLD.jl** can be executed to convert the data into a DataFrames with extremely fast loading time. (slow to run). It also convert the GPS coordinates into the ENU system

___________________________________
##Example of data manipulation and subsetting:
- **traveltime_data.jl** projects GPS coordinates onto the nearest node and filters the rides given a time of the day (ex: 12 to 2, weekdays). Also tries to remove bad data-points.


___________________________________
## Other

- **google_query.R** : Example of query on the dataset using Google's BigQuery free service.

___________________________________
*Rem*: All the data files have to be put into a "data" folder.

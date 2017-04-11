# acs-summary-files
## Summary
A Python script that assembles large batches of American Community Survey (ACS) summary files

## Get Started
1. Clone this repository to your local machine
1. Using the repository's existing file structure, download and store the required ACS input data in the appropriate subfolders
1. Once all inputs are downloaded and extracted, you can run the `5yr2015SummaryFileAssembler.py` script from the command line.
1. Summary files are written to Output folder

## Usage
```
$ python3 5yr2015SummaryFileAssembler.py -h

usage: 5yr2015SummaryFileAssembler.py [--help] [--measures] [--geos] [--topics|--sequences]

Assemble large batches of ACS Summary Files

optional arguments:
  -h, --help

          show this help message and exit


  -m          [{E,M} [{E,M}]],
  --measures  [{E,M} [{E,M}]]

          A list of measures to include in the output
          (E=Population Estimates; M=Margins-of-Error)


  -g      [{al,ak,...,wy,all} [{al,ak,...,wy,all} ...]],
  --geos  [{al,ak,...,wy,all} [{al,ak,...,wy,all} ...]]

          Geos (states, territories) to include in the output.
          EITHER, simply use 'all' to include every state, DC,
          Puerto Rico, and the USA (e.g. "-g all"), OR, provide
          a list of desired geos from the following: lowercase
          two-character state postal abbreviations, 'dc' for
          Washington, D.C., 'pr' for Puerto Rico, and 'us' for
          USA (e.g. "-g ak dc us wy"). If the 'all' argument is
          passed at all (e.g. "-g ak wy all") the program
          assumes all geos should be used.


  -t        [{UnweightedCount,
            AgeSex,
            Race,
            HispanicOrigin,
            Ancestry,
            ForeignBirth,
            PlaceOfBirth,
            ResidenceLastYear,
            JourneyToWork,
            Children,
            Grandparents,
            HouseholdsFamilies,
            MaritalStatus,
            Fertility,
            SchoolEnrollment,
            Education,
            Language,
            Poverty,
            Disability,
            Income,
            Earnings,
            Veterans,
            TransferPrograms,
            EmploymentStatus,
            Industry,
            Housing,
            GroupQuarters,
            HealthInsurance,
            QualityMeasures,
            Imputations} [{UnweightedCount,...,Imputations} ...]],
  --topics  [{UnweightedCount,...,Imputations} [{UnweightedCount,...,Imputations} ...]]

          Topic areas to include in the output


  -s          [{1,..,122} [{1,...,122} ...]],
  --sequences [{1,...,122} [{1,...,122} ...]]

          Sequences to include in the output (Caution: This
          argument overrides the default topic areas, and
          appropriate sequence numbers are required to use it.
          New users and those unfamiliar with ACS Summary File
          sequence template files are recommended to assemble
          files using the --topics -t argument instead of the
          --sequences -s argument.)
```

Note: The `--topics` and `--sequences` arguments are mutually exclusive. Adding the `--sequences` argument will override the default `--topics`. Users may not pass both `--topics` and `--sequences` arguments.

## Defaults
Run the assembler with default arguments:

```
$ python3 5yr2015SummaryFileAssembler.py
```

Running the default is quivalent to running with the following arguments:

```
$ python3 5yr2015SummaryFileAssembler.py -m E -g all -t AgeSex Race HispanicOrigin Ancestry ForeignBirth PlaceOfBirth ResidenceLastYear SchoolEnrollment Education Language Poverty Income Earnings EmploymentStatus Housing HealthInsurance
```

## Notes
* This script is currently configured to run only on 2015 5-year ACS Summary File input data.
* This script imports the following Python modules: `argparse`, `csv`, `json`, `os`, `sortedcontainers.SortedDict`, `xlrd`
* This script prints no status updates to the screen while running
* This script has only been tested on macOS

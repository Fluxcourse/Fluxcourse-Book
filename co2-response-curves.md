We are going to follow along with a Vignette that explains how to fit response curves using R

We'll use PEcAn - you'll use PEcAn next week to do some data assimilation

We will also look at another package written by Duursma

# Setup

```R
##### Required for PEcAN

# install packages

install.packages("devtools")

install.packages("rjags")

# load the packages

library(devtools)

library(rjags)
```

## The PEcAn Photosynthesis Package

```R
# Next Install PEcAN.photosynthesis ... this is not available through CRAN
# - but you can find it on GITHUB - this code will download and install

### This step might take a while

if (!require("PEcAn.photosynthesis", character.only = TRUE)) {
devtools::install_github("PecanProject/pecan/modules/photosynthesis")
}

knitr::opts_chunk$set(cache = TRUE)

library(PEcAn.photosynthesis)
```

## The plantecophys package:

* Modelling and Analysis of Leaf Gas Exchange Data
* Coupled leaf gas exchange model, A-Ci curve simulation and fitting, 
* Ball-Berry stomatal conductance models, leaf energy balance using Penman-Monteith,
* Cowan-Farquhar optimization, humidity unit conversions.

[https://cran.r-project.org/web/packages/plantecophys/index.html](https://cran.r-project.org/web/packages/plantecophys/index.html)

```R
# IN CASE YOU JUST ABOLUTELY HAVE TO HAVE THE LATEST VERSION
#install_bitbucket("remkoduursma/plantecophys")
#install the package

install.packages("plantecophys")

#load the package
library (plantecophys)

# REFERENCE MANUAL 
https://cran.r-project.org/web/packages/plantecophys/plantecophys.pdf

# Some utility packages# if you need to install ... then install them :)

# install.packages("dplyr")
library(dplyr)

# install.packages("tidyr")
library(tidyr)

# install.packages("ggplot2")
library(ggplot2)

# install.packages("grid")
library(grid) #required for 'unit'
```

# Loading data

## Using pre-loaded data

With the PEcAn Photosynthesis package, you have  downloaded the LICOR files collected by the FLUXCOURSE in 2012.

If you want to see the files you can go into your R directory on your computer and you can find it in the extdata folder within the PEcAN.photosynthesis package.

For example : `C:\Users\dmoore\Documents\R\R-3.4.0\library\PEcAn.photosynthesis\extdata`

The command system.file\(\)\` in R allows you to call up folders relevant to a particular package. This commant looks in the folder, scans for files with aci or aq in the filename and writes these names \(and their full path\) to the R object "filenames".

```R
## Get list of LI-COR 6400 file names (ASCII not xls)
filenames <- system.file("extdata", paste0("flux-course-",rep(1:6,each=2),c("aci","aq")), package = "PEcAn.photosynthesis")

# filenames is 12 character variables
# These files are licor files ... not CSV files, not XLSX files
# ... just the file that comes right off the machine ... it has no file extension

# PEcAN.photosynthesis contains a command call read.licor() ...I bet you can guess what it does!
# read.Licor will load an individual licor file ... if you have one.

## Load files to a list
master = lapply(filenames, read_Licor)
```

## Using your own data

You can download this year's data as a ZIP file at [https://github.com/Fluxcourse/2017\_LI-COR](https://github.com/Fluxcourse/2017_LI-COR)

![](/assets/Screen Shot 2017-07-11 at 12.29.31 AM.png)

You can do the same process with your own data .... you just need to point R to those data and load em up into a big list.

```R
my_data <- "path_to_your_data" 
# for example: my_data <- "~/Downloads/2017_LI-COR-master/07102017PSC0365_CO2response"

master = read_Licor(my_data)
```

# QA/QC Checks

The code below performs a set of interactive QA/QC checks on the LI-COR data that's been loaded.

```R
master[[1]] <- Licor_QC(master[[1]])
```

If you have more than one file loaded into the \`master\` list, you may only want to run the function for one file, rather than looping over all the files.

```R
master[[1]] <- Licor_QC(master[[1]])
```




# Installing DESeq2 via Posit Workbench for R 4.3.1:

## Logging into posit workbench to access/use R: 
### this is a tool for visualizing and interpreting RNA-seq data
### currently using version R 4.3.1
https://fiji-viz-3.int.colorado.edu/auth-sign-in?appUri=%2F
use your RC login info
TODAY, our goal is just to install all the DESeq2 packages we'll need to processing/interpreting our RNA-seq data that we ran using the nextflow pipeline


### NOTE - MAKE SURE YOU SUSPEND OR QUIT YOUR POSIT SESSION WHEN YOU ARE DONE - OTHERWISE IT WILL KEEP THOSE RESOURCES IN USE AND NO ONE ELSE CAN USE THEM


### Create new session
Session name: DESeq2_Install
Cluster: slurm
Resource profile: small (4 CPU)
queue: sandbox (always use this!)
Start session

### hard coding it into your control to make sure it always uses version R 4.3.1:
Tools --> Global Options --> default R version: 4.3.1
Then you can restart session (session tab) to make sure that it opens with this version
Note that it will ALWAYS use this version now unless you specify another version

# code for installing DESeq2:
on fiji, make a new directory for workflow & version control in your home directory (~ or /user/eroc4824, not scratch):
mkdir ~/R/Posit_libs
ls -lrt ~/R/P* --> total should be 0
ls -lrt ~/R --> list should include your Post_libs directory
nano ~/.Renviron --> type in: PATH=/opt/rh/devtoolset-10/root/bin:/usr/bin:$PATH
^this file basically tells fiji whenever you're using R, go to this file and find all this software
from now on, it should go find and download these devtools automatically

### now start a new R session in posit workbench
> assign(".lib.loc", c("/Users/eroc4824/R/Posit_libs", "/opt/R/4.3.1/lib/R/library/"), envir = environment(.libPaths))
> .libPaths()   ### this command will just spit out your new library paths --> output should be [1] "/Users/eroc4824/R/Posit_libs" "/opt/R/4.3.1/lib/R/library/"

note - you can also go into terminal on posit and that takes you directly into fiji
however, changes you make directly in fiji don't necessarily get reflected in the R space


### Install older version of curl due to v.6+ issues:
Curl is one of the dependencies for DESeq2
If we tried to install DESeq2 without this older version of curl, it will fail
> install.packages("remotes")
> library(remotes)
> install_version("curl", "5.2.3")






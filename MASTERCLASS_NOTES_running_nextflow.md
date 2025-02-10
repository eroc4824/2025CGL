## notes from rinn master class (lesson 04)

Data is here --> /scratch/Shares/rinnclass/MASTER_CLASS/DATA/mouse_wt_long_timecourse/
Pre-cooked documents for running nextflow are here --> /scratch/Shares/rinnclass/MASTER_CLASS/DATA/docs/

## we need 3 things to run nextflow (though there will ultimately be 4 things in our folder because I also made my output directory there:
  1. nextflow.config
  2. run.sh - shell script file with your script for submitting to slurm
  3. sample sheet - info on where 
  4. output directory - make this file and then path to this file in your shell script so it knows where to put the results




## Now, our goal is to make a sample sheet:
Hint - you can get these docs precooked in this file --> 

### NF-CORE website has info on input/outputs:
https://nf-co.re/rnaseq/3.14.0
We are using 
The exact format we will need for the sample sheet:
sample, fastq_1, fastq_2, strandedness

## we will also need to access our data (JR2707_R1.fastq.gz
note that there is R1 (read 1) and R2 (read 2) files for each sample
you can copy the entire thing from github and then reformat it in excel:
  paste it in
  text to columns
  can only do 1 column at a time -- paste it, go to data, text to columns, delimined, other (/)
  then you can just copy the final column that we want to a new column
  then paste the file path "/scratch/Shares/rinnclass/MASTER_CLASS/DATA/mouse_WT_long_timecourse
  paste special so it doesn't try to unformat it

transfering the samplesheet file: scp eroc4824@fiji.colorado.edu:/scratch/Shares/rinnclass/MASTER_CLASS/STUDENTS/eroc4824/MASTER_CLASS/lessons/04_RNAseq_Dox/01_Mouse_dox_wt/dox_long/samplesheet.csv /Users/eroc4824/Downloads/

## next, we need to make sure the shell script is executable --> chmod u+x run.sh
## now, we're ready to run --> sbatch run.sh
## make sure you know how to cancel a job BEFORE you run --> scancel -u eroc4824 
    this will cancel all your jobs you have running

this is a useful command for checking the status of your running job:
## tail -f nextflow.out --> this basically lets you see live updates as your job runs
squeue -u eroc4824 is an alternative way to check the status of your job, just doesn't show you much

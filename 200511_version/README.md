# README for 200511_version
Scripts written to make the most recent version of the circos plot for the genome paper. Currently, the idea is to have one main circos plot for the genome paper and also make smaller circos plots for the supplementary section with additional details.

## downsampled_circos.conf
Downsampled (GBS) for SNP density circos configuration file. Pairs with _run_downsampled_circos.sh_. 

## make_LTR_density_files_for_circos.R
This R script reads in the long terminal repeat (LTR) bed file and finds the density of _Gypsy_ and _Copia_ separately (versus LTR elements as a whole, as was done in the 200309 version. There are other types of elements besides _Gypsy_ and _Copia_, but those are grouped into one class called "other". Maybe we will eventually want to break those down into smaller components for the circos plot, but the breakdown is already done in a Supplementary Table for the manuscript--so it may not be necessary.
	
## move_LTR_files.sh
Shell script that moves files created by _run_make_LTR_density_files.sh_ and _make_LTR_density_files_for_circos.R_ into separate subdirectories.

## repeat_specific_circos.conf
Repeat-specific circos configuration file. Pairs with _run_repeat_circos.sh_. Currently it only breaks down the long terminal repeats (LTRs) into _Gypsy_, _Copia_, and _otherLTRs_. Other types of repetitive elements (long and short interspersed nuclear repeats-- _LINEs_ and _SINEs_) and DNA elements are not currently in this config file (as of 12 May 2020) because they are already present in the main circos plot. Unless we want to include them here instead?

## replace_scaffold_names_for_circos.sh
Shell script that **should** search for scaffold names according to the the Dovetail numbering system and replace them with a numbering system (1-16) that is preferred by circos using sed. I say **should** because it is not currently working when the script is submitted to the queue. It does, however, work when the code itself is entered directly on the command line. The purpose of this script is to make scaffold numbering systems understandable by circos. Specifically, this was made for the repeat-specific (gypsy, copia, other LTR) circos plot that we are planning to include in the Supplemental material.

## run_downsampled_circos.sh
Shell script that launches circos to make the GBS downsampling circos plot (config file = _downsampled_circos.conf_).

## run_make_LTR_density_files.sh
Shell script that launches the R script _make_LTR_density_files_for_circos.R_

## run_repeat_circos.sh
Shell script that launches circos to make the repeat-specific circos plot (config file = _repeat_specific_circos.conf_).
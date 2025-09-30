# Summit-analysis
> last update: 8/29/25 by JT
> 
> Code for analyzing the results of MARGO-tracked behavioral experiments, primarily for summiting in flies infected with *E. muscae*
>
> Elya lab 2025

## Table of Contents

- [Installation](#installation)
- [General summit analysis steps]
- [TBD]()

## Installation

If you have Anaconda and the summiting_environment.yml file installed, the following line of code will create an environment with compatible packages for running the analysis pipeline:

```
$ conda env create -f summiting_environment.yml
```
## General summit analysis steps: 

1. Once MARGO has finished running, retrieve address of designated MARGO output directory. This directory should contain a *.mat file with your tracking data.

2. Run convertMargo in MATLAB to generate the margoConvert.mat file required in future sets. 
```
convertMargo({'DIR/*.mat'}) # where DIR is the output directory where your Margo *.mat file lives. Include the full name of your *.mat file.
```
3. Retrieve the MARGO output directory for downstream analysis in your local environment. This directory will contain a subdirectory named raw_data that contains the raw tracking output.
The output directory will also contain your *.mat and *_margoConvert.mat files. These are required for downstream analysis. 

4. Score your boards and create a survival_data sheet exactly as described in the google doc [Protocol: Summitting Data Analysis]. Place this survival_data.xls sheet in the MARGO output folder in your local environment. 

5. Retrieve and open blindTod.m in MATLAB. This script has several dependencies - all should be in the same directory as the blindTod.m script. You can currently find it here: https://github.com/Elya-Lab/BlindTOD/tree/main/Code

6. In MATLAB, load your *_margoConvert.mat file, and run execute blindTod. You will need to manually score time of last movement in the activity traces as they appear in your screen. The scored times will be populated into your survival_data.xls sheet by blindTod. Once blindTod is done running, you will have
two new *.mat files: *_margoConvert_autodenoise.mat and *_last12hours.mat. 

7. Follow directions described above to create the summit analysis environment in your computer. This will ensure all necessary python packages are installed.

8. Open Multi-File Multi-Condition MARGO Convert Summiting Graph Creator.ipynb and set your experiment/analysis parameters. Make sure to declare the MARGO output directory where your *.mat and survival_data sheet live.
	Running this script will provide you with y-position and speed graphs for each of your experimental conditions, for up to 12 hours before death, and for the complete run.      

Previous README (to be changed soon!):

> This code is a work in progress! It is currently in a usable, but not finished, state for analyzing summiting data. Check back soon for a much better looking README file and better instuctions, as well as revised code.

> Current known issues:
> - NA (but I'm sure we'll find them!)

> If the code doesn't work as expected, please email Julius at jtabin@g.harvard.edu. However, many issues arise because of incorrect formatting of the "survival_data.xlsx" sheet. For instructions on how to do this, please see [this protocol](https://docs.google.com/document/d/19SRpimdHw6hPUJXM0fsrobkKUc5Ypd8zhV1BmTE9Skg/edit?usp=sharing) and/or [this presentation](https://docs.google.com/presentation/d/1VW9UR2XYu1eL4U_A--c2y4fPXs1X0GESYP2M_Z2HJwk/edit?usp=sharing)

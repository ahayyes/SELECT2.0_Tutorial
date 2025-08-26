# SELECT 2.0 Walkthrough 

## Example code and data for SELECT 2.0 approach DOI: 

### Outline
SELECT 2.0 is an analysis method to determine minimum selective concentrations of antibiotics and other antimicrobials. It was developed and refined from the [SELECT 1.0 method ](https://ehp.niehs.nih.gov/doi/full/10.1289/EHP6635). SELECT 2.0 uses OD readings of bacteria - either single species or mixed communities. Ideally, you will have kinetic reads, but single time point reads can also be used for this analysis. The method will identify the maximum OD for each treatment, and identify the concentration of antimicrobial at which there is a 10% reduction in growth when compared to the control (no antimicrobial) treatment, this can also be considered to be finding the EC10 of the antimicrobial. There is more detail in the method in the paper, but (briefly) a reduction in growth has been identified previously as a good proxy for selection for antibiotic resistance [Greenfield et al., 2018](https://pmc.ncbi.nlm.nih.gov/articles/PMC5826132/pdf/e01686-17.pdf) 

This repository contains an example R script and dataset which can be used to practise the SELECT 2.0 method before being used on your own data. The code here uses a default cut off time of 10 hours for exponential phase, however, please feel free to change this to suit your specific data and growth curves seen. Additionally, this approach allows for the user to understand if an effect concentration cannot be determined because the start concentration used was too low or too high, something that was not possible with the previous approach. 

If there are any problems with this code, or you require more information as to how best to alter it to your specific circumstances please either submit an issue here, or email either a.hayes4@exeter.ac.uk or a.k.murray@exeter.ac.uk.

#### Step 1 - Load your data 
Data can be loaded as either text files or csv. Code presented here will allow the user to shift the data from 'wide' to 'long'. Data will be required to be in long form to be processed and analysed correctly. There is also code here to average out replicates for each concentration tested, and to produce averages, sd, and se. 

#### Step 2 - Visualise the growth curves 
This step is technically optional but is very good practice to understand how your species or community is responding to the antibiotic (or other compound) being tested. This step also allows you to alter the exponential phase cut-off time in later steps. I wouldn't really recommend skipping this step - understanding how your bacteria(l community) is responding to your compound of choice is important, to know if the compound maintains a strong dose-response, or whether there is a binomial response occurring. Overall, it's just really good practice to get to know your data, and your bacteria(l community) of choice!

#### Step 3 - Find the EC10 
This step involves finding the maximum density of the control (no antibiotic) treatment, and finding all treatments that have growth reduced by 10% or more. The EC10 is the lowest concentration at which we see a 10% or more reduction in growth. From the EC10 a PNEC can be produced to understand the predicted no effect concentration.

#### Step 4 - Explore the rest of your data
This is not really part of the SELECT 2.0 method, but overall, I recommend using your OD readings to explore your data further. We often find that total area under the curve alters with antimicrobial concentration (and other abiotic factors) but perhaps your compound of interest alters growth rate or lag phase too!? I recommend using [gcplyr](https://mikeblazanin.github.io/gcplyr/) or [growthcurveR](https://github.com/sprouffske/growthcurver) for this. Dan Padfield has a really good [GitHub repo](https://github.com/padpadpadpad/multiskan_skyhigh_od_pipeline) that lets you read in lots of OD data and processes it using gcplyr.

# SELECT 2.0 Walkthrough 

## Example code and data for SELECT 2.0 approach DOI: 

### Outline
This repository contains an example R script and example dataset with which to use to explain the new SELECT 2.0 approach, as introduced in Hayes & Kaye et al., . SELECT 2.0 is a quick, and cost-effective way to determine effect concentrations of antibiotics. This has been shown to be a good proxy (two refs, greenfield and murray et al.,) for selection for antimicrobial resistance. The updated approach (SELECT 2.0) uses a 10% reduction in maximal OD (aka maximal density) to determine the effect concentration of the antibiotic tested. The code presented here will enable the user to determine EC10s and therefore PNECs for the compound being tested. 

The code here uses a default cut off time of XX hours for exponential phase, however, please feel free to change this to suit your specific data and growth curves seen. Additionally, this approach allows for the user to understand if an effect concentration cannot be determined because the start concentration used was too low or too high, something that was not possible with the previous (SELECT 1.0 DOI:XX) approach. 

If there are any problems with this code, or you require more information as to how best to alter it to your specific circumstances please either submit an issue here, or email either a.hayes4@exeter.ac.uk or a.k.murray@exeter.ac.uk.

#### Step 1 - Load your data 
Data can be loaded as either text files or csv. Code presented here will allow the user to shift the data from 'wide' to 'long'. Data will be required to be in long form to be processed and analysed correctly. There is also code here to average out replicates for each concentration tested, and to produce averages, sd, and se. 

#### Step 2 - Visualise the growth curves 
This step is technically optional but is good practice to understand how your species or community is responding to the antibiotic (or other compound) being tested. This step also allows you to alter the exponential phase cut-off time in later steps. 

#### Step 3 - Find the EC10 
This step involves finding the maximum density of the control (no antibiotic) treatment, and finding all treatments that have growth reduced by 10% or more. The EC10 is the lowest concentration at which we see a 10% or more reduction in growth. From the EC10 a PNEC can be produced to understand the predicted no effect concentration.

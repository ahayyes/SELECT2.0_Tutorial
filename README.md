# SELECT 2.0 Walkthrough 

## Example code and data for SELECT 2.0 approach DOI: 

### Outline
SELECT 2.0 is an analysis method to estimate selective concentrations of antibiotics and other antimicrobials. It was developed and refined from the [SELECT 1.0 method ](https://pmc.ncbi.nlm.nih.gov/articles/PMC7577113/). SELECT 2.0 uses kinetic OD readings of bacteria, and has been developed using data generated from complex bacterial communities. We have not validated this approach for use with single species but it might work for this too. SELECT 2.0 involves fitting a dose-response curve (for our data in the manuscript it was a four parameter log-logistic dose response curve) using the R package _[drc](https://cran.r-project.org/web/packages/drc/index.html)_. Then, using _drc::ED_ an effective dose of 1 is calculated. There is more detail in the method in the paper, but (briefly) a reduction in growth has been identified previously as a good proxy for selection for antibiotic resistance [Greenfield et al., 2018](https://pmc.ncbi.nlm.nih.gov/articles/PMC5826132/pdf/e01686-17.pdf) and [Murray et al., 2020](https://pmc.ncbi.nlm.nih.gov/articles/PMC7577113/) and can be used in a low-cost high throughput manner to estimate predicted no effect concentrations for antibiotics. 

This repository contains an example R script and dataset which can be used to practise the SELECT 2.0 method before being used on your own data. The code here uses a default cut off time of 10 hours for exponential phase, however, please feel free to change this to suit your specific data and growth curves. Additionally, this approach allows for the user to understand if an effect concentration cannot be determined because the start concentration used was too low or too high, something that was not possible with the previous approach.
If there are any problems with this code, or you require more information as to how best to alter it to your specific circumstances please either submit an issue here, or email either a.hayes4@exeter.ac.uk or a.k.murray@exeter.ac.uk.

#### Step 1 - Load your data 
Data can be loaded as either text files or csv. Code presented here will allow the user to shift the data from 'wide' to 'long'. Data will be required to be in long form to be processed and analysed correctly. There is also code here to average out replicates for each concentration tested, and to produce averages, standard deviation, standard error, and confidence intervals.

#### Step 2 - Visualise the growth curves 
This step is technically optional but is very good practice to understand how your microbial community is responding to the antibiotic (or other compound) being tested. This step also allows you to alter the exponential phase cut-off time in later steps. I wouldn't really recommend skipping this step - understanding how your community is responding to your compound of choice is important, to know if the compound maintains a strong dose-response, or whether there is a binomial response occurring. Overall, it's just really good practice to get to know your data, and your bacteria of choice!

#### Step 3 - Find the EC1 
This step involves fitting a dose response curve and using drc to estimate the ED1 – the antibiotic concentration at which growth is reduced by 1% or more. From the EC1 a PNECR can be produced to understand the predicted no effect concentration by dividing the EC1 by the assessment factor of 10.

#### Step 4 - Explore the rest of your data
This is not really part of the SELECT 2.0 method, but overall, I recommend using your OD readings to explore your data further. We often find that total area under the curve alters with antimicrobial concentration (and other abiotic factors) but perhaps your compound of interest alters growth rate or lag phase too!? I recommend using [gcplyr](https://mikeblazanin.github.io/gcplyr/) or [growthcurveR](https://github.com/sprouffske/growthcurver) for this. Dan Padfield has a really good [GitHub repo](https://github.com/padpadpadpad/multiskan_skyhigh_od_pipeline) that lets you read in lots of OD data and processes it using gcplyr.

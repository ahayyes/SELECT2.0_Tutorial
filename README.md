# Example code and data for the SELECT 2.0 approach introduced in Kaye et al., 2024
DOI of paper XX

## Outline
This repository contains an example R script and example dataset with which to use to explain the new SELECT 2.0 approach, as introduced in Kaye et al, 2024. SELECT 2.0 is a quick, and cost-effective way to determine effect concentrations of antibiotics. This has been shown to be a good proxy (two refs, greenfield and murray et al.,) for selection for antimicrobial resistance. The updated approach (SELECT 2.0) uses a 10% reduction in maximal OD (aka maximal density) to determine the effect concentration of the antibiotic tested. The code presented here will enable the user to determine EC10s and therefore PNECs for the compound being tested. 

The code here uses a default cut off time of XX hours for exponential phase, however, please feel free to change this to suit your specific data and growth curves seen. Additionally, this approach allows for the user to understand if an effect concentration cannot be determined because the start concentration used was too low or too high, something that was not possible with the previous (SELECT 1.0 DOI:XX) approach. 

If there are any problems with this code, or you require more information as to how best to alter it to your specific circumstances please either submit an issue here, or email either a.k.murray@exeter.ac.uk, a.hayes4@exeter.ac.uk, or s.kaye@exeter.ac.uk

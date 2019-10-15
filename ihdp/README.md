# IHDP Dataset 
This dataset is a version of the IHDP dataset used by [this paper](https://arxiv.org/pdf/1606.03976.pdf) and kindly provided by 
[Frederik Johansson](https://fredjo.com).

Originally, the data was generated using a script from [Vincent Dorie](https://github.com/vdorie/npci), but since 
the exact `R` settings have changed, the script does not produce the same dataset anymore.  

** TODO ** Ref to the Thesis where the problems with IHDP are explained. 

The data provided here 

## Covariates 
The covariates are from the Infant Health Development Program and contain 19 binary and 6 continuous variables for a total of 747 instances. There are 139 children in the treated group and 608 in the control group. 

## Outcomes
The outcomes are generated according to setting _B_ in [Jennifer Hill's original paper](https://www.tandfonline.com/action/journalInformation?journalCode=ucgs20http://pubs.amstat.org.)

1000 replications are available. To reproduce the reported scores, one has to average over the reported scores on each of the replications. 

## Lack of Overlap 
As Hill notes in her original paper, the IHDP dataset as provided here does not satisfy the overlap condition, because all non-white mothers were removed from the treated group. Thus, overlap only hold for the Conditional Average Treatment Effect of the Treated (CATT), not for the CATE (over all instances) or CATC (over control instances). 






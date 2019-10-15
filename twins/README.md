# Twins dataset 
Refers to a subset of the data collected and analysed for this paper: https://www.nber.org/papers/w10552.pdf
Data is taken from [here](https://github.com/AMLab-Amsterdam/CEVAE/tree/master/datasets/TWINS)

## Covariates 
The covariates are taken from the LBIDD-Dataset, like the `ibm_acic` data. The full dataset contains here 71.345 instances.
For the twins study, we only consider twins with low birthweights and without missing features, as described below. 

After removing all pairs where the lighter twin is heavier than 2000g and all instances with missing features, we're left with 8215 instances each with 52 features. 

## Outcomes 
The two potential outcomes are the mortality for the younger (Y(1)) and older (Y(0)) twin. Thus, in this construction, both potential outcomes are known. In order to make it a treatment effect dataset, we hide some of the data by defining a treatment. 

## Treatment 
There are different versions of how to assign treatment. We follow the elaboration in [this paper](https://papers.nips.cc/paper/7529-representation-learning-for-treatment-effect-estimation-from-observational-data.pdf)

We normalize the values column wise via `df_norm = (df - df.min()) / (df.max() - df.min())` 
The treatment is then assigned via 
```
        w = np.random.uniform(-0.1, 0.1, num_features)
        weighted = np.dot(df_norm.values, w)
        n = np.random.normal(0, 0.1, num_instances)
        ps = weighted + n
        sigmoid = 1 / (1 + np.exp(-ps))
        treatment = np.random.binomial(1, sigmoid)
```






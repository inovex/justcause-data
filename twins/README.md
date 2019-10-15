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



## Covariate Descriptions 
```
{'adequacy': 'adequacy of care',
 'alcohol': 'risk factor, alcohol use',
 'anemia': 'risk factor, Anemia',
 'birattnd': 'medical person attending birth',
 'birmon': 'birth month Jan-Dec',
 'bord_0': 'birth order of lighter twin',
 'bord_1': 'birth order of heavier twin',
 'brstate': 'state of residence NCHS',
 'brstate_reg': 'US census region of brstate',
 'cardiac': 'risk factor, Cardiac',
 'chyper': 'risk factor, Hypertension, chronic',
 'cigar6': 'num of cigarettes /day, quantiled',
 'crace': 'race of child',
 'csex': 'sex of child',
 'data_year': 'year: 1989, 1990 or 1991',
 'dfageq': 'octile age of father',
 'diabetes': 'risk factor, Diabetes',
 'dlivord_min': 'number of live births before twins',
 'dmar': 'married',
 'drink5': 'num of drinks /week, quantiled',
 'dtotord_min': 'total number of births before twins',
 'eclamp': 'risk factor, Eclampsia',
 'feduc6': 'education category',
 'frace': 'dad race',
 'gestat10': 'gestation 10 categories',
 'hemo': 'risk factor Hemoglobinopathy',
 'herpes': 'risk factor, Herpes',
 'hydra': 'risk factor Hvdramnios/Oliqohvdramnios',
 'incervix': 'risk factor, Incompetent cervix',
 'infant_id_0': 'infant id of lighter twin in original df',
 'infant_id_1': 'infant id of heavier twin in original df',
 'lung': 'risk factor, Lung',
 'mager8': 'mom age',
 'meduc6': 'mom education',
 'mplbir': 'mom place of birth',
 'mplbir_reg': US census region of mplbir',
 'mpre5': 'trimester prenatal care begun, 4 is none',
 'mrace': 'mom race',
 'nprevistq': 'quintile number of prenatal visits',
 'orfath': 'dad hispanic',
 'ormoth': 'mom hispanic',
 'othermr': 'risk factor, Other Medical Risk Factors',
 'phyper': 'risk factor, Hypertension, preqnancy-associated',
 'pldel': 'place of delivery',
 'pre4000': 'risk factor, Previous infant 4000+ grams',
 'preterm': 'risk factor, Previos pre-term or small',
 'renal': 'risk factor, Renal disease',
 'rh': 'risk factor, RH sensitization',
 'stoccfipb': 'state of occurence FIPB',
 'stoccfipb_reg': 'US census region of stoccfipb',
 'tobacco': 'risk factor, tobacco use',
 'uterine': 'risk factor, Uterine bleeding'}
```
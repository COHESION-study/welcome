# THE COHESION STUDY

## Introduction

As we are dealing with completely altered living conditions because of the pandemic, it is essential to understand how we are coping, today and in the coming months.  

The COHESION study, led by a team of researchers across Canada, evaluates the impact of the COVID-19 outbreak on individuals like you, across the country. With data you provide by completing online surveys and installing a smartphone app, you help understand how daily activities, social interactions, and the mental health of Canadians are being affected throughout, and following, the pandemic.

Collected data will be anonymized and analyzed by a team of scientists. Results will be shared with decision makers and public health experts. It will guide and inform ongoing and future public health interventions for communities and individuals alike.

More information on the [study Web site](https://cohesionstudy.ca).

## Goal of this Github workspace

This Github workspace aims at keeping track of all analyses and processing steps through which COHESION data may undergo. This will contribute to the traceability and reproduceability of analyses published in papers or blogs as well as computation of new derived variables or cleaning and standardiation of existing COHESION variables.

**Attention:** Never ever store sensitive data within a repo, public or private, be it passwords or survey data. Passwords should be stored in environment variables. Survey data should be stored outside of repo and referenced from within. Alternatively, a `data` subfolder could be created in the repo and explicitly added to the `.gitignore` file. Note that any temporary data file, such as Rstudio environment data files, should also be listed in the `.gitignore` file.

## Naming convention and structure

In order to improve readability of published repos, each repo name should adhere to the following convention (keywords in `{}` are placeholders and should be replaced by the proper information):
- repo for paper/blog analyses -> `pub_{title}_{year}_{author}`;
- repo for other type of analyses -> `analysis_{subject}_{author}`;
- repo for cleaning or derived variables -> `data_{variable-name(s)}_{author}`, `variable-name(s)` can also designed a block of variables;
- repo for data pipeline and generic processing tools -> `processing_{subject}_{author}`;
- other type of repo -> `other_{subject}_{author}`.

Repo names should be kept as concise as possible. All repos should contain a ReadMe.md file that briefly describe the repo objectives, content and any pertinent information to help readers understand how to use the repo.

## Documenting derived variables

Derived variables need an extra care to be sure that any change in the underlaying variables or conversely changes to the derived variable are correctely reflected in any dependent variables. Whatever the language chosen to compute the derived variable (R, Python, SQL, etc.) the code needs to be complete and all steps documented in the repo. This can be either through a batch file, script, or explicitly stated in the mandatory ReadMe.md file.

The computation of new variables is a 5-step process that need to be clearly documented in the scripts:
1. data loading (**input data must be stored outside of the repo**)
1. data cleaning and transformation (all required input variables need to be documented in the ReadMe.md)
1. new variable computation
1. data export (**output data must not be stored in the repo**; the exported dataset needs to contain at least the `participant_id`, as well as `survey_id` if specific to one or several surveys and/or any other pertinent level of aggregation)
1. summary statistic computation (summary stats will be added to the ReadMe.md)

The ReadMe.md file needs to contain the following information:
1. Author / date / version
1. Proposed name of new variable(s); these names should not collide with existing ones
1. Brief description of the new variable(s) as well as any other useful information (hyptheses, motivation, methods used, imputation made, etc.)
1. Exhaustive list of required input variables, including 
1. Summary statistics of the new variable(s), computed for all participants except those for which input variables are missing
1. All required information to run the scripts and reproduce the new dataset, including package or library versions.

The new variables should be computed at the participant and, possibly, the survey level. Once reviewed by the data manager, the new variables will be added to the core dataset and listed in the data dictionary; all COHESION researchers will have access to them. It is good practice to use published derived variables of broader use (_e.g._ age, weight, SF-12 scores, etc.) instead of computing new ones, this will improve the coherence of publications and analyses across researchers.

## Ressources

### COHESION related info

- Data dictionary
- Tableau dashboard
- Observable dashboard

### Github

- Introduction to [Github](https://www.atlassian.com/git)
- [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

### R, Rstudio

- [Tidyverse](https://www.tidyverse.org/)
- Using [spatial data](https://geocompr.robinlovelace.net/index.html) in R

### Compute Canada

- [CC Wiki](https://docs.computecanada.ca/wiki/Compute_Canada_Documentation)

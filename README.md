Template to work with R projects using Git and renv.
==============================

## A short description of the project.

## How to start
To start, we need to do some steps:
1. Execute the R project to start working in the relative directory
2. Install all required libraries using renv::restore().
		*Note: this does not ensure OS or external packages compatiblity!
.Optional: Install git precommit hooks (en caso de trabajar con Visual Code u otra IDE con plugins para Git):
  - `pre-commit install`
  
## Work with renv
renv package have some useful functions to track changes in library requierments and keep it updated.
1. First time a project is created, the function renv::activate() creates the enviroment in the project root to keep a specific subfolder for libraries
2. The renv.lock in the root folder keep tracks of the needed libraries.
2. Any time a library or package is installed you can update this file using renv::snapshot(). This function checks for 
	package names wrapped in requiere() or library() functions. It won't work with <package>::<function> lines!
4. In case there is some problems when installing a package, refer to: https://community.rstudio.com/t/cant-install-packages-with-renv/96696/8
	In many cases, utils::install.packages() works.

## How to commit
To clone the repository:
- `git clone <url-project>

To create a new branch:
- `git checkout -b <branch_name>`

To download the latest changes at the repo:
- `git pull`
- It's important to do this every time before start to code to avoid code incompatibility issues.

To make your changes available to everyone, you must commit your changes:
- `git add .`
- `git commit -m "A short description of your changes"`
- There is a pre-commit hook that review your changes before the commit. If it fails, you must repeat the two steps until all hooks are passed.
- It is recommended to commit every time you add/complete a new feature or function
- Finally, to upload to github: `git push`

## Useful things for jupyter notebooks
Executing the following lines in a jupyter cell, we can update our imported scripts and jupyter will reimport the script
automatically:
```
%load_ext autoreload
%autoreload 2
```

## Useful things for R notebooks

Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Makefile with commands like `make data` or `make train`
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump. 
	│							*Important to not share private or sensible data.
	│							*Recommended to have a backup data stored in local or cloud service!
    │
    ├── docs               <- A default Sphinx project; see sphinx-doc.org for details
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Folder with final running scripts. Can be raw scripts, Jupyter or R notebooks. 
	│ 						   Naming convention is a number (for ordering), the creator's initials, and a short `-` delimited description,
    │                          e.g. `1.0-jqp-initial-data-exploration`.
    │
    ├── documentation      <- Data dictionaries, manuals, references and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   ├── figures        <- Generated graphics and figures to be used in reporting
	│	└── tabular		   <- Tabular outputs from scripts and analysis (.txt, .csv ... )
    │
	├── renv			   <- local enviroment from renv package folder with local R library
	│
    ├── renv.lock          <- The requirements file for reproducing the local environment, from renv package
    ├── R.project          <- R project root
	│
	├── src                <- Source code (custom functions) for use in this project.
    │   │
    │   ├── data           <- Scripts to download or generate data
    │   │   └── 
	│	│	
    │   ├── processing     <- Scripts to process and transform data
	│	│	└── 
    │   │
    │   └── analysis  <- Scripts to create exploratory analysis and visualizations
    │       └── 
    │
	│
	├── renv 			   <- R environment with private libraries that do not clashes with central R managment
    └── tox.ini            <- tox file with settings for running tox; see tox.readthedocs.io


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>

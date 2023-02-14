Template to work with R projects using Git and renv.
==============================

## A short description of the project.

## How to connect Rstudio with Github
Check https://rfortherestofus.com/2021/02/how-to-use-git-github-with-r/
1. Install the packages 'usethis' and 'gitcreds' which provide some helpulf functions.
2. Check if Git is installed. Write in the R terminal: $which git
3. Create Github personal token. Use 'usethis::create_github_token()'
4. Copy the personal token from the Github pop-up
5. Call 'gitcreds::gitcreds_set()'. Follow the instructions.


To pull a Github repository (recommended)
I. Create a project -> Version control.
II. Paste the repository link.
  
To upload a local repository: 
I. Create project with Git or call 'usethis:: use_git()' to create the required files.
II. Create Github repo with 'usethis::use_github()'

## How to start
To start, we need to do some steps:
1. Execute the R project to start working in the relative directory
2. Install all required libraries using renv::restore().
		*Note: this does not ensure OS or external packages compatiblity!
Optional: Install git precommit hooks (en caso de trabajar con Visual Code u otra IDE con plugins para Git):
  - `pre-commit install`
  
## Work with renv
renv package have some useful functions to track changes in library requierments and keep it updated.
1. First time a project is created, the function renv::activate() creates the enviroment in the project root to keep a specific subfolder for libraries
2. The renv.lock in the root folder keep tracks of the needed libraries.
3. Any time a library or package is installed you can update this file using renv::snapshot(). This function checks for 
	package names wrapped in requiere() or library() functions. It won't work with <package>::<function> lines!
4. In case there is some problems when installing a package, refer to: https://community.rstudio.com/t/cant-install-packages-with-renv/96696/8
	In many cases, utils::install.packages() works.
5. Everytime the project need to be executed in a different machine, the packages can be recovered  fron renv.lock using renv::restore()

## How to commit from console
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

## Useful things for R notebooks

Project Organization
------------

    ├── LICENSE
    ├── README.md          <- The top-level README for developers using this project.
    ├── data
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump. 
    │                         *Important to not share private or sensible data. By default data commit is excluded in .gitignore.txt.
    │                         *Recommended to have a backup data stored in local or cloud service!
    │
    ├── docs               <- Here you can store any documentation that you’ve written about your analysis. 
    │                         It can also be used as root directory for GitHub Pages to create a project website.
    │
    ├── lib                <- Folder for any files that provide useful functionality for your work, but do not constitute a statistical analysis per se. 
    │                         Specifically, you should use the lib/helpers.R script to organize any small functions.
    │                         Big blocks of functions for a specific topic could belong to a proper package or be stored in a .R script.
    │
    ├── notebooks          <- Folder with final running scripts. Can be raw scripts, Jupyter or R notebooks. 
    │                         Naming convention is a number (for ordering), the creator's initials, and a short `-` delimited description,
    │                         e.g. `1.0-jqp-initial-data-exploration`.
    │
    ├── documentation      <- Data dictionaries, manuals, references and all other explanatory materials.
    │
    ├── profiling          <- Here you can store any scripts you use to benchmark and time your code.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   ├── articles       <- In case articles or papers are submitted, the following subfolders can be used to keep track of changes: 
    │   │                     a. Sent, b. Reviews and c. Proof (final print version submitted to journal).
    │   ├── figures        <- Generated graphics and figures to be used in reporting.
    │   └── tabular        <- Tabular outputs from scripts and analysis (.txt, .csv ... ) ready to be presented as supplemental info.
    │
    ├── renv               <- R environment with private libraries that do not clashes with central R managment. Useful to keep frozen-version R packages.
    │
    ├── renv.lock          <- The requirements file for reproducing the local environment, from renv package.
    │
    ├── R.project          <- R project root.
    │
    ├── src                <- Source code (custom functions) for use in this project.
    │   ├── data           <- Scripts to download or generate data.
    │   │   └── 
    │   ├── diagnostics    <- Here you can store any scripts you use to diagnose your data sets for corruption or problematic data points.
    │   │   └──	
    │   ├── processing     <- Scripts to process and transform data.
    │   │   └──
    │   └── analysis       <- Scripts to create exploratory analysis and visualizations.
    │       └── 
    │
    └── tests              <- Here you can store any test cases for the functions you’ve written. Your test files should use testthat style tests.
    

--------

<p><small>Project based on an adaptation of the Python verison <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience and  <a target="_blank" href="http://projecttemplate.net/architecture.html"> Rproject Template </a> </small></p>

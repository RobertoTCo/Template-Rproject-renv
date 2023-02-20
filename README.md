Template to work with R projects using Git and renv.
==============================

## A short description of the project.

## Install Git in your local machine
- Go to: <a target="_blank" href="https://git-scm.com/download/"> Git download section </a>
- Install the version suits better for your OS and requirements.

## How to connect Rstudio with Github
Check <a target="_blank" href="https://rfortherestofus.com/2021/02/how-to-use-git-github-with-r/"> How to use git github with r blog </a>

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
   *Note: this template does not have docker support.
  
## Work with renv
renv package have some useful functions to track changes in library requierments and keep it updated.
1. First time a project is created, the function `renv::activate()` creates the enviroment in the project root to keep a specific subfolder for libraries
2. The renv.lock in the root folder keep tracks of the needed libraries.
3. Any time a library or package is installed you can update this file using renv::snapshot(). This function checks for 
	package names wrapped in requiere() or library() functions. It won't work with `<package>::<function>` lines!
4. In case there is some problems when installing a package, refer to: <a target="_blank" href="https://community.rstudio.com/t/cant-install-packages-with-renv/96696/8"> This issue in the Rstudio community </a>. In many cases, utils::install.packages() works.
5. Everytime the project need to be executed in a different machine, the packages can be recovered  fron renv.lock using `renv::restore()`.

## How to commit from console
To clone the repository:
- `git clone <url-project>`

To create a new branch:
- `git checkout -b <branch_name>`

To download the latest changes at the repo:
- `git pull`
- It's important to do this every time before start to code to avoid code incompatibility issues.

To make your changes available to everyone, you must commit your changes:
- `git add .`
- `git commit -m "A short description of your changes"`
- It is recommended to commit every time you add/complete a new feature or function
- Finally, to upload to github: `git push`

When working with some colleges, always keep a branch with stable code, usually named 'main' or 'master' branch and perform changes with parallel branchs named with their purpose.
- When the parallel branch is finished and stable, the code can be merged into the main one with `git request-pull`
- It is advisable to appoint one or two coordinators of the Git repo to review every pull request to the main branch.

## Commit easier with IDEs
Organizing a repo and the commits, push and pull is usually integrated in the most common IDEs.
- If you are using Rstudio and you followed the above steps to connect to Github, there should be a tab to control commits and the history.
- VSCode has some useful extensions to work with repositories and keep track of the changes, like  <a target="_blank" href="https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens"> Gitlens extension </a>.

## Useful things for R notebooks

Project Organization
------------

    ├── LICENSE
    ├── README.md          <- The top-level README for developers using the project.
    ├── .gitignnore        <- File to exclude folders and files to commits into the Git respository
    ├── data
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump. 
    │                         *Important to not share private or sensible data. By default data commit is excluded in .gitignore.txt.
    │                         *Recommended to have a backup data stored in local or cloud service!
    │
    ├── docs               <- Any documentation about your analysis: Data dictionaries, manuals, references and all other explanatory materials.
    │                         It can also be used as root directory for GitHub Pages to create a project website.
    │
    ├── lib                <- Folder for any files that provide useful functionality for your work, but do not constitute a statistical analysis per se. 
    │                         Specifically, you should use the lib/helpers.R script or utils.R for more pythonic approach to organize any small functions.
    │                         Big blocks of functions for a specific topic could belong to a proper package or be stored in a .R script.
    │
    ├── notebooks          <- Folder with final running scripts. Can be raw scripts, Jupyter or R notebooks. 
    │                         Naming convention is a number (for ordering), the creator's initials, and a short `-` delimited description,
    │                         e.g. `1.0-jqp-initial-data-exploration`.
    │
    ├── profiling          <- Here you can store any scripts you use to benchmark and time your code.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   ├── articles       <- In case articles or papers are submitted, the following subfolders can be used to keep track of changes: 
    │   │                     a. Sent, b. Reviews and c. Proof (final print version submitted to journal).
    │   ├── figures        <- Generated graphics and figures to be used in reporting.
    │   └── tabular        <- Tabular outputs from scripts and analysis (.txt, .csv ... ) ready to be presented as supplemental info.
    │
    ├── renv               <- R environment with private libraries that do not clash with central R managment. Useful to keep frozen-version R packages.
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

<p><small>Project based on a simpler <a target="_blank" href="https://cran.r-project.org/web/packages/renv/index.html">renv</a> adaptation of the Python version <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a> &  <a target="_blank" href="http://projecttemplate.net/architecture.html"> Rproject Template </a> </small></p>

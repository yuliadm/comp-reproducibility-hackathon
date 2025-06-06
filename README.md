# comp-reproducibility-hackathon


## Setting description
* Trying to run the code and reproduce the code from https://github.com/GeertvanGeest/V-pipe/blob/master/docs/tutorial_sarscov2.md
* env 'comprepr' created, running in main branch: (comprepr) @yuliadm ➜ /workspaces/comp-reproducibility-hackathon (main)  
* **System specs:** Windows10, Visual Studio Code (recent), Github Codespaces, mobile internet connection


1. `V-pipe`, `bioconda` and snakemake installation.
a. installed `pip` just in case
b. installation using the `quick_install.sh` script
- the script gets installed
- `bash quick_install.sh -p vp-analysis -w work` raises Warning and an Error:

```bash
Oops:You have conda or modules automatically loaded in your profile. This is can lead to potential conflicts and errors.
consider always loading such environment modifiers either manually or at the beginning of your jobs, never in your profile.
======================
installing Mambaforge
======================

Using installer:        Mambaforge-Linux-x86_64.sh


Reusing existing connection to github.com:443.
HTTP request sent, awaiting response... 404 Not Found
2025-06-06 09:52:55 ERROR 404: Not Found.

sh: 0: Can't open Mambaforge-Linux-x86_64.sh
quick_install.sh: line 170: mambaforge/bin/activate: No such file or directory
Warning: 'defaults' already in 'channels' list, moving to the top
Warning: 'bioconda' already in 'channels' list, moving to the top
Warning: 'conda-forge' already in 'channels' list, moving to the top
quick_install.sh: line 181: mamba: command not found
Oops:I cannot install snakemake in base environment. Conflicts ?
quick_install.sh: line 188: mamba: command not found
Argh: I cannot install snakemake in environment V-pipe.
```

Trying to fix mambaforge absence by running

```bash
conda activate comprepr && conda install -c conda-forge mamba -y
```
✔️installed

Re-run `quick_install.sh`


Errors:
```bash
warning  libmamba The specification of the environment does not seem solvable in your current setup.
warning  libmamba For instance, packages from different channels might be specified,
warning  libmamba whilst your current configuration might not allow their resolution.
warning  libmamba 
warning  libmamba If it is the case, you need to either:
warning  libmamba  - adapt the channel ordering (e.g. by reordering the `-c` flags in your command line)
warning  libmamba  - use the flexible channel priority (e.g. using `--channel-priority flexible` in your command line)
warning  libmamba 
warning  libmamba For reference, see this piece of documentation on channel priority:
warning  libmamba https://docs.conda.io/projects/conda/en/stable/user-guide/tasks/manage-channels.html#strict-channel-priority
error    libmamba Could not solve for environment specs
    The following packages are incompatible
    ├─ pin on python =3.13 * is installable and it requires
    │  └─ python =3.13 *, which can be installed;
    └─ snakemake-minimal <8 * is not installable because there are no viable options
       ├─ snakemake-minimal [5.2.1|5.2.2|5.2.4|5.3.0] would require
       │  └─ python >=3.5,<3.6.0a0 *, which conflicts with any installable versions previously reported;
       ├─ snakemake-minimal [5.2.1|5.2.2|5.2.4|5.3.0] would require
       │  └─ python >=3.6,<3.7.0a0 *, which conflicts with any installable versions previously reported;
       ├─ snakemake-minimal [5.10.0|5.11.0|...|7.9.0] would require
       │  └─ ratelimiter =* * but there are no viable options
       │     ├─ ratelimiter 1.2.0 would require
       │     │  └─ python [=2.7 *|>=2.7,<2.8.0a0 *], which conflicts with any installable versions previously reported;
       │     ├─ ratelimiter 1.2.0 would require
       │     │  └─ python [=3.5 *|>=3.5,<3.6.0a0 *], which conflicts with any installable versions previously reported;
       │     ├─ ratelimiter 1.2.0 would require
       │     │  └─ python =3.6 *, which conflicts with any installable versions previously reported;
       │     ├─ ratelimiter 1.2.0 would require
       │     │  └─ python >=3.6,<3.7.0a0 *, which conflicts with any installable versions previously reported;
       │     ├─ ratelimiter 1.2.0 would require
       │     │  └─ python >=3.7,<3.8.0a0 *, which conflicts with any installable versions previously reported;
       │     ├─ ratelimiter 1.2.0 would require
       │     │  └─ python >=3.8,<3.9.0a0 *, which conflicts with any installable versions previously reported;
       │     └─ ratelimiter 1.2.0 would require
       │        └─ python >=3,<3.11 *, which conflicts with any installable versions previously reported;
       ├─ snakemake-minimal [7.18.2|7.19.0|...|7.32.4] would require
       │  └─ pulp >=2.0,<2.8.0 * but there are no viable options
       │     ├─ pulp [2.5.1|2.6.0|2.7.0] would require
       │     │  └─ python >=3.10,<3.11.0a0 *, which conflicts with any installable versions previously reported;
       │     ├─ pulp [2.6.0|2.7.0] would require
       │     │  └─ python >=3.11,<3.12.0a0 *, which conflicts with any installable versions previously reported;
       │     ├─ pulp 2.7.0 would require
       │     │  └─ python >=3.12.0rc3,<3.13.0a0 *, which conflicts with any installable versions previously reported;
       │     ├─ pulp [2.3|2.3.1|...|2.7.0] would require
       │     │  └─ python >=3.8,<3.9.0a0 *, which conflicts with any installable versions previously reported;
       │     ├─ pulp [2.3|2.3.1|...|2.7.0] would require
       │     │  └─ python >=3.9,<3.10.0a0 *, which conflicts with any installable versions previously reported;
       │     ├─ pulp [2.3|2.3.1|2.4|2.5.0|2.5.1] would require
       │     │  └─ python >=3.6,<3.7.0a0 *, which conflicts with any installable versions previously reported;
       │     └─ pulp [2.3|2.3.1|...|2.6.0] would require
       │        └─ python >=3.7,<3.8.0a0 *, which conflicts with any installable versions previously reported;
       └─ snakemake-minimal 7.32.4 would require
          └─ python >=3.7,<3.12 *, which conflicts with any installable versions previously reported.
critical libmamba Could not solve for environment specs

```

this was somehow overridden...


```bash

======================
configuring init_project
======================

Conda path:     /workspaces/comp-reproducibility-hackathon/vp-analysis/mambaforge
Conda environment:      V-pipe


======================
Working directory
======================

Working directory:      work
/workspaces/comp-reproducibility-hackathon/vp-analysis/V-pipe/init_project.conf: line 5: V-pipevp_conda_env=V-pipe: command not found
Warning: cannot detect conda environment
V-pipe project initialized!

Create and populate 'samples' directory and/or adjust config.yaml.
Then, use ./vpipe to run V-pipe.


Installation of V-pipe completed

```

The structure of the project (pipeline) that I am getting right after the installation is different from that reported in the tutorial https://github.com/GeertvanGeest/V-pipe/blob/master/docs/tutorial_0_install.md (maybe to the installation issues at the previous steps):

📁 [HOME]
└───📁vp-analysis
    ├───📁V-pipe      # V-pipe checked out from Github
    ├───📁Miniforge3  # bioconda + conda-forge + mamba + Snakemake
    ├───📁work        # work directories
    ├───📁work-tests  #  …
    └───📁 …          #  …


2. Checking installation by running

```bash
cd vp-analysis/work
# copy the example data from the repository to your working directory
cp -r ../V-pipe/docs/example_HIV_data/* .
# check what will be run with a dry run
./vpipe -n
# run vpipe on a small HIV test dataset
# this will install all dependencies and run the pipeline
./vpipe 
```


Getting an error:
```bash
(comprepr) @yuliadm ➜ /workspaces/comp-reproducibility-hackathon/vp-analysis/work (main) $ ./vpipe -n
./vpipe: line 3: exec: snakemake: not found
```

Trying to fix by running:

```bash
conda activate comprepr && mamba install -c bioconda -c conda-forge snakemake -y
```
Encountering errors:
```bash
warning  libmamba https://docs.conda.io/projects/conda/en/stable/user-guide/tasks/manage-channels.html#strict-channel-priority
error    libmamba Could not solve for environment specs
    The following packages are incompatible
    ├─ pin on python =3.13 * is installable and it requires
    │  └─ python =3.13 *, which can be installed;
    └─ snakemake =* * is not installable because there are no viable options
       ├─ snakemake [3.10.0|3.10.1|...|3.9.1] would require
       │  └─ python =3.4 *, which conflicts with any installable versions previously reported;
       ├─ snakemake [3.10.0|3.10.1|...|4.0.0] would require
       │  └─ python =3.5 *, which conflicts with any installable versions previously reported;
       ├─ snakemake [3.11.2|3.12.0|...|4.0.0] would require
       │  └─ python =3.6 *, which conflicts with any installable versions previously reported;
       ├─ snakemake [4.0.0|4.1.0|...|8.0.0] would require
       │  └─ dropbox >=7.2.1 *, which conflicts with any installable versions previously reported;
       ├─ snakemake [8.0.1|8.1.0|...|8.9.0] would require
       │  └─ snakemake-minimal [=8.0.1 *|=8.1.0 *|...|=8.9.0 *], which requires
       │     └─ toposort [>=1.10 *|>=1.10,<2.0 *], which conflicts with any installable versions previously reported;
       ├─ snakemake 8.11.2 would require
       │  └─ snakemake-minimal =8.11.2 *, which does not exist (perhaps a missing channel);
       ├─ snakemake 8.23.0 would require
       │  └─ snakemake-minimal =8.23.0 * but there are no viable options
       │     ├─ snakemake-minimal [8.23.0|8.23.1|...|9.5.1] would require
       │     │  └─ python >=3.11,<3.13 *, which conflicts with any installable versions previously reported;
       │     └─ snakemake-minimal [8.0.1|8.1.0|...|8.9.0], which cannot be installed (as previously explained);
       └─ snakemake [8.23.1|8.23.2|...|9.5.1] would require
          └─ snakemake-minimal [=8.23.1 *|=8.23.2 *|...|=9.5.1 *], which cannot be installed (as previously explained).
critical libmamba Could not solve for environment specs
```


After downgrading the python version and the snakemake, 

```bash
mamba install -c bioconda -c conda-forge snakemake=7.32.4 --strict-channel-priority -y
```

still getting an error: 

```bash
error    libmamba Could not solve for environment specs
    The following package could not be installed
    └─ snakemake =7.32.4 * is not installable because it requires
       └─ dropbox >=7.2.1 *, which conflicts with any installable versions previously reported.
critical libmamba Could not solve for environment specs
```


Explicitly install dropbox.

```bash
mamba install -c conda-forge dropbox=11.36.2 -y
mamba install -c bioconda -c conda-forge snakemake=7.32.4 --strict-channel-priority -y
```

Getting tons of incompatibility messages.

2. Try installing snakemake-minimal
```bash
mamba install -c bioconda -c conda-forge snakemake-minimal=7.32.4 --strict-channel-priority -y
```

Alternative: try installing snakemake==7.32.4
```bash
pip install snakemake==7.32.4
```
Issues:

```bash
  DEPRECATION: Building 'connection_pool' using the legacy setup.py bdist_wheel mechanism, which will be removed in a future version. pip 25.3 will enforce this behaviour change. A possible replacement is to use the standardized build interface by setting the `--use-pep517` option, (possibly combined with `--no-build-isolation`), or adding a `pyproject.toml` file to the source tree of 'connection_pool'. Discussion can be found at https://github.com/pypa/pip/issues/6334

DEPRECATION: Building 'stopit' using the legacy setup.py bdist_wheel mechanism, which will be removed in a future version. pip 25.3 will enforce this behaviour change. A possible replacement is to use the standardized build interface by setting the `--use-pep517` option, (possibly combined with `--no-build-isolation`), or adding a `pyproject.toml` file to the source tree of 'stopit'. Discussion can be found at https://github.com/pypa/pip/issues/6334  
```


Snakemake is now being found and executed, but hitting a new error:
```bash
AttributeError: module 'pulp' has no attribute 'list_solvers'. Did you mean: 'listSolvers'?
```

**Fix:** downgrade pulp to a version compatible with snakemake 7.32.4. The recommended version is `pulp==2.6.0`: pip install pulp==2.6.0

The dry run seems to be working after some tinkering. 
Trying the small HIV sample by running `bash ./vpipe`.

Results in 
```bash
Error: you need to specify the maximum number of CPU cores to be used at the same time. If you want to use N cores, say --cores N or -cN. For all cores on your system (be sure that this is appropriate) use --cores all. For no parallelization use --cores 1 or -c1. <_io.TextIOWrapper name='<stderr>' mode='w' encoding='utf-8'>
```


This error means that Snakemake (via mamba) is trying to create a new conda environment at a location where a non-conda folder already exists. This is a common issue when a previous run failed or left behind a corrupted or incomplete environment folder.

**Possible fix:**
1. Delete the problematic folder (/workspaces/comp-reproducibility-hackathon/vp-analysis/work/.snakemake/conda/99a95ea7e61fb60b56576f80acbc6acc_) so mamba/conda can recreate it cleanly.
2. Re-run your pipeline command `snakemake -s ../V-pipe/workflow/Snakefile --use-conda --cores 4`

Still getting an error:

```bash
CreateCondaEnvironmentException:
Could not create conda environment from /workspaces/comp-reproducibility-hackathon/vp-analysis/V-pipe/workflow/envs/sam2bam.yaml:
Command:
mamba env create --quiet --file "/workspaces/comp-reproducibility-hackathon/vp-analysis/work/.snakemake/conda/84129a1fac493295f4712a3a8cfdc747_.yaml" --prefix "/workspaces/comp-reproducibility-hackathon/vp-analysis/work/.snakemake/conda/84129a1fac493295f4712a3a8cfdc747_"
Output:
error    libmamba Non-conda folder exists at prefix - aborting.
critical libmamba Non-conda folder exists at prefix - aborting.
```

Didn't manage to solve the above after several iterations.

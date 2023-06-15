+++
author = "Andrew Smith"
title = "What the f*** is conda"
date = "2022-05-12"
description = "Tutorial for using conda"
tags = [
    "tutorial",
]
+++
1. Install conda.

    Install [miniconda](https://docs.conda.io/en/latest/miniconda.html). Pick Linux > [Miniconda3 Linux 64-bit](https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh) unless you are a little baby. Say yes to conda init.
    
2. Fix default things that conda does
   1. Close your terminal and open another, or source ~.bashrc or wherever you have bashrc.
   2. Prevent conda from activating base environment by default
        ```
        conda config --set auto_activate_base false
        ```
   3. Checkout base packages
        ```
        conda list
        ``` 
        If you had installed anaconda, you'd have 6 million base packages. For some reason, conda geniuses install conda inside the base environment, so we can't actually delete it.
    4. Checkout environments
        ```
        conda env list
        ```
        Oh, it's only the base environment. Let's make a new one.
3. Create your first *environment*

    ```
    conda create -n environment_name_here
    ```

    Make sure you created your environment.

    ```
    conda env list
    ```
    An environment is a place where you install packages, use them, and get out. If you install a package inside an environment, you cannot use it outside of the environment (provided you have not also installed it outside of the environment globally with pip or something).

    In order to use an environment, or get inside of it, you can activate it.

4. Activate your first environment

    ```
    conda activate environment_name_here
    ```
    Now you will see your environment name on your terminal prompt. Check out the packages installed in your environment.
    ```
    conda list
    ```
    Should be empty.

5. Install your first package

    ```
    conda install numpy
    ```

    conda might ask to install dependencies. Say yes.

    List packages. See numpy.

    Test it out by importing numpy in python (an interactive prompt, a script, or a noteboook).

6. Deactivate environment

    ```
    conda deactivate
    ```

    Now, if you did not have numpy installed globally, you can check your base packages and see that numpy is not installed. This is essentially the beauty of conda.

7. Share my conda environment with a friend (or just save it to use on another machine if you are lonely)

    ```
    conda env export -n environment_name_here -f filename.yml
    ```

8. Create conda environment from yml file

    Let's test on your machine. Let's delete your environment, then reinstall from the file you just exported.

    Remove conda environment

    ```
    conda env remove -n environment_name_here
    ```

    Create conda environment from yml file

    ```
    conda env create -n env_name -f filename.yml
    ```

    Make sure it's there

    ```
    conda list
    ```

Seems like that's about it.
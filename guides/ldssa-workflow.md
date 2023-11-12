# LDSSA Learning Units

## 1. Structure of the batch7-students repository
The repository has a directory for each specialization S01 - S06. Inside are the directories for the learning units. See the example below:

```
|--S01
   |-- requirements.txt
   |-- SLU01 - Pandas 101
       |-- media
           |-- some-image.csv
       |-- data
           |-- some-dataset.csv        
       |-- Examples notebook.ipynb
       |-- Exercise notebook.ipynb
       |-- Learning notebook.ipynb
       |-- README.md    
   |-- SLU02 - Subsetting Data in Pandas
       ...    
   |-- SLU03 - Visualization with Pandas and Matplotlib   
       ...           
```

The learning unit directory naming follows the convention

```markdown
<specialization ID> - <specialization name>/<learning unit ID> - <learning unit name>
```

The LU directory contains the `README` (a markdown file with the description of the unit), the `Learning notebook`, the `Exercise notebook`, and the `Examples notebook`. It may also contain a `media` directory with all the visual material, the `data` directory with the datasets, and a `utils.py` file with helper code.

The notebooks are all Jupyter notebooks, the same as you worked with during the admissions process. They contain text, interactive code, and tests for your solutions in the exercises.

The `requirements.txt` file in each specialization directory contains the packages to be installed in the virtual environment. 

Please keep this directory structure also in your workspace repository because the grader in the portal depends on it.

## 2. Working on a Learning Unit

### 2.1 Create a virtual environment for the current specialization
You will need a new virtual environment for every specialization. You have already created one for S01 during the previous setup steps. Here we will repeat some of those steps so that you have a complete guide for when you start each specialization.
 
1. Open the terminal and create the virtual environment for the specialization:

```bash
python3.10 -m venv ~/.virtualenvs/s01
```
1. Activate the virtual environment of the specialization:

```bash
source ~/.virtualenvs/s01/bin/activate
```

1. Enter the directory of the specialization and install the requirements:

```bash
cd ~/projects/batch7-workspace/"S01 - Bootcamp and Binary Classification"
pip install -r requirements.txt
```

You will see a lot of output on the terminal while pip installs the packages. You can also notice possible errors.

### 2.2 Launching the Jupyter notebook

1. Enter the learning unit directory in your workspace directory (`batch7-workspace`).
    >Note: It is **VERY IMPORTANT** that you **ALWAYS** work on the files on your `batch7-workspace` repository, and **NEVER** change the files in the `batch7-students` local repository! If you do change these files, you can have a merge conflict when you next pull from the GitHub repository.

```bash
cd ~/projects/batch7-workspace/"S01 - Bootcamp and Binary Classification"/"SLU01 - Pandas 101"
```

1. Run the jupyter notebook:

    ```bash
    jupyter notebook
    ```
If the previous command does not work, use this one:

```bash
jupyter notebook --NotebookApp.use_redirect_file=False
```

You should see something similar to this in your terminal:
![Open exercise notebook](assets/jupyter_terminal.png "Open exercise notebook")
Your browser should pop up with Jupyter open, however, if this does not happen, you can simply copy the link you see on your terminal (the one that contains `localhost`) and paste it in your browser's address bar:

![Open exercise notebook](assets/jupyter_terminal_link.png "Open exercise notebook")

>Note: If you see these scarry looking error messages, don't worry, you can just ignore them.

![Open exercise notebook](assets/jupyter_error_red.png "Open exercise notebook")

You will also see a message about the update of the jupyter notebook, you can ignore it.

### The Exercise Notebook

Make sure you open and go through the Learning Notebook first.

Every learning unit contains an exercise notebook with exercises you will
work on.
So let's have a look at the sample Learning Unit.

1. On the Jupyter Notebook UI in the browser open the exercise notebook
![Open exercise notebook](assets/jupyter_exercise_notebook.png "Open exercise notebook")
1. Follow the instructions provided in the notebook

Besides the exercises and the cells for you to write solutions you will see
other cells with a series of `assert` statements.
This is how we (and you) will determine if a solution is correct.
If all `assert` statements pass, meaning you dont get an `AssertionError` or
any othe r kind of exception, the solution is correct.

Once you've solved all of the notebook we recommend the following this simple
checklist to avoid unexpected surprises.

1. Save the notebook (again)
1. Run "Restart & Run All"
![Restart & Run All](assets/jupyter_clear_and_run.png "Restart & Run All")
1. At this point the notebook should have run without any failing assertions

If you want to submit your notebook before it is all the way done to
check intermediate progress, feel free to.

If you are able to go through the entire process and get a passing grade on
the sample LU you'll have a good understanding of the same flow that you'll use
for all LUs throughout the academy.

#### Commit and Push

Now you have worked on the sample learning unit and you have some uncommitted
changes.
It's time to commit the changes, which just means adding them to your `batch6-workspace`
repository history, and pushing this history to you remote on _GitHub_.

* Using the terminal commit and push the changes

```bash
git add .
git commit -m 'Testing the sample notebook'
git push
```

#### Grading

1. Go to the [_Portal_](https://portal.lisbondatascience.org) and select the learning unit
![Learning unit](assets/portal_sample_lu.png "Learning unit")
1. Select "Grade"
![Grade](assets/portal_grade.png "Grade")
1. After grading is complete you should have 20/20
1. If everything passes locally but the grader doesn't give you the excepted
output head to out [troubleshooting](https://github.com/LDSSA/LDSA-setup/blob/main/troubleshooting.md)

## 2. Learning Unit Workflow

You will need to follow this workflow whenever new learning materials are released.

Learning units will be announced in the academy's _#announcements_ channel.
At this point they are available in the
[batch6-students](https://github.com/LDSSA/batch6-students)
repository.
A new Learning Unit is released every Monday.

The steps you followed during the initial setup are exactly what you are going
to be doing for each new Learning Unit.
Here's a quick recap:

0. If you haven't, activate your virtual environment
    ```bash
    source ~/.virtualenvs/slu00/bin/activate
    ```

1. Once a new Learning Unit is available, pull the changes from the [batch6-students](https://github.com/LDSSA/batch6-students) repo:
    * enter the `~/projects/batch6-students/` using the `cd` command, then use the `git pull` command:

    ```bash
    cd ~/projects/batch6-students/
    git pull
    ```

1. Copy the Learning Unit to your `batch6-workspace` repo

    ```bash
    cp -r ~/projects/batch6-students/"<specialization ID> - <specialization name>"/"<learning unit ID> - <learnin unit name>" ~/projects/batch6-workspace/"<specialization ID> - <specialization name>"
    ```

    For example, for the `S01 - Bootcamp and Binary Classification` and `SLU01 - Pandas 101`, it would look like this:

    ```bash
    cp -r ~/projects/batch6-students/"S01 - Bootcamp and Binary Classification"/"SLU01 - Pandas 101" ~/projects/batch6-workspace/"S01 - Bootcamp and Binary Classification"
    ```

1. Create a new virtual environment for the Learning Unit you'll be working on.

    * To do this you will run the following command:

    ```bash
    python3.8 -m venv ~/.virtualenvs/<learning unit ID>
    ```

    * and you would replace the `<learning unit ID>` with the learning unit ID, such that for SLU01, for example, the command would be:

    ```bash
    python3.8 -m venv ~/.virtualenvs/slu01
    ```

1. Activate your virtual environment

    ```bash
    source ~/.virtualenvs/slu01/bin/activate
    ```

1. Install the python packages from requirements.txt for the specific Learning Unit (you must do this for each Learning Unit, and there are multiple Learning Units in a Specialization)

    ```bash
    pip install -r ~/projects/batch6-workspace/"<specialization ID> - <specialization name>"/"<learning unit ID> - <learnin unit name>"/requirements.txt
    ```

    For example, for the `S01 - Bootcamp and Binary Classification` and `SLU01 - Pandas 101`, it would look like this:

    ```bash
    pip install -r ~/projects/batch6-workspace/"S01 - Bootcamp and Binary Classification"/requirements.txt
    ```

1. Change to the `batch6-workspace` dir

    ```bash
    cd ~/projects/batch6-workspace
    ```

1. Open Jupyter Notebook

    ```bash
    jupyter notebook
    ```

1. Work
1. Once all tests pass or once you're happy, save your work, close the browser tab with the Jupyter Notebook, close the terminal and open a new terminal
1. Then commit the changes and push

    ```bash
    cd ~/projects/batch6-workspace
    git add .
    git commit -m "Worked on SLU01 exercises"
    git push
    ```

1. Profit

## Updates to Learning Units

As much as we try and have processes in place to prevent errors and bugs in
the learning units some make it through to you.
If the problem is not in the exercise notebook you can just pull the new
version from the students repo and replace the file.
The problem is if the correction is in the exercise notebook, you can't just
replace the file your work is there and you'll lose it!

When a new version of the exercise notebook is released (and announced) two
things will happen.
If you submit an old version of the notebook it will be flagged as out of date
and not graded.
You will have to merge the work you've already done into the new version of the
notebook.

At the moment our suggestion to merge the changes is:

1. Rename the old version
1. Copy the new exercise notebook over
1. Open both and copy paste your solutions to the new notebook

We understand it's not ideal and are working on improving this workflow using
[_nbdime_](https://nbdime.readthedocs.io/).
If you are comfortable installing _Python_ packages you can try it out, but
we offer no support for this at the moment.

### Add your Slack ID to the Portal

In your **Profile** in the **Portal**, besides your *GitHub Handle*, you should add your **SlackID**. You can find information on how to find it [following this link](https://moshfeu.medium.com/how-to-find-my-member-id-in-slack-workspace-d4bba942e38c)



## Help

During the academy you will surely run into problems and have doubts about the
material.
We provide you with some different channels to ask for help.

### Learning Unit

If you feel something is not clear enough or there is a bug in the learning
material please follow [these steps](https://ldssa.github.io/wiki/Starters%20Academy%20(LDSSA)/How-to-ask-for-and-give-help/). Remember, there is no such thing as a dumb question, and by asking questions publicly you will help others!

If you have more conceptual questions about the materials or how to approach a problem you can also
reach out to the instructors on slack.
You can find the main contact for the learning unit in the
[_Portal_](https://portal.lisbondatascience.org/) this instructor can help you
out or redirect you to someone that is available at the moment.

### _Portal_

Are you getting different results locally than what you are getting in the
_Portal_?
If so we will first ask to do a bit of troubleshooting.

1. Ensure that you have saved the changes in the notebook
1. Ensure that you have committed and pushed the changes
1. Ensure that you are not using packages that are not present in the original
`requirements.txt` file (changes to this file or your local environment have no
effect)
1. In the learning unit page in the [_Portal_](https://portal.lisbondatascience.org/)
you are able to download the exercise notebook with the results of the grader
by clicking your grade, have a look to figure out what went wrong.
![Download notebook](assets/portal_download_notebook.png "Download notebook")
If none of these steps helped go ahead and open a support ticket for the portal
[here](https://github.com/LDSSA/batch6-students).

Is the _Portal_ down or acting out in some unexpected way?
Then please open a support ticket for the portal
[here](https://github.com/LDSSA/batch6-students).

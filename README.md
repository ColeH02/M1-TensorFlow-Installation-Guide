# M1-TensorFlow-Installation-Guide
A short guide to getting tensorflow to work with the m1 and m2 macs

Modified guide from Jeff Heaton which can be found [here](https://github.com/jeffheaton/t81_558_deep_learning/blob/master/install/tensorflow-install-mac-metal-jan-2023.ipynb)

## Step 0 OS requirements
Make sure you are updated to MacOS version 12.0+

## Step 1 (Optional) Remove Anaconda
This step is optional but recommended as some problems may stem from initial python install  
While `conda install anaconda-clean` can be run in any conda env, I recommened inputing the following as it will speed this process up greatly and avoid any errors
```
conda create -n cleaner anaconda-clean
conda activate cleaner
anaconda-clean
```

Next, run the following commands to ensure Anaconda is nuked from any existence on your mac
```
rm -rf anaconda3
rm -rf ~/anaconda3
rm -rf ~/opt/anaconda3
```

## Step 2 Installing (Mini)Conda
While you can install anaconda I highly recommend installing miniconda, it'll take up less space and give you more control of what goes into your environment

The download for apple m1 is linked directly [here](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.pkg)
Or choose from the list of downloads [here](https://docs.conda.io/en/latest/miniconda.html)

*NOTE: Please Please Please check that you install Miniconda macOS Apple M1 64-bit pkg*

Now verify that the you installed the correct version by running the following in the terminal
```
python
>>>import platform
>>>platform.platform()
```
The output should be `macOS-xxx-arm64-64bit` where `xxx` is your OS version, if you do NOT see this, refer back to previous steps

## Step 3 Install Xcode 
`xcode-select --install`
If you already have this installed, great!

## Step 4 Install Jupyter and Create Environment
First,
`conda install -y jupyter`

Now, deactivate the base environment
`conda deactivate`

Next, download the yml file [here](https://github.com/ColeH02/M1-TensorFlow-Installation-Guide/blob/main/tensorflow-apple-m1.yml)

This is a yml file I created which contains all the packages that will be used in this course

Make sure this file is saved to `Users/[user]`

Now,
`conda env create -f tensorflow-apple-m1.yml -n csci349`

*Note: csci349 can be changed to whatever you would like to call this new environment*

Finally, activate the new environment
`conda activate csci349`

## Step 5 Register the Environment

`python -m ipykernel install --user --name csci349 --display-name "Python 3.9 (csci349)"`

Then, test the environment with
`jupyter notebook` or `jupyter lab` and make sure to change the kernel in the top right to "Python 3.9 (csci349)"!

If you are using PyCharm make sure to set the interpreter to "Python 3.9 (csci349)" as well 

*Note: if jupyter lab does not recognize `tensorflow` you may need to run the following command to ensure the versions match
`python -m pip install tensorflow-macos==2.9.0 tensorflow-metal==0.6.0 --force-reinstall`

If you want to confirm that you have all the packages installed try the following imports in jupyter lab
```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import plotly
from sklearn.model_selection import cross_val_score
from sklearn.tree import DecisionTreeClassifier
from sklearn.svm import LinearSVC
from sklearn.metrics import accuracy_score
from sklearn.metrics import classification_report
from sklearn.metrics import confusion_matrix
from sklearn.metrics import accuracy_score
from sklearn.model_selection import KFold
from sklearn.model_selection import cross_validate
from sklearn.model_selection import cross_val_predict
from sklearn.neighbors import KNeighborsClassifier
from sklearn.naive_bayes import MultinomialNB
from scipy.stats import zscore
from sklearn.utils import shuffle
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers
from scikeras.wrappers import KerasClassifier
```

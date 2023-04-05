# M1-TensorFlow-Installation-Guide
A short guide to getting tensorflow to work with the m1 and m2 Macs

Modified guide from Jeff Heaton which can be found [here](https://github.com/jeffheaton/t81_558_deep_learning/blob/master/install/tensorflow-install-mac-metal-jan-2023.ipynb)

## Step 0 OS requirements
Make sure you are updated to MacOS version 12.0+

## Step 1 (Optional) Remove Anaconda
This step is optional but recommended as some problems may stem from initial python install  
While `conda install anaconda-clean` can be run in any conda env, I recommend inputing the following commands as it will speed this process up greatly and avoid any errors
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
While you can install anaconda I highly recommend installing miniconda; It'll take up less space and give you more control of what goes into your environment

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
First install juypter,
```
conda install -y jupyter
```

Now, deactivate the base environment
```
conda deactivate
```

Next, download tensorflow-apple-m1.yml [here](https://github.com/ColeH02/M1-TensorFlow-Installation-Guide/blob/main/tensorflow-apple-m1.yml)

This is a yml file I created which contains all the packages that will be used in this course \
Make sure this file is saved to `Users/[user]`

Now create a new environment using the yml file,
```
conda env create -f tensorflow-apple-m1.yml -n csci349
```
*Note: csci349 can be changed to whatever you would like to call this new environment*

Finally, activate the new environment
```
conda activate csci349
```
[OPTIONAL] ensure that the tensorflow versions match by running the following
```
python -m pip install tensorflow-macos==2.9.0 tensorflow-metal==0.6.0 --force-reinstall
```

## Step 5 Register the Environment
This command ensures that our environment shows up as a kernel in jupyter
```
python -m ipykernel install --user --name csci349 --display-name "Python 3.9 (csci349)"
```

Then, test the environment with
`jupyter notebook` or `jupyter lab` and make sure to change the kernel in the top right to "Python 3.9 (csci349)"

If you are using PyCharm make sure to set the interpreter to "Python 3.9 (csci349)" as well 

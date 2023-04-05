# M1-TensorFlow-Installation-Guide
A short guide to getting tensorflow to work with the m1 and m2 macs

Modified guide from Jeff Heaton which can be found [here](https://github.com/jeffheaton/t81_558_deep_learning/blob/master/install/tensorflow-install-mac-metal-jan-2023.ipynb)

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

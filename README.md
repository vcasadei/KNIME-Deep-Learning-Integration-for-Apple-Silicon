# Installing KNIME Deep Learning Integration on Apple Silicon

I've created an environment file ([environment.yml](environment.yml)) with all the necessary libraries for the KNIME Deep Learning Integration installation for Apple Silicon.

## Why we need this?

KNIME has an [official page on how to install](https://docs.knime.com/latest/deep_learning_installation_guide/), however it uses older versions of some libraries, such as [Python 3.6.13](https://www.python.org/downloads/release/python-3613/). The problem is that these older versions are not compiled for Apple Silicon (platform armosx-64) and Anaconda or Miniforge do not offer these versions for the Apple Silicon Platform ([see here](https://anaconda.org/conda-forge/python/files?version=3.6.13)).

KNIME then says that you can use a simple workflow to make it work ([workflow](https://hub.knime.com/s/lbXIHueMXd1u739n)). But in my experience, this does not work as well.

> On Apple computers with the Apple Silicon Chips you need to create an environment with specific packages in order to use the KNIME Deep Learning Integration. You can use the following workflow from the KNIME Community Hub to create a conda environment with all the required packages
*From [KNIME Installation guide](https://docs.knime.com/latest/deep_learning_installation_guide/).*

# How to solve this?

1. We need to install [Anaconda](https://www.anaconda.com/download) or [Conda-Forge](https://conda-forge.org/download/) for arm64 or Apple Silicon.

2. Then, install Rosetta using a Terminal with the following command:

'''bash
/usr/sbin/softwareupdate --install-rosetta --agree-to-license
'''

3. Create an environment with the ([environment.yml](environment.yml)) file and setting platform as 'osx-64':

'''bash
conda env create -f environment.yml --platform osx-64
'''

That's it! Now you just need to open KNIME and select the environment named 'knime_dl_mac' on the settings. You can follow the [KNIME Installation guide](https://docs.knime.com/latest/deep_learning_installation_guide/) for this.

## How to test?

After configuring the settings, you may donwload the following [workflow](https://hub.knime.com/s/u1r90u1HtRee4EQq) and execute it. If it does not present any erros, everything is working!

### I need help!

I made a video explaining step-by-step with some common problems. You can [watch it here](https://youtu.be/2ompUejF1kE) (It's in Portuguese, but with English Subs)

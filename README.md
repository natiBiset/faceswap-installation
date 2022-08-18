# faceswap-installation

this is installation guide for facesawp on aws ubuntu ec2 instance.
# installation


- install anaconda as its the prefered method in the oficial ripo for the faceswap tool.

*we use pyenv here*

```pyenv install anaconda3-2022.05```

and lets activate it: `pyenv activate anaconda3-2022.05`

- clone the original faceswap repository with : `git clone --depth 1 https://github.com/deepfakes/faceswap.git`
- Enter the faceswap folder: `cd faceswap`
- Enter the command `python setup.py` and follow the prompts
- to check if everything is installed correctly type: `python faceswap.py -h'

#

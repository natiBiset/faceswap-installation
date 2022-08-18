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

#creating the necessary folders
- some folders need to be created, i recommend the following structure to make the correct handling of files mre easy:
1. have a separate folder for the original video as well as for the lipsynced video.(here as an example we will have the original video under the folder name "video-original" and the lipsynced one in "video-lipsynced"
2. create multiple folders named," model" , "face-original" , "face-lipsynced" , "timelapse" , "output" in the same location as the "video-original" and "video-lipsynced" folders

# extracting faces from the videos
**Note, you can view the help section for each of the the three main commands we will use here with `python faceswap.py [extract][train][convert]
- extract the faces from the original video and put it in the "face-original" folder and do the dame with the lipsynced on ("face-lipsynced")
```python faceswap.py extract --detector s3fd --input-dir [location to the video] --output-dir [location to the folder(either "face-original" or "face-lipsynced")] ```

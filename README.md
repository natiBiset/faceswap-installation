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
2. create multiple folders named,"model" , "face-original" , "face-lipsynced" , "timelapse" , "output" in the same location as the "video-original" and "video-lipsynced" folders

# extracting faces
**Note, you can view the help section for each of the the three main commands we will use here with `python faceswap.py [extract][train][convert]
- extract the faces from the original video and put it in the "face-original" folder and do the dame with the lipsynced on ("face-lipsynced")
```python faceswap.py extract --detector s3fd --input-dir [location to the video] --output-dir [location to the folder(either "face-original" or "face-lipsynced")] ```

# Training 

- train the faceswap model with the following command:
```
python faceswap.py train --input-A [location to the face-lipsynced folder] --input-B [location to the face-original folder] --model-dir [location to the model folder we have created --timelapse-input-A [location to the face-lipsynced folder] --timelapse-input-B [location to the face-original folder] --timelapse-output [location to the timelapse folder we have created --batch-size 32 --save-interval 50
```
- the save-interval will help to save the trained model for each 50 iteration inorder to avoid wasting time and training from scratch incase of any connection issues. 
- the batch size 32 seems to work best for me , you can try to find anther optimal value
- you can hit enter when the model is training and the model will be saved and the training will be saved , and it will resume from that stage whenever you continue to train it.
- the number of iterations that will make the result video look good will depepend on the specific videos , but **the longer the model is trained the better**. 

# Converting

to convert the result from the above training into a video use:
```
python faceswap.py convert --input-dir [location to the lipsynced video]  --output-dir [location to the output folder] --model-dir [location to the model folder] --color-adjustment match-hist --writer ffmpeg

```
you can upscale the resulting video by adding `--output-scale 200` which will double the resolution. 



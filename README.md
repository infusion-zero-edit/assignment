# Problem Statement: Edit pose of an object in a scene

Recent advancement in generative AI has led to a development of a lot of creative workflows. One
such workflow is to use generative AI techniques for editing product photographs after they have
been shot at a studio, for example to polish the scene for displaying the product on an e-commerce
website. One such post-production editing requirement could be editing the pose of the object by
rotating it within the same scene.

This problem statement involves two tasks - for the eventual goal of developing technology for a
user-friendly pose edit functionality. The first task is to segment an object (defined by a user given
class prompt) in a given scene. This enables the ‘user-friendly’ part of the problem statement. The
second task is to edit the pose of the object by taking user poses (e.g. Azimuth +10 degrees, Polar -5
degrees). The final generated scene should look realistic and composite.

## Usage
```
pip install -r requirements.txt
pip install -e taming-transformers/
pip install -e CLIP/
pip install -e GroundingDINO/
```
Create folder checkpoints 
```
mkdir checkpoints
wget https://cv.cs.columbia.edu/zero123/assets/105000.ckpt
wget https://zero123.cs.columbia.edu/assets/zero123-xl.ckpt
```
Example Run Task-1
```
python task1.py --image ./inputs/office_chair.jpg --class_name "office chair" --output ./generated_office_chair.png
```
Example Run Task-2
```
python task2.py --image ./inputs/office_chair.jpg --class_name "office chair" --azimuth +72 --polar +0 --output ./generated_office_chair.png
```
We have used zero123-xl.ckpt and 105000.ckpt interchangeably to get best results which is stored in the folder outputs. For example lamp example gives best output with 105000.ckpt however zero123-xl.ckpt does not able to produce lamp and it gives random image. While in case of office chair the checkpoint 105000.ckpt produce distorted image while zero123-xl.ckpt produces better image.


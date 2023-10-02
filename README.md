### StyleEmbryo

The training data is available at [here](https://drive.google.com/file/d/1oFrAzSIjW3pbjEhSWswRTIEEb_sqJatT/view?usp=sharing).
The pretrained weights from this study are at [here](https://drive.google.com/drive/folders/1kegtpN3VaC5-irWP6F58qrK9KJrzkbp-?usp=sharing).

#### Training 
1. Baseline model
```
python train.py --outdir=./output_gan --data=./embryoGAN256.zip --cfg=stylegan3-t --aug=noaug --gpus=4 --batch=32 --gamma=2 \
    --freezed=13 --workers=2 --mirror=0 --kimg=5000 --tick=2 --snap=50 --metrics=none --cbase=16384 
```

2. Baseline+AUG model
   
```
python train.py --outdir=./output_gan --data=./embryoGAN256.zip --cfg=stylegan3-t --gpus=4 --batch=32 --gamma=2 \
--freezed=13 --workers=2 --mirror=1 --kimg=5000 --tick=2 --snap=50 --metrics=none --cbase=16384 
```

3. Pretrained-T model

```
python train.py --outdir=./output_gan --data=./embryoGAN256.zip --cfg=stylegan3-t --aug=noaug --gpus=4 --batch=32 --gamma=2 \
--freezed=13 --workers=2 --mirror=0 --kimg=5000 --tick=2 --snap=50 --metrics=none --cbase=16384 \
--network=./weights/stylegan3-t-ffhqu-256x256.pkl
```

4. Pretrained-T+AUG model
   
```
python train.py --outdir=./output_gan --data=./embryoGAN256.zip --cfg=stylegan3-t --gpus=4 --batch=32 --gamma=2 \
--freezed=13 --workers=2 --mirror=1 --kimg=5000 --tick=2 --snap=50 --metrics=none --cbase=16384 \
--network=./weights/stylegan3-t-ffhqu-256x256.pkl
```

5. Pretrained-R+AUG model
   
```
python train.py --outdir=./output_gan --data=./embryoGAN256.zip --cfg=stylegan3-r --gpus=4 --batch=32 --gamma=2 \
--freezed=13 --workers=2 --mirror=1 --kimg=5000 --tick=2 --snap=50 --metrics=none --cbase=16384 \
--network=./weights/stylegan3-t-ffhqu-256x256.pkl
```

#### Generating image 

```
python gen_images.py --outdir=./data/25000 --trunc=1 --seeds=100 \
    --network=./weights/network-snapshot-025000.pkl
```

#### Calculating metrics
```
python calc_metrics.py --metrics=fid50k_full,pr50k3_full,kid50k,is50k --data=./embryoGAN256.zip --mirror=1 --gpus=1 \
    --network=./weights/network-snapshot-025000.pkl
```

### StyleEmbryo

training example
```
python train.py --outdir=./output_gan --data=./embryoGAN256.zip --cfg=stylegan3-t --gpus=4 --batch=32 --gamma=2 \
--freezed=13 --workers=2 --mirror=1 --kimg=5000 --tick=2 --snap=50 --metrics=none --cbase=16384

```

generate image 
```
python gen_images.py --outdir=./gen-images --trunc=1 --seeds=100 \
#    --network=./network-snapshot-025000.pkl
```

calculate metrics
```
python calc_metrics.py --metrics=fid50k_full,pr50k3_full,kid50k,is50k --data=./embryoGAN256.zip --mirror=1 --gpus=1 \
    --network=./network-snapshot-025000.pkl
```

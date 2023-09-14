# The training data link
### https://drive.google.com/file/d/1oFrAzSIjW3pbjEhSWswRTIEEb_sqJatT/view?usp=drive_link ###

# Randomly generated 100 images
python stylegan3/gen_images.py --outdir=./data/25000 --trunc=1 --seeds=100 \
   --network=./weights/network-snapshot-025000.pkl

# simple_disco_diffusion_cli ver0.01

## Description

A simple CLI tool for disco diffusion

CLI tool developed by `Jian Lin (github: Nayzi-2019)` base on [Disco Diffusion v5.4](https://colab.research.google.com/github/alembics/disco-diffusion/blob/main/Disco_Diffusion.ipynb)

<br>

Licensed under the MIT License

## Requirements
- Nvidia CUDA 11 (or 10 but extra steps)
- python 3.9
<br>

## Application Installation

### Prepare for installation

Make sure you can run these on your terminal (or cmd, **NOT** powershell)
```
wget --version
git --version
```

### Python env install

using virtualenv python3.9
```
pip install virtualenv
virtualenv venv -p path/to/your/python3.9
```
Then activate your virtualenv

- **Linux**
```
source ./venv/bin/activate
```
- **Win10**
```
powershell
./venv/Scripts/Activate.ps1
```

pip install requirements in requirements.txt
```
pip install -r requirements.txt
```
<br>

## Setup and Test

To step up the required package and folders, run a simple script to start setup the process
```
python discoCLI.py -t ["mountain"] -s 25 -S 20
```
including git clone & wget pretrained model, it's going to download 10GB files to your proj.

Or you can download it manually by uncomment the raise
```
def wget(url, outputdir):
        print(f'wget from source: {url} to path: {outputdir}')
        # Uncomment the raise if you want to download it manually
        # raise
        res = subprocess.run(['wget', url, '-P', f'{outputdir}'], stdout=subprocess.PIPE).stdout.decode('utf-8')
        print(res)
```

which you can predownload the require models by the following url
```

# put the following models to ./models
https://the-eye.eu/public/AI/models/512x512_diffusion_unconditional_ImageNet/512x512_diffusion_uncond_finetune_008100.pt
https://openaipublic.blob.core.windows.net/diffusion/jul-2021/256x256_diffusion_uncond.pt
https://github.com/intel-isl/DPT/releases/download/1_0/dpt_large-midas-2f21e586.pt
https://v-diffusion.s3.us-west-2.amazonaws.com/secondary_model_imagenet_2.pth
https://github.com/intel-isl/DPT/releases/download/1_0/dpt_hybrid-midas-501f0c75.pt


# put the following models to ./pretrained
https://cloudflare-ipfs.com/ipfs/Qmd2mMnDLWePKmgfS8m6ntAg4nhV5VkUyAydYBp8cWWeB7/AdaBins_nyu.pt
        
```

## Usage

Use -h arg to checkout
```
python discoCLI.py -h
```

Example: draw `painting of Taipei street and cyberpunk, Trending on artstation, without human`, output to `Taipei` folder with step `250` and draw `2` paintings in this batch
```
python discoCLI.py -t "Taipei street and cyberpunk, artstation" "human:-2" -s 250 -o "Taipei" -n 2
```

Example: draw `a plane base on an image(./init_images/sky.png)`, output to `Plane` folder with step `250`, skip `200` steps and draw `1` paintings in this batch
```
python discoCLI.py -I 'path/to/image.png' -S 200 -t "plane, artstation" "human:-2" -s 250 -o "Plane"
```








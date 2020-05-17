[![Run on Ainize](https://ainize.ai/static/images/run_on_ainize_button.svg)](https://ainize.web.app/redirect?git_repo=github.com/kmswlee/UGATIT)
>if you use Ainize, please input jpg/png file.</br>
if you input other file not jpg/png, It will not work.please do not input other kinds of file.
## U-GAT-IT &mdash; Official TensorFlow Implementation (ICLR 2020)
### : Unsupervised Generative Attentional Networks with Adaptive Layer-Instance Normalization for Image-to-Image Translation

<div align="center">
  <img src="./assets/teaser.png">
</div>

### [Paper](https://arxiv.org/abs/1907.10830) | [Official Pytorch code](https://github.com/znxlwm/UGATIT-pytorch)
This repository provides the **official Tensorflow implementation** of the following paper:

> **U-GAT-IT: Unsupervised Generative Attentional Networks with Adaptive Layer-Instance Normalization for Image-to-Image Translation**<br>
> **Junho Kim (NCSOFT)**, Minjae Kim (NCSOFT), Hyeonwoo Kang (NCSOFT), Kwanghee Lee (Boeing Korea)
>
> **Abstract** *We propose a novel method for unsupervised image-to-image translation, which incorporates a new attention module and a new learnable normalization function in an end-to-end manner. The attention module guides our model to focus on more important regions distinguishing between source and target domains based on the attention map obtained by the auxiliary classifier. Unlike previous attention-based methods which cannot handle the geometric changes between domains, our model can translate both images requiring holistic changes and images requiring large shape changes. Moreover, our new AdaLIN (Adaptive Layer-Instance Normalization) function helps our attention-guided model to flexibly control the amount of change in shape and texture by learned parameters depending on datasets. Experimental results show the superiority of the proposed method compared to the existing state-of-the-art models with a fixed network architecture and hyper-parameters.*

## Pretrained model
> We released 50 epoch and 100 epoch checkpoints so that people could test more widely.
> 
> steps:
> 1. download checkpoint you want to.
> 2. unzip download file on your cloned remote folder. don't change folder, file names.
* [selfie2anime checkpoint (50 epoch)](https://drive.google.com/file/d/1V6GbSItG3HZKv3quYs7AP0rr1kOCT3QO/view?usp=sharing)
* [selfie2anime checkpoint (100 epoch)](https://drive.google.com/file/d/19xQK2onIy-3S5W5K-XIh85pAg_RNvBVf/view?usp=sharing)

## Dataset
* [selfie2anime dataset](https://drive.google.com/file/d/1xOWj1UVgp6NKMT3HbPhBbtq2A4EDkghF/view?usp=sharing)

## Web page
* [Selfie2Anime](https://selfie2anime.com) by [Nathan Glover](https://github.com/t04glovern)
* [Selfie2Waifu](https://waifu.lofiu.com) by [creke](https://github.com/creke)

## Telegram Bot
* [Selfie2AnimeBot](https://t.me/selfie2animebot) by [Alex Spirin](https://github.com/sxela)

## Usage
```
├── dataset
   └── YOUR_DATASET_NAME
       ├── trainA
           ├── xxx.jpg (name, format doesn't matter)
           ├── yyy.png
           └── ...
       ├── trainB
           ├── zzz.jpg
           ├── www.png
           └── ...
       ├── testA
           ├── aaa.jpg 
           ├── bbb.png
           └── ...
       └── testB
           ├── ccc.jpg 
           ├── ddd.png
           └── ...
```

### Train
```
> python main.py --phase train
# default phase is test
```
* If the memory of gpu is **not sufficient**, set `--light` to **True**
  * But it may **not** perform well
  * paper version is `--light` to **False**

### RUN on local
```
> git clone https://github.com/kmswlee/UGATIT
> cd UGATIT
> apt install -y libsm6 libxext6 libxrender-dev
> pip install flask -r requirements-gpu.txt
## if you can't use gpu, use 'requirements.txt'
> python app.py
```
you can browser http://localhost

### RUN on Docker
```
> git clone https://github.com/kmswlee/UGATIT
> cd UGATIT
> docker build -f Dockerfile.gpu -t ugatit .
> docker run -p 80:80 ugatit
```
you can browser http://localhost  
if you can't use gpu, use `Dockerfile` **not** `Dockerfile.gpu`

## Architecture
<div align="center">
  <img src = './assets/generator_fix.png' width = '785px' height = '500px'>
</div>

---

<div align="center">
  <img src = './assets/discriminator_fix.png' width = '785px' height = '450px'>
</div>

## Results
### Ablation study
<div align="center">
  <img src = './assets/ablation.png' width = '438px' height = '346px'>
</div>

### User study
<div align="center">
  <img src = './assets/user_study.png' width = '738px' height = '187px'>
</div>

### Kernel Inception Distance (KID)
<div align="center">
  <img src = './assets/kid_fix2.png' width = '750px' height = '400px'>
</div>

## Citation
If you find this code useful for your research, please cite our paper:

```
@inproceedings{
Kim2020U-GAT-IT:,
title={U-GAT-IT: Unsupervised Generative Attentional Networks with Adaptive Layer-Instance Normalization for Image-to-Image Translation},
author={Junho Kim and Minjae Kim and Hyeonwoo Kang and Kwang Hee Lee},
booktitle={International Conference on Learning Representations},
year={2020},
url={https://openreview.net/forum?id=BJlZ5ySKPH}
}
```

## Author
[Junho Kim](http://bit.ly/jhkim_ai), Minjae Kim, Hyeonwoo Kang, Kwanghee Lee

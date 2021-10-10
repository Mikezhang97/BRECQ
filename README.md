# Block Reconstruction Open Source Code for Demo
Main idea based on this paper: https://arxiv.org/pdf/2102.05426.pdf

```latex
@article{li2021brecq,
  title={BRECQ: Pushing the Limit of Post-Training Quantization by Block Reconstruction},
  author={Li, Yuhang and Gong, Ruihao and Tan, Xu and Yang, Yang and Hu, Peng and Zhang, Qi and Yu, Fengwei and Wang, Wei and Gu, Shi},
  journal={arXiv preprint arXiv:2102.05426},
  year={2021}
}
```

## Results

Using only the validation set for calibration, ResNet 18 (W4A4) pretrained model

Float model accuracy: 70.70%
Quantized accuracy before BRECQ: 54.40 %
Weight quantization accuracy: 71.100 %
Full quantization  accuracy: 70.0 %

## Command to run

```bash
python main_imagenet.py --data_path PATN/TO/DATA --arch resnet18 --n_bits_w 4 --channel_wise --n_bits_a 4 --act_quant --test_before_calibration
```
## Environment

RTX A6000 GPU from Lambda https://lambdalabs.com/

Encountering issues: 
```bash
RTX A6000 with CUDA capability sm_86 is not compatible with the current PyTorch installation.
```
Solution:
```bash
>>> torch.__version__
'1.11.0.dev20211009+cu111'
>>> tv.__version__
'0.12.0.dev20211009+cu111'
```
# Block Reconstruction Open Source Code for Demo
Main idea based on this paper: https://arxiv.org/pdf/2102.05426.pdf


## Results

Using only the validation set for calibration, ResNet 18 (W4A4) pretrained model

```latex
\begin{table}[]
\begin{tabular}{|l|l|l|}
\hline
\%                     & \multicolumn{2}{l|}{Resnet 18} \\ \hline
Quant                  & W4A4          & W2A4           \\ \hline
Float                  & \multicolumn{2}{l|}{70.70}     \\ \hline
Before BRECQ           & 54.40         & 0.200          \\ \hline
Only weights           & 71.10         & 68.800         \\ \hline
Weights and activation & 70.00         & 68.100         \\ \hline
\end{tabular}
\end{table}
```
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
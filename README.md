# Block Reconstruction Open Source Code for Demo
Main ideas based on this paper: https://arxiv.org/pdf/2102.05426.pdf


## Command to run

```bash
python main_imagenet.py --data_path PATN/TO/DATA --arch resnet18 --n_bits_w 4 --channel_wise --n_bits_a 4 --act_quant --test_before_calibration
```
## Running Demo

![Demo GIF](https://github.com/mike-zyz/BRECQ/blob/main/Pictures/ezgif.com-gif-maker.gif)

## Results

Using only the validation set for calibration, ResNet 18 (W4A4) pretrained model

```{=html}

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-0pky">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;%</th>
    <th class="tg-0pky" colspan="2">Resnet 18</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0pky">Quant</td>
    <td class="tg-0pky">W4A4</td>
    <td class="tg-0pky">W2A4</td>
  </tr>
  <tr>
    <td class="tg-0pky">Float</td>
    <td class="tg-0pky" colspan="2">     70.70</td>
  </tr>
  <tr>
    <td class="tg-0pky">Before BRECQ</td>
    <td class="tg-0pky">54.40</td>
    <td class="tg-0pky">0.200</td>
  </tr>
  <tr>
    <td class="tg-0pky">Only weights</td>
    <td class="tg-0pky">71.10</td>
    <td class="tg-0pky">68.800</td>
  </tr>
  <tr>
    <td class="tg-0pky">Weights and activation</td>
    <td class="tg-0pky">70.00</td>
    <td class="tg-0pky">68.100</td>
  </tr>
</tbody>
</table> 

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
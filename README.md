# ACANet: Adaptive Context Aggregation Network for Monocular Depth Estimation.

Pytorch implementation of ACANet for monocular depth estimation.</br>

## Architecture
<p align="center">
    <img src="/images/architecture.png"></br>
</p>

## Supervised Self-Attention
<p align="center">
    <img src="/images/self-attention.png"></br>
</p>

## Visualization of Attention Maps

<p align="center">
    <img src="/images/nyu_att.png"></br>
</p>

* The first and second row respectively denotes the attention maps trained with and w/o `Attention Loss`. </br>

## Soft Inference VS Hard Inference

<p align="center">
    <img src="/images/soft_vs_hard1.png"></br>
    <img src="/images/soft_vs_hard2.png"></br>
</p>

* The third column and the fourth column respectively denotes the results of soft inference and hard inference. </br>
## Quick start

### Requirements
~~~~
torch=0.4.1
torchvision
tensorboardX
pillow
tqdm
h5py
scikit-learn
cv2
~~~~
This code was tested with Pytorch 0.4.1, CUDA 9.1 and Ubuntu 18.04.  </br>

### Data

### [NYU v2](https://cs.nyu.edu/~silberman/datasets/nyu_depth_v2.html)
We download the raw dataset, which weights about 428GB. We use the toolbox of NYU v2 to sample around 12k training samples, you can find them in the [matlab](code/matlab) folder and use `Get_Dataset.m` to produce the training set.

### Training

**Warning:** The input sizes need to be mutiples of 8. 

```shell
bash ./code/train_nyu_script.sh
```

### Testing  
```shell
bash ./code/test_nyu_script.sh
```

### Attention Map
If you want to get the task-specific attention maps, you should first train your model from scratch, then finetuning with attention loss, by setting
~~~~
BETA=1
RESUME=./workspace/log/best.pkl
~~~~

## Thanks to the Third Party Libs
[Non-local_pytorch](https://github.com/AlexHex7/Non-local_pytorch)

[Pytorch-OCNet](https://github.com/PkuRainBow/OCNet.pytorch)

[NConv-CNN](https://github.com/abdo-eldesokey/nconv-nyu)



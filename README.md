# CBAM-TensorFlow
This is a Tensorflow implementation of ["CBAM: Convolutional Block Attention Module"](https://arxiv.org/pdf/1807.06521).
This repository includes the implementation of ["Squeeze-and-Excitation Networks"](https://arxiv.org/pdf/1709.01507) as well, so that you can train and test among base CNN model, base model with CBAM block and base model with SE block.
Base CNN models are *ResNext*, *Inception-V4*, and *Inception-ResNet-V2* where the original implementation is from [SENet-Tensorflow](https://github.com/taki0112/SENet-Tensorflow).

If you want to use more sophisticated implementation and more base models to use, check the repository [CBAM-TensorFlow-Slim]() which aims to be compatible on the [TensorFlow-Slim image classification model library](https://github.com/tensorflow/models/tree/master/research/slim) and support more base models.

## CBAM: Convolutional Block Attention Module
**CBAM** proposes an architectural unit called *"Convolutional Block Attention Module" (CBAM)* block to improve representation power by using attention mechanism: focusing on important features and supressing unnecessary ones.
This research can be considered as a descendant and an improvement of ["Squeeze-and-Excitation Networks"](https://arxiv.org/pdf/1709.01507).

### Diagram of a CBAM_block
<div align="center">
  <img src="https://github.com/kobiso/CBAM-tensorflow/blob/master/figures/overview.png">
</div>

### Diagram of each attention sub-module
<div align="center">
  <img src="https://github.com/kobiso/CBAM-tensorflow/blob/master/figures/submodule.png">
</div>

### Classification results on ImageNet-1K

<div align="center">
  <img src="https://github.com/kobiso/CBAM-tensorflow/blob/master/figures/exp4.png">
</div>

<div align="center">
  <img src="https://github.com/kobiso/CBAM-tensorflow/blob/master/figures/exp5.png"  width="750">
</div>

## Prerequisites
- Python 3.x
- TensorFlow 1.x
- tflearn

## Prepare Data set
This repository use [*Cifar10*](https://www.cs.toronto.edu/~kriz/cifar.html) dataset.
When you run the training script, the dataset will be automatically downloaded.

## CBAM_block and SE_block Supportive Models
You can train and test base CNN model, base model with CBAM block and base model with SE block.
You can run **CBAM_block** or **SE_block** added models in the below list by adding one argument `--attention_module=cbam_block` or `--attention_module=se_block` when you train a model.

- Inception V4 + CBAM / + SE
- Inception-ResNet-v2 + CBAM / + SE
- ResNeXt + CBAM / + SE

### Change *Reduction ratio*
To change *reduction ratio*, you can add an argument `--reduction_ratio=8`.

## Train a Model
You can simply run the model by executing following scripts.
- `sh train_ResNext.sh`
- `sh train_inception_resnet_v2.sh`
- `sh train_inception_v4.sh`

### Train a model with CBAM_block
Below script gives you an example of training a model with CBAM_block.
```
CUDA_VISIBLE_DEVICES=0 python ResNeXt.py \
--model_name put_your_model_name \
--attention_module cbam_block  \
--reduction_ratio 8 \
--learning_rate 0.1 \
--weight_decay 0.0005 \
--momentum 0.9 \
--batch_size 128 \
--total_epoch 100 \
--attention_module cbam_block
```

### Train a model with SE_block
Below script gives you an example of training a model with SE_block.
```
CUDA_VISIBLE_DEVICES=0 python ResNeXt.py \
--model_name put_your_model_name \
--attention_module cbam_block  \
--reduction_ratio 8 \
--learning_rate 0.1 \
--weight_decay 0.0005 \
--momentum 0.9 \
--batch_size 128 \
--total_epoch 100 \
--attention_module se_block
```


### Train a model without attention module
Below script gives you an example of training a model without attention module.
```
CUDA_VISIBLE_DEVICES=0 python ResNeXt.py \
--model_name put_your_model_name \
--attention_module cbam_block  \
--reduction_ratio 8 \
--learning_rate 0.1 \
--weight_decay 0.0005 \
--momentum 0.9 \
--batch_size 128 \
--total_epoch 100
```

## Related Works
- [CBAM-TensorFlow-Slim](https://github.com/kobiso/CBAM-tensorflow-slim)
- [SENet-TensorFlow-Slim](https://github.com/kobiso/SENet-tensorflow-slim)

## Reference
- [CBAM: Convolutional Block Attention Module](https://arxiv.org/pdf/1807.06521)
- [Squeeze-and-Excitation Networks](https://arxiv.org/pdf/1709.01507)
- [TensorFlow-Slim image classification model library](https://github.com/tensorflow/models/tree/master/research/slim)
- [SENet-Tensorflow](https://github.com/taki0112/SENet-Tensorflow)
  
## Author
Byung Soo Ko / kobiso62@gmail.com

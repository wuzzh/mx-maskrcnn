# MX Mask R-CNN
An MXNet implementation of [Mask R-CNN](https://arxiv.org/abs/1703.06870).

This repository is a experiment statistics and analyzing on [mx-maskrcnn](https://github.com/precedenceguo/mx-rcnn) repo by [TuSimple](https://github.com/TuSimple).


<div align="center">
<img src="https://github.com/TuSimple/mx-maskrcnn/blob/master/figures/maskrcnn_result.png"><br><br>
</div>


## Main Results by TuSimple


### Cityscapes

| Method |Training data| Test data| Average | person | rider | car | truck | bus  | train| motorcycle| bicycle|
|:---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| Ours| fine-only |test|26.9|33.0|25.7|47.7|21.6|27.4|23.0|19.9|16.9|
| Reference[5]| fine-only |test|26.2|30.5|23.8|46.9|22.8|32.2|18.6|19.1|16.0|
| Ours | fine-only |val|31.3|32.6|26.6|49.5|26.5|45.4|32.1|17.6|20.4|
| Reference[5]| fine-only |val|31.5| -| -| -| -| -| -| -| -| -| -|

- Backbone: Resnet-50-FPN

## Our Experiments Results on Cityscapes

| Training data | Test data | cls network | epoch rpn/rcnn | traing scale | test scale | rcnn batch size | AP | AP50% |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| fine-only | test | resnet50(by tusimple) | 8/24 | 820-1024 | 1024 | 256 | 26.4 | 49.2 |
| fine-only | val  | resnet50(by tusimple) | 8/24 | 820-1024 | 1024 | 256 | 31.4 | 57.5 |


## Quick Experiments
To evaluate different classification network on maskrcnn, we experimented resnet101-v1 and air101.
For quick experiments, we cut down the training epoch of both rpn and rcnn to a quarter of the original epoch set by TuSimple.

| Training data | Test data | cls network | epoch rpn/rcnn | traing scale | test scale | rcnn batch size | AP | AP50% | test time |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| fine-only | val | resnet50(by tusimple) | 2/6 | 820-1024 | 1024 | 256 | 21.6 | 42.9 | - |
| fine-only | val | resnet50 | 2/6 | 820-1024 | 1024 | 128 | 17.7 | 37.1 | 1.71 | 
| fine-only | val | resnet101-v1 | 2/6 | 820-1024 | 1024 | 128 | 24.1 | 47.7 | 1.84 | 
| fine-only | val | air101 | 2/6 | 410-512 | 512 | 256 | 13.1 | 28.6 | 2.26 |

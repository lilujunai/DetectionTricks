# ImageNet Detection Tricks

## ATLAB ImageNet leaderboard
| model | mAP | eval method | Training set | PreTrain set | Training Log | Eval Log | Base Module| config |
| ----- |---|---|---|---|---|---|---|---|
| 【ALL】= resnet101 (multiscale) + resnet101 ratio1:4,4:1 (multiscale) + resnet101 scale4 (multiscale) + resnet152 (multiscale) + inceptionv3 (multiscale) + rcnn_dcn (multiscale) | 0.5295 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| 【ENS1】=【ALL】 - dcn\_rcnn (scale1000, mAP=0.4231) | 0.5301 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| 【ENS2】=【ENS1】 - dcn\_rcnn (scale400, mAP=0.4249) | 0.5297 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| 【ENS3】=【ENS2】 - inceptionv3 (scale400, mAP=0.4257)| 0.5289 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| 【ENS4】=【ENS3】 - resnet152 (scale400, mAP=0.4318)  - resnet101\_ratio4 (scale400, mAP=0.4350) - resnet101\_scale4 (scale400, mAP=0.4375)| 0.5289 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| 【ENS5】=【ALL】 - resnet152 (scale400, mAP=0.4318)  - resnet101\_ratio4 (scale400, mAP=0.4350) - resnet101\_scale4 (scale400, mAP=0.4375)| 0.5298 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| 【ENS6】=【ENS1】 + dcn\_rfcn (scale600, mAP=0.4695) | 0.5305 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| 【ENS7】=【ENS6】 - resnet101 (scale400, mAP=0.4456) | 0.5295 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| 【ENS8】=【ENS7】 - resnet101 (scale1000, mAP=0.4532) | 0.5301 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| 【ENS9】=【ENS8】 - resnet101\_scale4 (scale1000, mAP=0.4555) | 0.5296 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| 【ENS10】=【ENS9】 - dcn\_rfcn (scale800, mAP=0.4597) | 0.5292 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| resnet101(multiscale) + resnet152 + inceptionv3 + rcnn_dcn | 0.5238 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| resnet101(multiscale) +resnet152 +inceptionv3 | 0.5222 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| resnet101(multiscale) +deepmask +resnet152 +inceptionv3 | 0.5213 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| resnet101(multiscale) +deepmask +resnet152|0.5141 |nms+box voting | Imagenet all|-|-|-|-|NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
| resnet101(multiscale) +deepmask | 0.5090 | [nms+box voting](https://github.com/ataraxialab/DetectionTricks/blob/dev/ensemble/BoxVoting.md) | Imagenet all | - | - | - | -| NMS＝0.5 IoU_Thresh=0.5 score_Thresh=0.1 |
|[Resnet-101 std](http://op3uxikvk.bkt.clouddn.com/resnet-101-all.params)|0.4874|[test.py](https://github.com/likelyzhao/mxnet/blob/dev-faster-rcnn/example/rcnn/test.py)|ImageNet all|None|[Train](http://op3uxikvk.bkt.clouddn.com/resnet-101-all-train.log)|[Test](http://op3uxikvk.bkt.clouddn.com/resnet-101-all-test.log)|[Resnet-101 param](http://data.dmlc.ml/mxnet/models/imagenet/resnet/101-layers/resnet-101-0000.params) [Resnet 101 modeljson](http://data.dmlc.ml/mxnet/models/imagenet/resnet/101-layers/resnet-101-symbol.json)|[config](https://github.com/likelyzhao/mxnet/blob/dev-faster-rcnn/example/rcnn/rcnn/config.py)|
|[ResNet-101 smalldb](http://op3uxikvk.bkt.clouddn.com/resnet101-params)|0.3958|[test.py](https://github.com/likelyzhao/mxnet/blob/dev-faster-rcnn/example/rcnn/test.py)|ImageNet train_0| None |[Train](http://op3uxikvk.bkt.clouddn.com/Resnet101-smalldb-train.log)|[Eval](http://op3uxikvk.bkt.clouddn.com/Resnet101-smalldb-eval.log)|[Resnet-101 param](http://data.dmlc.ml/mxnet/models/imagenet/resnet/101-layers/resnet-101-0000.params) [Resnet 101 modeljson](http://data.dmlc.ml/mxnet/models/imagenet/resnet/101-layers/resnet-101-symbol.json)|[config](https://github.com/likelyzhao/mxnet/blob/dev-faster-rcnn/example/rcnn/rcnn/config.py)



## 基础模型
* [ResNet-101 Variants](http://op3uxikvk.bkt.clouddn.com/resnet101-params)

### 使用多个差异很大的CNN模型 - diversity matters!
* 7 * BN-Inception (32 Layers)
* 2 * MSRA-Net (22 Layers)
* ResNet, Identity Map

### 数据放大
* random crop
* multi-scale
* contrast jittering
* color jittering
* Pretrain on LOC !!

### 单个模型的改进
* Objectness loss
* Negative categories
* BBox Voting

## 训练技巧
* Balanced Sampling
* Multi-Scale Training
* Online Hard Sample Mining

### RPN Proposal
* Cascade RPN
* Constrained Neg/Pos Anchor Ratio

### Pretraining
* Pretrained Global Context


## 测试技巧
* Multi-Scale Testing
* HFlip
* Box Votinng


Tricks的实现划分在以下5个文件夹中：
* dataprocess
* regionproposal
* fastrcnn
* postprocess
* ensumble

上述代码尝试做成平台无关，与计算框架相关的代码都在*PlatformRelated*文件夹中



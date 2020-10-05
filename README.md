# Object detection learning materials

把蒐集到的不錯的文章、值得深究的名詞(或東西)記錄下來，並更深度學習！

[這個網站](https://paperswithcode.com/sota/object-detection-on-coco)可以知道 dataset 下各家 model 的表現如何？

## Measure
### mAP (mean average precisions)
![](https://i.imgur.com/3iAJybu.png)


## YOLOv4
友善的[中文介紹](https://zhuanlan.zhihu.com/p/135909702)可以先看一下。以下是 yolov4 主要組成，跟該階段的 improving skills：
- Backbone: CSPDarknet53 - 主要目的是
    - BoF
        - data augmentation: CutMix(2019), Mosaic
            ![](https://i.imgur.com/V9BS4ga.png)
            CutMix 可以得到比 Mixup & Cutout 更好的結果，但 bounding box ground truth 要重做
            ![](https://i.imgur.com/hOQaMKW.png)
            根據下圖可以看出 Mosaic 是 BoF 裡最具影響力的方法，但 bbox 一樣要解決
            ![](https://i.imgur.com/cwHP0aR.png)
        - regularization: DropBlock, 把遮擋的概念運用在 model 中
        - Class labeling smoothing: 不要絕對的 1 跟 0 ，目標是解決 overfitting & **overconfidence**
    - BoS
        - Mish activation
        - Cross-stage partial connections (CSP)
        - Multi- input weighted residual connections (MiWRC)
- Neck：SPP, PAN - 主要目的是
- Head：YOLOv3 - 主要目的是

For detector：
- BoF
	- data augmentation: Mosaic
    - regularization: DropBlock
    - Self-Adversarial Training
    - Eliminate grid sensitivity
    - Using multiple anchors for a single ground truth
    - Cosine annealing scheduler
    - Optimal hyper- parameters
    - Random training shapes
    - CmBN
    - CIoU-loss
- BoS
    - Mish activation
    - SPP-block
    - SAM-block
    - PAN path-aggregation block
    - DIoU-NMS

文內還整理了眾多模型的不同功能、隸屬的階段 (論文 fig.2)

模型與其運用的硬體也有關係：
- GPU: CSPResNeXt50 / CSPDarknet53 (CPSNet 也該看一下！)
- VPU: EfficientNet-lite / MixNet / GhostNet / MobileNetV3 (What is VPU?)

### tiny-yolo 是什麼？
[中文網站](https://zhuanlan.zhihu.com/p/151389749)

![](https://i.imgur.com/gZiOdZ4.png)


## YOLOv5
[這篇文章](https://zhuanlan.zhihu.com/p/161083602)有針對 v5 跟 v4 的差別做比較



## References
可以看 [計算機視覺論文速遞](https://zhuanlan.zhihu.com/c_172507674) 跟上一下新知

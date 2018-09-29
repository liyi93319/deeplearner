NMS
本文档主要参考以下两篇paper

[Shaoqing Ren et al. 2016, Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks]

[Jan Hosang et al. 2017, Learning non-maximum suppression]

以下是在靳老师的指导下的总结

NMS 是 non-maximum suppression 的缩写，中译为 非极大值抑制，在 Object Detection 任务中的作用是去重。
这是因为，第一次将图片输入网络时，R-CNN 会对同一个物体，比如同一张人脸，输出多个回归框（比如3个），如下图所示

![proposals](https://github.com/liyi93319/deeplearner/blob/master/proposals.png)

而我们只需要一个最合适的框，nms就是做这件事的。
大体思路是，把这些回归框按照评分由高到低排序，得到 0.9、0.8、0.75
选出最高分的框，0.9，计算剩余的两个框与0.9这个框的重叠面积比例Intersection-over- Union (IoU)，根据预先设定的 IoU 阈值，删掉达到条件的框。

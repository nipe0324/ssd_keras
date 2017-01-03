# A port of [SSD: Single Shot MultiBox Detector](https://github.com/weiliu89/caffe/tree/ssd) to [Keras](https://keras.io) framework.
For more details, please refer to [arXiv paper](http://arxiv.org/abs/1512.02325).
For forward pass for 300x300 model, please, follow `SSD.ipynb` for examples. For training procedure for 300x300 model, please, follow `SSD_training.ipynb` for examples. Moreover, in `testing_utils` folder there is a useful script to test `SSD` on video or on camera input.

Weights are ported from the original models and are available [here](https://mega.nz/#F!7RowVLCL!q3cEVRK9jyOSB9el3SssIA). You need `weights_SSD300.hdf5`, `weights_300x300_old.hdf5` is for the old version of architecture with 3x3 convolution for `pool6`.

## Memo

I didn't try below codes yet.

* Howt to convert caffe weights to keras weights?

https://gist.github.com/rykov8/5fa4d2faff2e5e4704df54729bf57159

* How to create own training data?

Create `gt_pascal.pkl`. Don't need to create `prior_boxes_ssd300.pkl` because it depends on ssd300 architecture.

To create `gt_pascal.pkl`

```
# data type: dict
# key: filename
# value: [xmin, ymin, xmax, ymax, label (one-hot vector)]
#        maybe, xmin, ymin, xmax, ymax are 0. to 1. for regularized input image

# sample (detect 4 classes)
{
  'frame00600.png' : [
    [xmin, ymin, xmax, ymax, 1, 0, 0, 0],
    [xmin, ymin, xmax, ymax, 0, 1, 0, 0]
  ],
  'frame00601.png' : [
    [xmin, ymin, xmax, ymax, 0, 1, 0, 0],
    [xmin, ymin, xmax, ymax, 0, 1, 0, 0]
  ],
  ...
}
```

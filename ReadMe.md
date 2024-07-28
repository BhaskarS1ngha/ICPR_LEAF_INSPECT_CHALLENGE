# [ICPR LEAF INSPECT CHALLENGE](https://sites.google.com/view/icpr-2024/about-challenge?authuser=0)
## Goal: Leaf instance segmentation
**ML framework: Pytorch**

**ML model: [Mask2former by facebook](https://huggingface.co/facebook/mask2former-swin-large-coco-instance)**

**Note:** Recommended to use GPU for training and testing. Code written in google colab environment

This repository contains 2 notebooks
>1. Train_model.ipynb This notebook is used to train the model. You can change the source directories for the dataset at the beginning of the notebook.

>2. Inference.ipynb This notebook is used to test the model. You can change the source directories for the dataset and model used at the beginning of the notebook. This notebook generates the output images in the output folder.

The dataset provided has been preprocesssed to match the format expecterd by mask2former for instance segmentation tasks. The provided label images were converted into 3 channel RGB images where the **R(ed)** channel encodes category ID, and the **G(reen)** channel encodes instance ID. Each object instance has a unique instance ID regardless of its category ID.
**DO NOT** be alarmed if you see a blank mask as the masks are not designed to be human-readable. As there is only one category (leaf) in this dataset with its category id being 1, you may not see anything if there are only a few instances of leaves.

## Dependencies
>1. Pytorch
>2. opencv-python
>3. numpy
>4. matplotlib
>5. albumentations
>6. Tensorboard
>7. tqdm
>8. datasets == 2.15
>9. transformers
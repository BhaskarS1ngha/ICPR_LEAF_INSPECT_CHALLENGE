<a href="https://colab.research.google.com/github/BhaskarS1ngha/ICPR_LEAF_INSPECT_CHALLENGE" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>
# [ICPR LEAF INSPECT CHALLENGE](https://sites.google.com/view/icpr-2024/about-challenge?authuser=0)
## Goal: Leaf instance segmentation
**ML framework: Pytorch**

**ML model: [Mask2former by facebook](https://huggingface.co/facebook/mask2former-swin-large-coco-instance)**

**Note:** Recommended to use GPU for training and testing. Code written in google colab environment

This repository contains 2 notebooks
>1. [Train_model.ipynb](/Train_model.ipynb) This notebook is used to train the model. You can change the source directories for the dataset at the beginning of the notebook.

>2. [Inference.ipynb](/Inference.ipynb) This notebook is used to test the model. You can change the source directories for the dataset and model used at the beginning of the notebook. This notebook generates the output images in the output folder.

The dataset provided has been preprocesssed to match the format expecterd by mask2former for instance segmentation tasks. The provided label images were converted into 3 channel RGB images where the **R(ed)** channel encodes category ID, and the **G(reen)** channel encodes instance ID. Each object instance has a unique instance ID regardless of its category ID.
**DO NOT** be alarmed if you see a blank mask as the masks are not designed to be human-readable. As there is only one category (leaf) in this dataset with its category id being 1, you may not see anything if there are only a few instances of leaves.

**Example:**

**RGB Image**
![Original RGB Image](/Resources/rgb_image.png "RGB Image") 
---
**Label Image from dataset**
![Label Image](/Resources/label_image.png "Label Image") 
---
**Mask Image after preprocessing**
![Mask image after preprocessing](/Resources/mask_image.png "Mask Image") 
---

### Directory structure
```
Repository Root
├── Validation Results
    ├── Output of the model on the validation dataset
├── mask2former-swin-large-leaf
    ├── Model weights
    ├── Model config file
    ├── Image preprocessor config file
```
## USAGE
### Train model
1. Clone the repository
2. Train the model
    >1. Open the [Train_model.ipynb](/Train_model.ipynb) notebook.
    >2. Change the source directories for the dataset and the `MODEL_SAVE_DIR` at the beginning of the notebook. `MODEL_SAVE_DIR` is the directory where the model weights will be saved. By default  `MODEL_DIRECTORY` is set to `mask2former-swin-large-leaf`.
    >3. Run the notebook.

### Test model
1. Clone the repository
2. Test the model
    >1. Open the [Inference.ipynb](/Inference.ipynb) notebook.
    >2. Change the `SOURCE_DIRECTORY` for the validation dataset and the `MODEL_DIRECTORY` at the beginning of the notebook. `MODEL_DIRECTORY` is the directory where the model weights are saved. By default  `MODEL_DIRECTORY` is set to `mask2former-swin-large-leaf`.
    >3. Run the notebook. Results will be saved to `results_dir`.

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
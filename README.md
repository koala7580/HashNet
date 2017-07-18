# HashNet
Code release for ["HashNet: Deep Learning to Hash by Continuation" (ICCV 2017)](https://arxiv.org/abs/1702.00758) 

## Datasets
We use ImageNet, NUS-WIDE and COCO dataset in our experiments. You can download the ImageNet dataset and NUS-WIDE dataset [here](https://drive.google.com/drive/folders/0B7IzDz-4yH_HOXdoaDU4dk40RFE?usp=sharing).
As for COCO dataset, we use COCO 2014, which can be downloaded [here](http://mscoco.org/dataset/#download). And in case of COCO changes in the future, we also provide a download link [here](https://drive.google.com/drive/folders/0B7IzDz-4yH_HOXdoaDU4dk40RFE?usp=sharing) on google drive.
After downloading, you need to move the imagenet.tar.gz to [./data/imagenet](./data/imagenet) and extract the file there. Also, you need to move the nus_wide.tar.gz to [./data/nuswide_81](./data/nuswide_81) and extract the file there. For COCO dataset, you need to extract both train and val archive for COCO in [./data/coco](./data/coco) 

You can also modify the list file in ./data as you like. Each line in the list file follows the following format:
```
image_name label_represented_by_0_and_1
```
## Compiling
The compiling process is the same as caffe. You can refer to Caffe installation instructions [here](http://caffe.berkeleyvision.org/installation.html).

## Training
You can train the model for each dataset using the followling command.
```
dataset_name = imagenet, nuswide_81 or coco
./build/tools/caffe train -solver models/train/dataset_name/solver.prototxt -weights ./models/bvlc_reference_caffenet/bvlc_reference_caffenet.caffemodel -gpu gpu_id
```
For more instructions about training and parameter setting, see the instructions in the [training directory](./models/train).

## Evaluation
You can evaluate the Mean Average Precision(MAP) result on each dataset using the followling command.
```
dataset_name = imagenet, nuswide_81 or coco
python models/predict/dataset_name/predict_parallel.py --gpu gpu_id --model_path your_caffemodel_path --save_path the_path_to_save_your_code
```
For more instructions about training and parameter setting, see the instructions in the [predicting directory](./models/predict).

## Citation
If you use this code for your research, please consider citing:
```
@article{cao2017hashnet,
  title={HashNet: Deep Learning to Hash by Continuation},
  author={Cao, Zhangjie and Long, Mingsheng and Wang, Jianmin and Yu, Philip S},
  journal={arXiv preprint arXiv:1702.00758},
  year={2017}
}
```

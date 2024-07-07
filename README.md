# Pytorch Medical Segmentation

## Requirements
* pytorch1.7
* torchio<=0.18.20
* python>=3.6

## Notice
* You can modify **hparam.py** to determine whether 2D or 3D segmentation and whether multicategorization is possible.
* We provide algorithms for almost all 2D and 3D segmentation.
* This repository is compatible with almost all medical data formats(e.g. nii.gz, nii, mhd, nrrd, ...), by modifying **fold_arch** in **hparam.py** of the config. 
* **Convert both the source and label images to the same type, where labels are marked with 1, not 255.**
* **For multi-category**, modify the corresponding codes for your specific categories.
* Whether in 2D or 3D, this project is processed using **patch**. Therefore, images do not have to be strictly the same size. In 2D, however, you should set the patch large enough.

## Prepare Your Dataset
### Example1

- **hparam.py:**
  - fold_arch: \*.mhd

```
source_dataset
├── source_1.mhd
├── source_2.mhd
└── ...
```

label dataset:
```
label_dataset
├── label_1.mhd
├── label_2.mhd
└── ...
```

### Example2

- **hparam.py:**
  - fold_arch: \*/\*.mhd

```
source_dataset
├── 1
    ├── source_1.mhd
├── 2
    ├── source_2.mhd
└── ...
```

label dataset:
```
label_dataset
├── 1
    ├── label_1.mhd
├── 2
    ├── label_2.mhd
└── ...
```



## Training
* without pretrained-model
```
set hparam.train_or_test to 'train'
python main.py
```
* with pretrained-model
```
set hparam.train_or_test to 'train'
python main.py -k True
```
  
## Inference
* testing
```
set hparam.train_or_test to 'test'
python main.py
```

## Examples
![](https://ellis.oss-cn-beijing.aliyuncs.com/img/20210108185333.png)
![](https://ellis.oss-cn-beijing.aliyuncs.com/img/2021-02-06%2022-40-07%20%E7%9A%84%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE.png)

## Tutorials
* https://www.bilibili.com/video/BV1gp4y1H7kq/

## Done
### Network
* 2D
- [x] unet
- [x] unet++
- [x] miniseg
- [x] segnet
- [x] pspnet
- [x] highresnet(copy from https://github.com/fepegar/highresnet, Thank you to [fepegar](https://github.com/fepegar) for your generosity!)
- [x] deeplab
- [x] fcn
* 3D
- [x] unet3d
- [x] residual-unet3d
- [x] densevoxelnet3d
- [x] fcn3d
- [x] vnet3d
- [x] highresnert(copy from https://github.com/fepegar/highresnet, Thank you to [fepegar](https://github.com/fepegar) for your generosity!)
- [x] densenet3d
- [x] unetr (copy from https://github.com/tamasino52/UNETR)

### Metric
- [x] metrics.py to evaluate your results

## TODO
- [ ] dataset
- [ ] benchmark
- [ ] nnunet

## By The Way
This project is not perfect and there are still many problems. If you are using this project and would like to give the author some feedbacks, you can send [Me](elliszkn@163.com) an email.

## Acknowledgements
This repository is an unoffical PyTorch implementation of Medical segmentation in 3D and 2D and highly based on [MedicalZooPytorch](https://github.com/black0017/MedicalZooPytorch) and [torchio](https://github.com/fepegar/torchio). Thank you for the above repo. The project is done with the supervisions of [Prof. Ruoxiu Xiao](http://enscce.ustb.edu.cn/Teach/TeacherList/2020-10-16/114.html), [Prof. Shuang Song](ssong@ustb.edu.cn) and [Dr. Cheng Chen](b20170310@xs.ustb.edu.cn). Thank you to [Youming Zhang](zhangym0820@csu.edu.cn), [Daiheng Gao](https://github.com/tomguluson92), [Jie Zhang](jpeter.zhang@connect.polyu.hk), [Xing Tao](kakatao@foxmail.com), [Weili Jiang](1379252229@qq.com) and [Shanshan Li](https://github.com/ssli23) for all the help I received.


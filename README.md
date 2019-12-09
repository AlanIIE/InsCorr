# InsCorr

Code for [Self-supervised Learning of Visual Correspondence via Instance Discrimination]. The code is developed based on the [PyTorch](https://pytorch.org/) framework. 

## Model and Result
<p float="left">
  <img src="figures/1.gif" width="50%" />
  <img src="figures/2.gif" width="50%" />
</p>

Our trained model can be downloaded from [here](https://drive.google.com/open?id=1choamF305CCheAGqtl4zBC1Hwn4oq2xn). The tracking performance on DAVIS-2017 for this model (without training on DAVIS-2017) is:

| J_mean | J_recall | J_decay | F_mean | F_recall | F_decay |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 0.560 | 0.669 | 0.012 | 0.577 | 0.685 | 0.059 |

## Dataset Preparation

Please read [`DATASET.md`](DATASET.md) for downloading and preparing the VLOG dataset for training and DAVIS dataset and JHMDB dataset for testing.

## Training
Replace the input list in train.py in the home folder as:
```Shell
    params['filelist'] = 'YOUR_DATASET_FOLDER/vlog_frames_12fps.txt'
```
Then run the following code:
```Shell
    python3 train.py  --checkpoint ./pytorch_checkpoints/release
```

## Testing
Replace the input list in test_davis.py in the home folder as:
```Shell
    params['filelist'] = 'YOUR_DATASET_FOLDER/davis/DAVIS/vallist.txt'
```
Set up the dataset path YOUR_DATASET_FOLDER in run_test*.sh . Then run the testing and evaluation code together:
```Shell
    sh run_test_davis.sh
```

```Shell
    sh run_test_davis_texture.sh
```

```Shell
    sh run_test_PCK.sh
```


## Acknowledgements
[TimeCycle](https://github.com/xiaolonw/TimeCycle) by Xiaolong Wang and Allan Jabri and Alexei A. Efros.

[SFNet](https://github.com/cvlab-yonsei/projects/blob/master/SFNet/codes/model.py) by Lee, Junghyup and Kim, Dohyung and Ponce, Jean and Ham, Bumsub.

[PCGAN](https://github.com/AlanIIE/PCGAN) by Dong Liang, Rui Wang, Xiaowei Tian, Cong Zou.


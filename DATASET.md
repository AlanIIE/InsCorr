# Dataset Preparation

## Training Dataset

We train our model on the [VLOG Dataset](http://web.eecs.umich.edu/~fouhey//2017/VLOG/). We use the official release of the videos, the files are named as "block_x.tar" (0<=x<=4). We assume the videos are downloaded on the path: YOUR_DATASET_FOLDER/vlog/.

Download the list for the videos [data_v1.1.tgz](http://web.eecs.umich.edu/~fouhey//2017/VLOG/data/data_v1.1.tgz). Extract the list "manifest.txt" to the same folder: YOUR_DATASET_FOLDER.

Go into the folder:
```Shell
    cd preprocess
```
Change the video path in preprocess/downscale_video_joblib.py. Reduce the video size and save it to YOUR_DATASET_FOLDER/vlog_256/ :
```Shell
    python downscale_video_joblib.py
```
Extract the jpgs to YOUR_DATASET_FOLDER/vlog_frames_12fps/ by using:
```Shell
    python extract_jpegs_256.py
```
Gnerate the jpg list to YOUR_DATASET_FOLDER/vlog_frames_12fps.txt for training:
```Shell
    python genvloglist.py
```

## Testing Dataset
* DAVIS2017

Download [DAVIS 2017](https://davischallenge.org/davis2017/code.html) dataset on the path: YOUR_DATASET_FOLDER/davis/ . Clone the [evaluation code for DAVIS 2017](https://github.com/davisvideochallenge/davis-2017) to YOUR_DATASET_FOLDER/davis-2017/ .

Go into the folder:
```Shell
    cd preprocess
```
Generate the groundtruth and the list for testing as YOUR_DATASET_FOLDER/davis/DAVIS/strip_vallist.txt of the texture propagation task:
```Shell
    python genstripe.py -d YOUR_DATASET_FOLDER/davis/
```
Generate the list for instance segmentation testing as YOUR_DATASET_FOLDER/davis/DAVIS/vallist.txt:
```Shell
    python gendavis_vallist.py -d YOUR_DATASET_FOLDER/davis/
```
<!-- Replace the input list in test_davis.py in the home folder as:
```Shell
    params['filelist'] = 'YOUR_DATASET_FOLDER/davis/DAVIS/vallist.txt'
``` -->

* JHMDB
Download [JHMDB](http://jhmdb.is.tue.mpg.de/) dataset (joint_ositions.zip, puppet_mask.zip, Rename_images.tar.gz, splits.zip) and extract them on the path YOUR_DATSET_FOLDER/JHMDB/. 

   ```
   ./JHMDB
   ├── joint_positions
   │   └──├── brush_hair
   │      ├── catch
   │      ├── clap
   │      ├── climb_stairs
   │      ├── golf
   │      ├── ...
   │      └── wave
   ├── puppet_mask
   │   └── ........... same as joint_positions
   ├── Rename_Images
   │   └── ........... same as joint_positions
   └── splits
       └──├── brush_hair_test_split1.txt
          ├── brush_hair_test_split2.txt
          ├── brush_hair_test_split3.txt
          ├── catch_test_split1.txt
          ├── ...
          └── wave_test_split3.txt
   ```
   
Go into the folder:
```Shell
    cd preprocess
```

Generate the list for testing as YOUR_DATASET_FOLDER/JHMDB/vallist.txt:
```Shell
    python genJHMDB_vallist.py -d YOUR_DATASET_FOLDER/JHMDB/
```
   
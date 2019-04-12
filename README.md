## Attention 
This is a copy branch from https://github.com/lichengunc/refer.

Compared to [old verison](https://github.com/lichengunc/refer.), this branch is extended to python3.x.

## Note
This API is able to load all 4 referring expression datasets, i.e., RefClef, RefCOCO, RefCOCO+ and RefCOCOg. 
They are with different train/val/test split by UNC, Google and UC Berkeley respectively. We provide all kinds of splits here.
<table width="100%">
<tr>
<td><img src="http://bvisionweb1.cs.unc.edu/licheng/referit/refer_example.jpg", alt="Mountain View" width="95%"></td>
</tr>
</table>

## Citation
If you used the following three datasets RefClef, RefCOCO and RefCOCO+ that were collected by UNC, please consider cite our EMNLP2014 paper; if you want to compare with our recent results, please check our ECCV2016 paper.
```bash
Kazemzadeh, Sahar, et al. "ReferItGame: Referring to Objects in Photographs of Natural Scenes." EMNLP 2014.
Yu, Licheng, et al. "Modeling Context in Referring Expressions." ECCV 2016.
```

## Prerequistes
+ skimage
+ matplotlib
+ numpy


## Compile

### COCO

```bash
git clone https://github.com/cocodataset/cocoapi.git ./coco

cd ./coco/PythonAPI

make 
```

### Refer 

```bash
make 
```

## Prepare Data 

### data directory structure
```
$DATA_PATH
├── images
│   ├── mscoco
│       └── train2014
|       └── val2014
|       └── test2014
├── refcoco
│   ├── instances.json
│   ├── refs(google).p
│   └── refs(unc).p
├── refcoco+
│   ├── instances.json
│   └── refs(unc).p
├── refcocog
│   ├── instances.json
│   └── refs(google).p
└── refclef
   	├── instances.json
  	├── refs(unc).p
	└── refs(berkeley).p
```

### Download
Download the cleaned data and extract them into "data" folder
- 1) http://bvisionweb1.cs.unc.edu/licheng/referit/data/refclef.zip
- 2) http://bvisionweb1.cs.unc.edu/licheng/referit/data/refcoco.zip
- 3) http://bvisionweb1.cs.unc.edu/licheng/referit/data/refcoco+.zip 
- 4) http://bvisionweb1.cs.unc.edu/licheng/referit/data/refcocog.zip 

Download coco dataset(http://cocodataset.org/#download)

## How to use
The "refer.py" is able to load all 4 datasets with different kinds of data split by UNC, Google, UMD and UC Berkeley.
**Note for RefCOCOg, we suggest use UMD's split which has train/val/test splits and there is no overlap of images between different split.**
```bash
# locate your own data_root, and choose the dataset_splitBy you want to use
refer = REFER(data_root, dataset='refclef',  splitBy='unc')
refer = REFER(data_root, dataset='refclef',  splitBy='berkeley') # 2 train and 1 test images missed
refer = REFER(data_root, dataset='refcoco',  splitBy='unc')
refer = REFER(data_root, dataset='refcoco',  splitBy='google')
refer = REFER(data_root, dataset='refcoco+', splitBy='unc')
refer = REFER(data_root, dataset='refcocog', splitBy='google')   # test split not released yet
refer = REFER(data_root, dataset='refcocog', splitBy='umd')      # Recommended, including train/val/test
```

<!-- refs(dataset).p contains list of refs, where each ref is
{ref_id, ann_id, category_id, file_name, image_id, sent_ids, sentences}
ignore filename

Each sentences is a list of sent
{arw, sent, sent_id, tokens}
 -->
 
 **It worth noting that the value of  data_root should be the $DATA_PATH.**

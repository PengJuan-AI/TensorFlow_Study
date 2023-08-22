# Models trained

| Model Name | Description | Dataset |
| -------- | ------------------ | -------- | 
| 101_food_classes_10_pct_data_fine_tuned_last.zip | EfficientNetB0 trained and fine-tuned on 10% of food101 datasets | [10pct_food101](https://storage.googleapis.com/ztm_tf_course/food_vision/101_food_classes_10_percent.zip) |
| Food101_feature_extraction.zip | EfficientNetB0 feature extraction on full food101 datasets | [TFDS_Food101](https://www.tensorflow.org/datasets/catalog/food101)|
| All_food101_efficientnetb0_fine_tune.zip | ZTM trained EfficientNetB0 fine_tuned on full food101 datasets | [TFDS_Food101](https://www.tensorflow.org/datasets/catalog/food101)|
| all_food101_efficientnetb0_fine_tune_self.zip | self-trained EfficientNetB0 fine_tuned on full food101 datasets | [TFDS_Food101](https://www.tensorflow.org/datasets/catalog/food101) |

## How to use?

### Download datasets
For proportional food101 dataset, copy the link and paste the following code on your notebook (recommended)
```python
!wget model_URL

# upzip the data
def unzip_data(filename):
  """
  Unzips filename into the current working directory.

  Args:
    filename (str): a filepath to a target zip folder to be unzipped.
  """
  zip_ref = zipfile.ZipFile(filename, "r")
  zip_ref.extractall()
  zip_ref.close()

unzip(filename)
```

For TDFS Food101 datasets
```python
# Get Tensorflow Datasets
import tensorflow_datasets as tfds

# TFDS allows you to use the datasets for modelling directly
# Load in the data
(train_data, test_data), ds_info = tfds.load(name="food101",
                                             split=["train", "validation"],
                                             shuffle_files=True,
                                             as_supervised=True, # we want label and data
                                             with_info=True)# download the metadata as well
```
More details, see: https://www.tensorflow.org/datasets/catalog/food101

## Dowload model
```python
loaded_model = tf.keras.models.load_model(model_name)
...
```

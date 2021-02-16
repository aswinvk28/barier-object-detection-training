## Barrier / Gate Detection

### Training

Clone the research models repository of tensorflow

```bash

git clone https:/github.com/tensorflow/models

cd models/research/object_detection/

```

**Install models directory on to your root project folder**

**OR**


```bash

docker-compose up -d build

```

__Training the Dataset using tensorflow__

```bash

python model_main_tf2.py -- \
  --model_dir=$MODEL_DIR --num_train_steps=$NUM_TRAIN_STEPS \
  --sample_1_of_n_eval_examples=$SAMPLE_1_OF_N_EVAL_EXAMPLES \
  --pipeline_config_path=$PIPELINE_CONFIG_PATH \
  --alsologtostderr

```

__Create Pipeline Config__

```python

from object_detection.utils import config_util

config_util.get_configs_from_pipeline_file(pipeline_config_path='<dirname>')

```

__Create Dataset of Barrier Images__

```bash

cd bing_image_downloader/

python setup.py install

```

```python

from bing_image_downloader import downloader
downloader.download(query_string, limit=100,  output_dir='dataset', adult_filter_off=True, force_replace=False, timeout=60)

```

#### Download existing MSCOCO Dataset

```bash

cd /home/tensorflow/models/research/object_detection/dataset_tools/ bash ./download_and_preprocess_mscoco.sh /home/tensorflow/output_dir

```

__Image Annotation__

**CVAT (Computer Vision Annotation Toolkit) does the Image Annotation on training data. Training data of barrier images consists of some hundreds of images.**


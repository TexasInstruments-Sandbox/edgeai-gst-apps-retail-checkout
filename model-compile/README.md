# Model compilation with tidlrunner

The model here was compiled with [tidlrunner](https://github.com/TexasInstruments/edgeai-tidlrunner) using the following command: 

```bash
tidlrunner-cli compile --config_path ./data/models//vision/detection/coco/edgeai-mmdet/food-rec-demo/food_recognition_mobilenetv2_lite_512x512_20201214_model_config.yaml --target_device AM62A
```

This uses the model_config YAML in this directory, and will assume that the food-model.onnx and the .prototxt file are in the same directory as said YAML. 

This also assumes that there are images from the food-recognition model's training dataset available in edgeai_tidlrunner/data/datasets/vision/food-rec/images. 

This will take several minutes to complete compilation using the default settings. 


There was one manual fix required in the resulting model-artifacts/onnxrtMetaData.txt, where the last line describing the output model names needed to be modified from: 

`0:outDataNames=labels,dets`

to 

`0:outDataNames=dets,labels`

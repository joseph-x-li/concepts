# Using YOLOv4 Detector

1) Create a folder called ```weights``` in the base of the repo (it is gitignored). 

2) Download weights from https://drive.google.com/file/d/1cewMfusmPjYWbrnuJRuKhPMwRe_b9PaT/view and place into ```weights``` folder.

3) Create an ONNX model from the weights:  
```python demo_darknet2onnx.py cfg/yolov4.cfg ../weights/yolov4.weights data/dog.jpg <<BATCHSIZE>>```  
   - You can specify ```<<BATCHSIZE>>``` based on your computer hardware capabilities.  
   - Set ```<<BATCHSIZE>>``` to ```-1``` for dynamic batch sizes.  
   - The generated ONNX model is called ```yolov4_<<BATCHSIZE>>_3_608_608_dynamic.onnx```

4) The previous command generates a test prediction that you can delete with ```rm predictions_onnx.jpg```

5) Use ```mv yolov4_<<BATCHSIZE>>_3_608_608_dynamic.onnx ../weights``` to store the weights for save keeping.

6) In ```demo_darknet2onnx.py```, the ```detect``` function can be used to generate outputs using the ONNX model.

7) If your computer has an NVIDIA GPU, you can convert the ONNX model to a TensorRT model, which I currently do not have, so I have not written the HOW-TO for this.

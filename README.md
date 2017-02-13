# Convolutional Neural Network Techniques
Comparison analysis of 11 convolutional neural networks usingTensorFlow on the CIFAR-10 dataset. I explored each of the six techniques (Max Pooling, Local Response Normalization, Batch Normalization, Dropout, and Data Augmentation) to see its effect on the test accuracy and training time.

Theoretical and practical details are documented in the report (https://github.com/kumikokashii/cnn_techniques/blob/master/theory_and_practice_of_cnn_techniques.pdf).

## Data
I downloaded the data from https://www.cs.toronto.edu/~kriz/cifar.html.

## Results
Model | Model Description | Learning Rate | Test Accuracy (%) | Time Till Best (hr) | Steps Till Best | Average Time Per Step (sec)
:---:| --- | ---:| ---:|---:| ---:|---:
01 | Basic | 0.01 | 54.82 | 0.8 | 47,400 | 0.058
02 | 01 + Max Pooling | 0.01 | 74.07 | 1.0 | 64,500 | 0.058
03 | 02 + Local Response Normalization | 0.01 | 74.51 | 1.2 | 67,700 | 0.062
04 | 03 + Batch Normalization | 0.01 | 77.15 | 0.2 | 8,500 | 0.098
04 | 03 + Batch Normalization | 0.10 | 80.20 | 0.3 | 14,600 | 0.077
05 | 04 + Dropout | 0.10 | 82.62 | 0.5 | 28,500 | 0.069
06 | 05 + No Resize Data Augmentation | 0.10 | 86.17 | 6.6 | 230,100 | 0.104
07A | 06 + Crop | 0.10 | 86.90 | 23.6 | 618,900 | 0.137
07B | 07A + Last Max Pooling Stride = 1 | 0.10 | 87.05 | 24.8 | 692,600 | 0.129
08 | 06 + Enlarge + One More Convolutional Layer | 0.10 | 86.15 | 2.5 | 43,200 | 0.204
09 | 08 + Crop + Last Max Pooling Stride = 1 | 0.10 | 88.16 | 6.0 | 111,200 | 0.193

Notes:<br />
1) During a training, a validation accuracy is recorded in a log every 100 steps.<br />
2) Average validation accuracy is an average of the 8 most recent validation accuracies recorded in the log.<br />
3) Test accuracy is determined by the best model i.e. the model with the highest average validation accuracy.<br />
4) Training for Model 07A and 07B were terminated after about 24 hours even though the average validation accuracy was still increasing, but only slightly.<br />
5) All models were trained and tested with a GPU, [NVIDIA Titan X Pascal&trade;](https://www.nvidia.com/en-us/geforce/products/10series/titan-x-pascal/).<br />
6) All models were trained and tested with [TensorFlow&trade;](https://www.tensorflow.org/).

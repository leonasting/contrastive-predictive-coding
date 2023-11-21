# File: Data_utils.py
It has 5 classes as follows:
1. Mnisthandler
2.MnistGenerator
3.SortedNumberGenerator
4.SameNumberGenerator
5. PlotSequence

## SortedNumberGenerator
Data generator providing lists of sorted numbers.
This is most important function that is generative terms and predictive terms which are numbers. 
Positive samples are present in sequence and Negative sample are not in sequence.
Example of Positive sample:
Terms 3,4,5,6
Predictive Terms 7,8,9,0

Numbers range from 0-10 and sequence can start from any number.

Example of Negative sample:
Terms 3,4,5,6
Predictive Terms 9,4,3,2[ any number which is not in sequence] 

All the generated iamges have random image background and digit shape in some rnadom font in dark shade.



### Initialization
Initialization Function parameters:
- batch_size
-  subset
-  terms
-  positive_samples=1
-  predict_terms=1
-  image_size=28
-  color=False
-  rescale=True 

Working :
Creates instance MnistHandler class.
Calls get_n_samples(input:subset_count) // input:term_value
Dividest the sample in batches based on input: batch_size

###  Step Function

Based on bkackbox ussage:
1. Provides 2 output. 
	1.  Two batch of 32 sized with terms (4 )training and predict terms (6) both of which are 64*64 *3 RGB image.
	2. Label ??

#  Train_model.py
It has 1 classand 5 function as follows:
1.  CPC layer Class
2.  Network Encoder Function
3.  Network Autoregressive 
4.  Netwrork Prediction
5.  Network CPC
6.  Train Model

## Network Encoder
It contains the first architecture of consuming the image data and provide linear embedding of size provided by code_size.

It has following layers:
```
x = keras.layers.Conv2D(filters=64, kernel_size=3, strides=2, activation='linear')(x)
x = keras.layers.BatchNormalization()(x)
x = keras.layers.LeakyReLU()(x)
x = keras.layers.Conv2D(filters=64, kernel_size=3, strides=2, activation='linear')(x)
x = keras.layers.BatchNormalization()(x)
x = keras.layers.LeakyReLU()(x)
x = keras.layers.Conv2D(filters=64, kernel_size=3, strides=2, activation='linear')(x)
x = keras.layers.BatchNormalization()(x)
x = keras.layers.LeakyReLU()(x)
x = keras.layers.Conv2D(filters=64, kernel_size=3, strides=2, activation='linear')(x)
x = keras.layers.BatchNormalization()(x)
x = keras.layers.LeakyReLU()(x)
x = keras.layers.Flatten()(x)
x = keras.layers.Dense(units=256, activation='linear')(x)
x = keras.layers.BatchNormalization()(x)
x = keras.layers.LeakyReLU()(x)
x = keras.layers.Dense(units=code_size, activation='linear', name='encoder_embedding')(x)
```




## Network Autoregressive
```
x = keras.layers.GRU(units=256, return_sequences=False, name='ar_context')(x)
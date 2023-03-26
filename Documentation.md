# File: Data_utils.py
It has 5 classes as follows:
1. Mnisthandler
2.MnistGenerator
3.SortedNumberGenerator
4.SameNumberGenerator
5. PlotSequence

## SortedNumberGenerator
Data generator providing lists of sorted numbers.

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
It has 1 and 5 function as follows:
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
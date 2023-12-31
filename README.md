# Physical-Activity-Recognition
This GitHub Respo is a condensed version of my MSc Data Analytics dissertation project *'Investigating Deep Learning Techniques for Physical Activity Recognition Using Cost-Effective Wearable Devices'*. For reference, this project was awarded a distinction.

**Abstract -** *Applications of physical activity recognition (PAR) have gained lots of attention in recent years due to the modern advancements of wearable smart devices giving deep learning techniques the platform to perform activity recognition well. The automated feature learning boasted by state-of-the-art deep learning techniques enables them to execute robust real-time activity recognition within smart devices using the wealth of sensor data they generate. The current popularity of activity recognition has stemmed from its pertinence in health-related fields, providing an economical approach to monitoring people’s everyday movements. In this paper, an investigation of modern PAR is conducted. This includes assessing the implications of cost-effective and wearable activity recognition and exploring areas of the field where standardisation has the potential to be enhanced. In particular, a Convolutional Neural Network (CNN) is tested on three diverse publically available wearable sensor datasets, greatly differing in features, using a variety of sample generation parameter configurations. From this, the effect of the sample generation process across datasets with a range of features is evaluated. The results show that an inappropriate sample generation process can significantly inhibit PAR performance, with datasets containing extensive features proving more sensitive to its sample generation parameters. Hence, patterns present in the results indicate standardisation can be introduced into the sample generation process from wearable sensor data to maximise performance. So, when the CNN model is tested using optimal sample generation parameters, the results outperform a recent benchmark PAR study for one of the experimental datasets. At the end of this paper, standardisations within the features of wearable sensor datasets and the sample generation process are inferred using the distribution of the results obtained.*

If this project is of particular interest to you, please email @murtoncal@gmail.com to see the full paper. 
## Datasets
UCI_HAR - https://archive.ics.uci.edu/dataset/240/human+activity+recognition+using+smartphones <br />
USC_HAD - https://sipi.usc.edu/had/ <br />
UTD_MHAD - https://personal.utdallas.edu/~kehtar/UTD-MHAD.html
## Python Libraries
Pandas, Numpy, Matplotlib, Keras, Seaborn, Scikit-Learn and PyTorch.
## File Structure
There are four files detailing all the code written for this project. One data preprocessing file. Three experimental files (one for each dataset).
## Project Overview
### ML Pipeline
A machine learning pipeline is an end-to-end graph designed to streamline machine learning workflows. The deep learning pipeline for each experiment in this study can be seen below.

<p align="center">
<img src="/images/Pipeline.png" width="150" align="center"/>
</p>

### Data Preprocessing
Three datasets of varying features were chosen to apply a CNN model and perform PAR. The data contained within each dataset are the raw triaxial sensor readings of an accelerometer and a gyroscope, where the different positions of the sensors replicate the likely positions of a smart device on a user in a free-living environment. The table below shows the characteristics of each dataset.

<p align="center">
<img src="/images/Diss_data_table.png" width="600" align="center"/>
</p>

The preprocessing procedure of each of the three datasets is slightly different due to minor variations in their raw data. The first variation is within the UCI-HAR dataset, as its activities were performed one after another during the data collection process, unlike the other two datasets, with their activities recorded disconnected from one another. The second variation is within the USC-HAD dataset due to its larger sampling frequency than the two other datasets.

Each set of continuous strings of triaxial accelerometer and gyroscope sensor readings form an activity graph, split into sliding windows with a defined window length and overlap between the windows. Please refer to the figure below.

<p align="center">
<img src="/images/slide.png" width="480" align="center"/>
</p>

Further preprocessing stages include a data noise reduction filter, data normalisation, and one-hot encoding of the activity labels.


### CNN Model

The CNN model comprises of two 2D convolutional layers with convolutional and max pooling stages. These then connect to a fully connected layer and a soft-max classifier to make activity recognition predictions. The following function creates this CNN model in Python, using the Keras library imported from TensorFlow.

```
# creating model
def CNN(X_train, y_train, filters):
    # no. of activities for the units of the final fully connected layer
    no_activities = len(np.unique(y_train))
    # enables the stacking of layers into a model 
    model = Sequential()
    # stacking layers
    # first convolution
    model.add(Conv2D(filters=filters, kernel_size=(5,5),padding='same',input_shape=X_train.shape[1:], activation='relu'))
    # max pooling of size 2
    model.add(MaxPooling2D(2,2))
    # second convolution, filter size is doubled
    model.add(Conv2D(filters=filters*2,kernel_size=(3,3),padding='same',activation='relu'))
    # max pooling of size 2
    model.add(MaxPooling2D(2,2))
    # flattern the data
    model.add(Flatten())
    # fully connected layers
    model.add(Dense(units=100,activation='relu'))
    model.add(Dense(units=no_activities, activation='softmax'))
    # summarises the model
    model.summary()
    # compliing the model defines the loss function, optimiser and the metrics
    model.compile(optimizer='adam', loss = 'categorical_crossentropy', metrics=['accuracy'])
    # returns the CNN model
    return model
```

### Findings

The results of each experiment in this project can be seen below. The chosen evaluation metrics for activity recognition performance are F-measure and computational cost. Various sample generation parameters were used to investigate their importance for activity recognition.

<p align="center">
<img src="/images/diss_results.png" width="575" align="center"/>
</p>

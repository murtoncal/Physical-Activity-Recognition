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
Three datasets of varying features were chosen to apply a CNN model and perform PAR. The data contained within each dataset are the raw triaxial sensor readings of an accelerometer and a gyroscope, where the different positions of the sensors seen in the table below replicate the likely positions of a smart device on a user in a free-living environment.

![alt text](https://github.com/murtoncal/Physical-Activity-Recognition/images/Diss_data_table.png?raw=true)

where CNN-based feature extraction is performed to classify the desired physical activities and critical analysis is conducted to assess the impacts of various sample generation parameters and features of each dataset.

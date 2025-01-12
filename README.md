<h1>
The Inertial Sensor Signals Processing
</h1>

- this project is based on [*Smartphone-Based Recognition of Human Activities and Postural Transitions Data Set*](http://archive.ics.uci.edu/ml/datasets/smartphone-based+recognition+of+human+activities+and+postural+transitions) :point_left: all descriptions are here
- includes the use of csv files, data processing algorithms, windowing, time and frequency signals, data visualisation
- final data is ready to use in *Neural Network Models*
- the project is focused on the classification of 6 activities: 3 dynamic like walking, walking upstairs, walking downstairs, and 3 static like standing, sitting, laying
- data was registered by sensors from smartphone


- language: Python 3.10.1
- main libraries: TensorFlow, Keras, Matplotlib, Seaborn, Pandas, Numpy
- computing platform: Jupyter Notebook

<h2>
More about the project:
</h2>

Stages of this data processing project:

**1. Opening .csv files and putting all signal samples and labels into DataFrames**

**2. Raw signals visualisation**

**3. Noise reduction and extraction of time signals components:**

- *median_filter()* - median filter
- *butterworth3rd()* - low-pass 3rd order Butterowrth filter to reduce noises above 20 Hz
- *butterworth()* - high-pass filter to separate body and gravity components from the total acc. signals (cutoff - 0.3 Hz)
- *jerk_signal()* - the jerk signal (da/dt) where: da = d(signal) and dt=1/fs
- *magnitude()* - the euclidean magnitude for 3 axes signals

**4. Windowing (fixed-width sliding windows)**

- Windowing the signal with a span of 2.56 sec (2.56sec × 50Hz = 128 cycles) and an overlap of 50%
- **Each window has 128 elements**
- As a result, 10399 samples were obtained

**5. Converting the time signals to frequency singals**

**6. Measures for computing feature vectors**

Feature extraction from signals to prepare the data for the Neural Network - **summary 481 signals features**.

- *mean_f()* - arithmetic mean
- *std_f()* - standard deviation
- *mad_f()* - median absolute deviation
- *min_f()* - lowest value 
- *max_f()* - largest value
- *energy_f()* - average sum of the squares
- *iqr_f()* - interquartile range
- *ropy_f()* - signal entropy
- *sma_f()* - signal magnitude area
- *corr_axis()* - Pearson correlation coefficient (just 3 axes time signals)
- *maxFreqInd()* - largest frequency component (just freq. signals)
- *meanFreq()* - frequency signal weighted average (just freq. signals)
- *skewness()* - frequency signal Skewness (just freq. signals)
- *kurtosiss()* - frequency signal Kurtosis (just freq. signals)
- *energyBands()* - spectral energy of a frequency band (just 3 axes freq. signals)
- *angle_features()* - angle between to vectors 

**7. Results**

**General Data**

<img src="https://github.com/mkowalsky97/Acc_Gyro_Signals_Processing/blob/main/images/g_data.png" width="400px">

- :white_check_mark: after signal processing it's 481 features for each window
- :white_check_mark: it's 10399 samples which are useful to train and test cnn 
- :white_check_mark: features are saved in the file: 'global_data.csv'
- :white_check_mark: labels for each window are saved the file: 'global_labels.csv'
- :white_check_mark: this database is ready to use in *Neural Networks Models*

## Usage
1. Clone the repository:
   ```bash
   git clone <https://github.com/mivhvl/HAR_signals.git>
   ```
2. Open and run the Jupyter Notebook:
   ```bash
   jupyter notebook

## Structure
- `RawData/`: Raw Signals
- `GlobalData/`: Global Dataset
- `SignalProcessing.ipynb`: Notebook

## License
Licensed under the MIT License.











Hurricane-detection
 
We have reuploaded the project now, sorry for the delay 

This project is open for all contributer as it is a big project and shall add value to your profiles, we are making it for a problem statement given by NHC
 
Also please star the repo if you like the project
 
A machine learning algorithm to forecast the intensity and trajectory of Atlantic tropical storms




Background
The National Hurricane Center (NHC) and National Oceanic and Atmospheric Administration (NOAA) provide predictions for storms trajectories, intensity, and size. They create these predictions based on models that can be classified into 3 groups: dynamical, statistical, and ensemble [1]. The most accurate models are based on computational fluid dynamics and achieve more precision than their statistical and ensemble counterparts [1][4]. The current statistical
 
models (OCD5) are based on multiple regression methods that can explain a significant amount of variance [1]. In this project, we research and implement the domain of machine learning and deep learning into predictive hurricane models for both trajectory and intensity and evaluate them against the NHC standards. Previous research into machine learning to forecast tropical Atlantic storms include a sparse recurrent neural network (Kordmahalleh, Sefidmazgi, & Homaifar, 2016) and an artificial neural network (Jung & Das, 2013); both achieved favorable results. The hurricane models created can be utilized to develop more precise emergency planning. There is a necessity for more accurate and timely models that can help reduce the amount of loss caused by hurricanes.

Problem
The NOAA and NHC have several different classifications for Atlantic hurricane models that describe feature prediction and model architecture. The 3 main classifications for hurricane model architecture include dynamical, statistical, and ensemble. Classifications also include relative compute time required to create an output grouped as either early or late and forecast parameters such as trajectory, intensity, and wind radii. The most accurate models are late models that take upwards of 6 hours to produce an output whereas models that can produce an output in seconds to minutes are called early. Early models tend to be statistical which include the baseline model for trajectory named CLIPER5 Climatology and Persistence (CLP5) utilizing multivariate regression. The performance for these methods can be augmented by incorporating more advanced statistical methods from deep learning such as recurrent neural networks.
Kordmahalleh et al., 2016 created a sparse recurrent neural network augmented by a genetic
algorithm but there are factors requiring improvement. The training set utilized an older version of the NHC Hurricane Database format known as HURDAT while a new format has been released called HURDAT2 with additional information on wind radii. Kordmahalleh et al., 2016 also utilized benchmarks different from the standard applied within the NHC. Other than improving their methodology, we can expand the scope by creating separate models for both intensity and trajectory. These models can be used to predict the trajectory and intensity for future Atlantic storms.

Datasets
The following datasets and inputs including their sources will be used to create machine learning models:

NHC Hurricane Database (HURDAT2) http://www.nhc.noaa.gov/data/#hurdat https://www.kaggle.com/noaa/hurricane-database

NHC Forecast Error Database http://www.nhc.noaa.gov/verification/verify7.shtml

NHC GIS : http://www.nhc.noaa.gov/gis/


In the future, the IBTrACS database will be used to extend the hurricane-ai to additional regions.
 
The NHC HURDAT2 database contains the tracking information for Atlantic tropical and subtropical cyclones which includes hurricanes and tropical storms from 1851 to 2016. The most updated version of the dataset is included on the noaa.gov site and includes 2 additional years of cyclone data compared to the data set available on Kaggle and is potentially more descriptive. To match the inputs of the baseline model used by the NHC, we are calculating the forward motion of the storm by applying a vector based on previous and current geographical location.


Table 1. This table contains the tentative features as input to the model


Name	Data Type	Description
Time	Date Time	The date and time of the measurement.
Latitude	Float	The geographical latitude of the storm eye to 1 decimal precision.
Longitude	Float	The geographical longitude of the storm eye to 1 decimal precision.
Maximum Winds	Integer	The maximum sustained winds within the storm.
Minimum Pressure	Integer	The minimum barometric pressure within the storm.

Forward Motion	String	Calculated vector of motion based on location in time series.
The Forecast Error Database contains information on the accuracy of predicted models from the NHC. The two model forecast errors available are labeled OFCL and BCD5. The OFCL is the official NHC forecast and the BCD5 is the real track available. This data set can be used to benchmark and evaluate the deep learning model. The NOAA and NHC also hosts a geographical information system (GIS) that contains raw and processed data on hurricanes. The server hosting the GIS is publicly accessible and can be used to evaluate our model by comparing the 2017 Atlantic tropical season. The preliminary best tracks can be found here before they are finalized and available in the HURDAT2 data set. With the GIS, we can construct a final evaluation data set.

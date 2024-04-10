# AutomatiData-Taxi-Fare-Forecast

## Introduction 

This project aims to develop a regression model to help estimate taxi cab fares prior to the ride, based on data that TLC has gathered. 
The TLC data comes from over 200,000 taxi and limousine licensees, making approximately one million combined trips per day. 
The final linear regression model performed with a R-squared coefficient of 0.84 with RMSE of 4.23. 
The feature which appeared to be most influential in determining the taxi fare amount was ride duration. 

## Business Understanding 
Providing Fare estimates upfront allows customers to plan and budget their trips more effectively. It enhances transparency and reduces uncertainty. Transparent pricing also builds trust between the taxi company and its customers. Furthermore, upfront price estimates can also allow the company to manage their resources more efficiently in terms of driver allocation. 

## Data understanding 
The project uses a dataset called 2017_Yellow_Taxi_Trip_Data.csv. The data is gathered by the New York City Taxi & Commission. In order to shorten runtimes, a sample of 408 thousand rows was drawn from the 113 million rows from the original dataset. Features include pickup times, trip_distance, fare_amount and more. 

## Data Dictionary 
| Column name             | Description                                                       |
|-------------------------|-------------------------------------------------------------------|
| ID                      | Trip identification number                                        |
| VendorID                | A code indicating the TPEP provider that provided the record.     <br> 1 = Creative Mobile Technologies, LLC <br> 2 = VeriFone Inc. |
| tpep_pickup_datetime    | The date and time when the meter was engaged.                    |
| tpep_dropoff_datetime   | The date and time when the meter was disengaged.                 |
| Passenger_count         | The number of passengers in the vehicle.                         <br> This is a driver-entered value. |
| Trip_distance           | The elapsed trip distance in miles reported by the taximeter.    |
| PULocationID            | TLC Taxi Zone in which the taximeter was engaged.                |
| DOLocationID            | TLC Taxi Zone in which the taximeter was disengaged.             |
| RateCodeID              | The final rate code in effect at the end of the trip.            <br> 1 = Standard rate <br> 2 = JFK <br> 3 = Newark <br> 4 = Nassau or Westchester <br> 5 = Negotiated fare <br> 6 = Group ride |
| Store_and_fwd_flag      | This flag indicates whether the trip record was held in vehicle memory before being sent to the vendor, aka “store and forward,” because the vehicle did not have a connection to the server. <br> Y = store and forward trip <br> N = not a store and forward trip |
| Payment_type            | A numeric code signifying how the passenger paid for the trip.  <br> 1 = Credit card <br> 2 = Cash <br> 3 = No charge <br> 4 = Dispute <br> 5 = Unknown <br> 6 = Voided trip |
| Fare_amount             | The time-and-distance fare calculated by the meter.             |
| Extra                   | Miscellaneous extras and surcharges.                             <br> Currently, this only includes the $0.50 and $1 rush hour and overnight charges. |
| MTA_tax                 | $0.50 MTA tax that is automatically triggered based on the metered rate in use. |
| Improvement_surcharge   | $0.30 improvement surcharge assessed trips at the flag drop. The improvement surcharge began being levied in 2015. |
| Tip_amount              | Tip amount – This field is automatically populated for credit card tips. Cash tips are not included. |
| Tolls_amount            | Total amount of all tolls paid in trip.                         |
| Total_amount            | The total amount charged to passengers. Does not include cash tips. |


## Modeling and Evaluation 
A Multiple Linear Regression (MLR) model was developed to estimate taxi cab fares based on trip distance and duration and time of day the ride took place.  

Prior to the model, a number of pre-processing steps and data transformations were applied to the original dataset. Pre-processing included checking for null values, duplicates and standardising data. Transformations included conbining pickup and dropoff time into a duration column, as well as engineering a rush_hour column to lable whether the ride occured during rush hour. 

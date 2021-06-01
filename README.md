# Testing APIs Data Collection

Under `Test Environment` the APIs use the following data collections:

## Air

- `Flight Inspiration Search` and `Flight Cheapest Date Search` contain the following [list of origin and destinations](data/flightsearch.md)

- `Flight Most Booked and Traveled Destinations` and `Flight Busiest Traveling Period` contain the following [list of origin and destinations](data/ti.md).

- `Flight Check-in Links` contains the following [valid airlines](data/checkinlinks.md).

- `Airport Nearest Relevant` & `Airport & City Search` contain data from United States, Spain, United Kingdom, Germany and India.

- `Airline Code Lookup` contains almost all airlines.

- `Flight Choice Prediction`, `Flight Delay Prediction` and `Airport On-time Performance` APIs have no data restrictions in test.

- `On Demand Flight Status` contains a copy of live data at a given time and real-time updates are not supported. Check out the [differences between test and production](data/ondemandflightstatus.md) environment. 

- `Flight Price Analysis` contains the following [routes](data/flightpriceanalysis.md) in both test and production environments. 

## Hotel

- The content of `Hotel Search` comes directly from the hotel providers, so the content might change dynamically. For your test, use big cities like `LON` (London) or `NYC` (New-York).

- The [following table](data/hotelchains.md) contains a list of valid hotel chains for `Hotel Search`.

- `Hotel Ratings` offers 24 hotels in the test environment: 10 in London and 14 in New-York. You can find the list [here](data/hotelratings.md).


## Destination Content

- `Points Of Interest`, `Safe Place`, `Tours & Activities` and `Location Score` APIs contain data for the [following cities](data/pois.md) in test.

## Trip

- `Trip Purpose Prediction` and `AI-generated Photos` APIs have no data restrictions in test.


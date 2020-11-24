## On Demand Flight Status

In test environment, the On Demand Flight Status API contains cached data.
As these data are static the test environment doesn't support live updates such as real-time delay status, gate updates, terminal information etc.
Let's have a look at an example below for the flight IB532 with departure date 2020-11-24.

The **arrival's flight delay** is not part of the response in test environment, but in production it is as below: 

```
                    "arrival": {
                        "timings": [
                            {
                                "qualifier": "STA",
                                "value": "2020-11-24T13:00+01:00",
                                "delays": [
                                    {
                                        "duration": "PT-24M"
                                    }
                                ]
                            }
                        ]
                    }
```

Also, in test there is no information on the **departure terminal**, whereas in production it's returned: 
```
                    "departure": {
                        "terminal": {
                            "code": "4"
                        },
                        "timings": [
                            {
                                "qualifier": "STD",
                                "value": "2020-11-24T11:40+01:00"
                            }
                        ]
                    }
```

Below you can find both API responses for test and production environment. 

### Test environment 
```
{
    "meta": {
        "count": 1,
        "links": {
            "self": "https://test.api.amadeus.com/v2/schedule/flights?carrierCode=IB&flightNumber=532&scheduledDepartureDate=2020-11-24"
        }
    },
    "data": [
        {
            "type": "DatedFlight",
            "scheduledDepartureDate": "2020-11-24",
            "flightDesignator": {
                "carrierCode": "IB",
                "flightNumber": 532
            },
            "flightPoints": [
                {
                    "iataCode": "MAD",
                    "departure": {
                        "timings": [
                            {
                                "qualifier": "STD",
                                "value": "2020-11-24T11:40+01:00"
                            }
                        ]
                    }
                },
                {
                    "iataCode": "VGO",
                    "arrival": {
                        "timings": [
                            {
                                "qualifier": "STA",
                                "value": "2020-11-24T13:00+01:00"
                            }
                        ]
                    }
                }
            ],
            "segments": [
                {
                    "boardPointIataCode": "MAD",
                    "offPointIataCode": "VGO",
                    "scheduledSegmentDuration": "PT1H20M",
                    "partnership": {
                        "operatingFlight": {
                            "carrierCode": "AA",
                            "flightNumber": 8711
                        }
                    }
                }
            ],
            "legs": [
                {
                    "boardPointIataCode": "MAD",
                    "offPointIataCode": "VGO",
                    "aircraftEquipment": {
                        "aircraftType": "320"
                    },
                    "scheduledLegDuration": "PT1H20M"
                }
            ]
        }
    ]
}
```

### Production environment
```
{
    "meta": {
        "count": 1,
        "links": {
            "self": "https://api.amadeus.com/v2/schedule/flights?carrierCode=IB&flightNumber=532&scheduledDepartureDate=2020-11-24"
        }
    },
    "data": [
        {
            "type": "DatedFlight",
            "scheduledDepartureDate": "2020-11-24",
            "flightDesignator": {
                "carrierCode": "IB",
                "flightNumber": 532
            },
            "flightPoints": [
                {
                    "iataCode": "MAD",
                    "departure": {
                        "terminal": {
                            "code": "4"
                        },
                        "timings": [
                            {
                                "qualifier": "STD",
                                "value": "2020-11-24T11:40+01:00"
                            }
                        ]
                    }
                },
                {
                    "iataCode": "VGO",
                    "arrival": {
                        "timings": [
                            {
                                "qualifier": "STA",
                                "value": "2020-11-24T13:00+01:00",
                                "delays": [
                                    {
                                        "duration": "PT-24M"
                                    }
                                ]
                            }
                        ]
                    }
                }
            ],
            "segments": [
                {
                    "boardPointIataCode": "MAD",
                    "offPointIataCode": "VGO",
                    "scheduledSegmentDuration": "PT1H20M",
                    "partnership": {
                        "operatingFlight": {
                            "carrierCode": "AA",
                            "flightNumber": 8711
                        }
                    }
                }
            ],
            "legs": [
                {
                    "boardPointIataCode": "MAD",
                    "offPointIataCode": "VGO",
                    "aircraftEquipment": {
                        "aircraftType": "320"
                    },
                    "scheduledLegDuration": "PT1H20M"
                }
            ]
        }
    ]
}
```

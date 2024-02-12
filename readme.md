# Hertz Scraper Documentation

## Overview

Hertz Scraper is a sophisticated tool engineered for interfacing with the Hertz API, designed to fetch comprehensive rental location data and detailed rental information effortlessly. This documentation provides a thorough overview of the tool's capabilities, usage instructions, input parameters, and expected outputs to ensure users can effectively leverage its functionality.

More information on how to use this scraper here: https://apify.com/travelspider/hertz-car-rental-scraper

## Features

Hertz Scraper offers two primary features, enabling users to query specific information from Hertz's extensive database:

- **Locations Query**: Aimed at identifying Hertz rental locations, this feature allows users to find locations based on a specified search criterion, providing a detailed overview of each available rental location.
- **Rentals Query**: This feature focuses on extracting rental information, including details about available vehicles, their pricing, and rental quotes, to assist users in making informed rental decisions.

## Getting Started

### Input Parameters

To interact with the Hertz Scraper API Wrapper, users must provide specific input parameters, which vary based on the query type. These parameters include:

- **`pickupAge`**: Age of the renter. (String)
- **`pickupDate`**: Date of vehicle pickup, formatted as DD/MM/YYYY. (String)
- **`pickupLocationCode`**: Code identifying the pickup location. (String)
- **`pickupLocationName`**: Name of the pickup location. (String)
- **`pickupTime`**: Time of vehicle pickup. (String)
- **`queryType`**: Type of query (`"locations"` or `"rentals"`). (String)
- **`returnDate`**: Date of vehicle return, formatted as DD/MM/YYYY. (String)
- **`returnLocationCode`**: Code for the return location. (String)
- **`returnLocationName`**: Name of the return location. (String)
- **`returnTime`**: Time of vehicle return. (String)

### Outputs

#### Locations

The output for the "locations" query type is an array of rental locations with the following attributes:

- **locationName**: The name of the rental location.
- **latitude**: The latitude coordinate of the location.
- **longitude**: The longitude coordinate of the location.
- **code**: The code associated with the location.
- **streetAddressLine1**: The first line of the street address.
- **streetAddressLine2**: The second line of the street address.
- **zipCode**: The zip code of the location.
- **city**: The city where the location is situated.
- **country**: The country where the location is situated.

#### Rentals

The output for the "rentals" query type is an array of rental information with the following attributes:

- **type**: The type or model of the vehicle.
- **group**: The group or category of the vehicle.
- **fuelConsumption**: The fuel consumption details of the vehicle.
- **passengers**: The number of passengers the vehicle can accommodate.
- **luggage**: Details about luggage capacity.
- **transmission**: The type of transmission of the vehicle.
- **quotes**: An array of quotes containing pricing information, each with attributes:
  - **currency**: The currency in which the price is quoted.
  - **price**: The rental price.
  - **prepaid**: Indicates whether the rental is prepaid (1) or not (0).

### Example Input (locations)

```json
{
  "queryType": "locations",
  "searchLocation": "Miami"
}
```

### Example output (locations)

```json
{
[
  {
    "locationName": "Miami International Airport",
    "latitude": 25.798598,
    "longitude": -80.260607,
    "code": "MIAT15",
    "streetAddressLine1": "3900 Northwest 25th Street",
    "streetAddressLine2": ", Suite 410",
    "zipCode": "33142                         ",
    "city": "Miami",
    "country": "United States"
  }
]
}
```

### Example Input (rentals)

```json
{
  "pickupAge": "25",
  "pickupDate": "07/06/2024",
  "pickupLocationCode": "MIAT15",
  "pickupLocationName": "Miami International Airport",
  "pickupTime": "10:00",
  "queryType": "rentals",
  "returnDate": "27/06/2024",
  "returnLocationCode": "MIAT15",
  "returnLocationName": "Miami International Airport",
  "returnTime": "10:00"
}
```

### Example Output (rentals)
```json
{
[
  {
    "type": "(E7)Tesla Model 3 Standard Range",
    "group": "E7",
    "fuelConsumption": "260 Mile Range",
    "passengers": "5 Passengers",
    "luggage": "1 Large Suitcase, 2 Small Suitcases",
    "transmission": "Automatic Transmission",
    "quotes": [
      {
        "currency": "USD",
        "price": "778.71",
        "prepaid": 0
      },
      {
        "currency": "USD",
        "price": "655.37",
        "prepaid": 1
      }
    ]
  }
]
}
```
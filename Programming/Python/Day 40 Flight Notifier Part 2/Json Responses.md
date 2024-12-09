`get_city_data()`

```json
{
  "prices": [
    {
      "city": "Paris",
      "iataCode": "PAR",
      "lowestPrice": 54,
      "id": 2
    },
    {
      "city": "Frankfurt",
      "iataCode": "FRA",
      "lowestPrice": 42,
      "id": 3
    },
    {
      "city": "Tokyo",
      "iataCode": "TYO",
      "lowestPrice": 485,
      "id": 4
    },
    {
      "city": "Hong Kong",
      "iataCode": "HKG",
      "lowestPrice": 551,
      "id": 5
    },
    {
      "city": "Istanbul",
      "iataCode": "IST",
      "lowestPrice": 95,
      "id": 6
    },
    {
      "city": "Kuala Lumpur",
      "iataCode": "KUL",
      "lowestPrice": 414,
      "id": 7
    },
    {
      "city": "New York",
      "iataCode": "NYC",
      "lowestPrice": 240,
      "id": 8
    },
    {
      "city": "San Francisco",
      "iataCode": "SFO",
      "lowestPrice": 260,
      "id": 9
    },
    {
      "city": "Dublin",
      "iataCode": "DBN",
      "lowestPrice": 378,
      "id": 10
    }
  ]
}
```

`get_flight_offers()`

```json
{
  "data": [
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LHR",
      "departureDate": "2024-12-16",
      "returnDate": "2024-12-31",
      "price": {
        "total": "129.05"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-16&returnDate=2024-12-31&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LHR",
      "departureDate": "2024-12-17",
      "returnDate": "2024-12-31",
      "price": {
        "total": "129.05"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-17&returnDate=2024-12-31&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LHR",
      "departureDate": "2024-12-18",
      "returnDate": "2024-12-31",
      "price": {
        "total": "129.05"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-18&returnDate=2024-12-31&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LHR",
      "departureDate": "2024-12-24",
      "returnDate": "2024-12-31",
      "price": {
        "total": "129.05"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-24&returnDate=2024-12-31&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LGW",
      "departureDate": "2024-12-19",
      "returnDate": "2024-12-31",
      "price": {
        "total": "133.55"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-19&returnDate=2024-12-31&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LGW",
      "departureDate": "2024-12-14",
      "returnDate": "2024-12-25",
      "price": {
        "total": "148.37"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-14&returnDate=2024-12-25&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LGW",
      "departureDate": "2024-12-12",
      "returnDate": "2024-12-25",
      "price": {
        "total": "148.37"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-12&returnDate=2024-12-25&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LHR",
      "departureDate": "2024-12-23",
      "returnDate": "2024-12-31",
      "price": {
        "total": "156.05"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-23&returnDate=2024-12-31&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LGW",
      "departureDate": "2024-12-15",
      "returnDate": "2024-12-25",
      "price": {
        "total": "163.37"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-15&returnDate=2024-12-25&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LGW",
      "departureDate": "2024-12-13",
      "returnDate": "2024-12-25",
      "price": {
        "total": "178.37"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-13&returnDate=2024-12-25&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LGW",
      "departureDate": "2024-12-22",
      "returnDate": "2025-01-05",
      "price": {
        "total": "188.37"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-22&returnDate=2025-01-05&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LGW",
      "departureDate": "2024-12-20",
      "returnDate": "2024-12-31",
      "price": {
        "total": "189.55"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-20&returnDate=2024-12-31&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    },
    {
      "type": "flight-date",
      "origin": "MAD",
      "destination": "LGW",
      "departureDate": "2024-12-21",
      "returnDate": "2024-12-31",
      "price": {
        "total": "189.55"
      },
      "links": {
        "flightDestinations": "https://test.api.amadeus.com/v1/shopping/flight-destinations?origin=MAD&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&currency=EUR&viewBy=DATE",
        "flightOffers": "https://test.api.amadeus.com/v2/shopping/flight-offers?originLocationCode=MAD&destinationLocationCode=LON&departureDate=2024-12-21&returnDate=2024-12-31&adults=1&nonStop=false&maxPrice=280&currency=EUR"
      }
    }
  ],
  "dictionaries": {
    "currencies": {
      "EUR": "EURO"
    },
    "locations": {
      "MAD": {
        "subType": "AIRPORT",
        "detailedName": "ADOLFO SUAREZ BARAJAS"
      },
      "LHR": {
        "subType": "AIRPORT",
        "detailedName": "HEATHROW"
      },
      "LGW": {
        "subType": "AIRPORT",
        "detailedName": "GATWICK"
      }
    }
  },
  "meta": {
    "currency": "EUR",
    "links": {
      "self": "https://test.api.amadeus.com/v1/shopping/flight-dates?origin=MAD&destination=LON&departureDate=2024-12-12,2024-12-24&oneWay=false&duration=1,15&nonStop=false&maxPrice=280&viewBy=DATE"
    },
    "defaults": {
      "oneWay": false,
      "duration": "1,15",
      "nonStop": false
    }
  }
}
```
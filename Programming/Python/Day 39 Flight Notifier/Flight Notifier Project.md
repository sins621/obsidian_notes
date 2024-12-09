# Program Requirements

1. Use the Flight Search and Sheety API to populate your own copy of the Google Sheet with [International Air Transport Association (IATA)](https://en.wikipedia.org/wiki/IATA_airport_code#Cities_with_multiple_airports) codes for each city. Most of the cities in the sheet include multiple airports, you want the city code (not the airport code see [here](https://en.wikipedia.org/wiki/IATA_airport_code#Cities_with_multiple_commercial_airports)).

2. Use the Flight Search API to check for the cheapest flights from tomorrow to 6 months later for all the cities in the Google Sheet.

3. If the price is lower than the lowest price listed in the Google Sheet then send an SMS (or WhatsApp Message) to your own number using the Twilio API.

4. The SMS should include the departure airport IATA code, destination airport IATA code, flight price and flight dates. e.g.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-05-24_14-01-11-8a81da6acff1044a6330a19853f3d01f.jpeg)

Here's what it looks like with WhatsApp:

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-05-24_14-01-11-9b2d3c8941a101031135123ae6ef151d.png)

## Notes and Gotchas

**Avoid hitting your rate limit** on your trial accounts by not using too many destination airports in your google Sheet (use 5 or at most 10)

Also, the test Amadeus test API does not include all airports. You may not be able to retrieve prices for many routes flights. Try and stick to popular airports while practicing. 

## Toggle these options when setting up with Sheety

**Sheety API**

Avoid making too many unnecessary requests with the Sheety API while testing your code. The free tier for the Sheety API **only** allows **200 requests per month**.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-05-24_14-01-11-c9af9080a2eb134a4b0f82e044892180.png)

Also, **enable the PUT option** so that you can write to your Google sheet

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-05-24_14-01-11-d13543efd7056b9defcb7e75e11e727e.png)

#### Register with the Amadeus Flight Search API

Amadeus provides a free, rate limited test API.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-05-24_14-01-12-968453b63315627ee73c76ff4e6c5a20.png)

Go ahead and register: [https://developers.amadeus.com/register](https://developers.amadeus.com/register)

There is no need to provide a credit card or billing information.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-05-24_14-01-12-1a7320d41a732a1a8edf2f261512fe88.png)

A verification email will get sent to the email that you provided. Click the button to activate your account. 

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-05-24_14-01-12-971e1357b721ec98c0831776408d234a.png)

## Set up your Self Service App

Login to Amadeus. Then go to your self service workspace and create a new Self-Service App

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-05-24_14-01-12-51e91965b6e2506269120a5414702363.gif)

Create your new app. You can call it anything you want.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-05-24_14-01-12-c6fde75893295da05856c9552254215a.gif)

Make sure you get hold of your API keys! Copy and paste them someplace safe. You'll need these keys later to request an access token, so that you can search for flights.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-05-24_14-01-13-e29c49069a6f3cd1397b2eee2838b702.png)
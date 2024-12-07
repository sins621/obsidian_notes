# Step 1 - Create a Sharable Form linked to your Sheet

We'll need our customer's names and emails in order to email them the flight deals. We've already got a Google Sheet set up, so the easiest way to have our future customers provide their emails is to send the a form, so that they can add their email to our Google sheet. Our Python program will then read from that sheet (as it did before), but now it will be able to email those customers who put their email down!

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-03-49dfffce49e295a596a916e4311f4e69.png)

#### Configure a Google Form write to your existing Sheet

1. Inside [Google Drive](https://drive.google.com/drive/), right click and create a new google form.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-03-e000698dbec4fce89619f682fe76809c.gif)

2. Make sure **email collection** is **disabled** and you do _not_ limit to 1 response (this makes testing and entering some dummy data easier).

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-03-6aab90fbcb116b5bd16ebb8d306db0e2.gif)

3. Add 3 questions to collect their first name, last name, and email.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-04-9a4c137c3b60a2998856cdf457dd68e8.gif)

**4. ‼️ Link your google form to your existing Flight Deals Sheet ‼️**

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-04-b0c0bae7c74a9d5ceab5026c7ab84bf0.gif)

5. **Rename** your responses sheet to "**users**"

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-04-c136ae11b2286e37f38388c9d719522c.gif)

6. Try out your form. Submit some dummy data and see if it shows up in your sheet. Click **Send** and copy the link.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-04-213671c2aec0ba311acedb84429f4067.png)

Paste the link into a private or incognito window in your browser. And submit some responses.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-05-158f9a45348f7e60936b4e8fd76a2f42.gif)

You should see your data show up in your spreadsheet now.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-05-7511957dc988e93ffacccfe90e4324ee.png)

#### Configure Sheety for User Data

 1. **Sync** the new sheet in Sheety. Your "users" sheet should appear below "prices".

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-05-d62f30f84ef4aabe8e18cb484acd085d.gif)

Note: you might have to log in again to Sheety.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-05-d4beaf7c519de8cb52dd41f1711ea9d9.png)

4. **Check** that **PUT** and **POST** requests are enabled for your users tab. Enable **POST** requests for the users endpoint.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-11_14-38-10-5c49dbe2c1c94457c184c2fbf5f6152d.png)

4. Enable the **POST** method in the **users** endpoint:

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-11_14-38-10-3011692b02b6c76bc9e5a69678c10442.png)


![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-12_12-19-05-7335053c2142f02a90d76e93428c2eb0.gif)

Why are we using a google form instead of writing the Python terminal program that you saw in the previous video? Sadly, replit has disabled sharing of terminal style programs. A google form has become the best substitute for now.

# Step 2 - Destinations without Direct Flights

There are a lot of popular destinations that our customers will want to go to that don't have direct flights. e.g. London to Bali would have to be via, say, Singapore.

**Requirements**

If a direct flight is not found, search Amadeus one more time for that destination to see if there are indirect flights (flights with 1 stop or 2 stops) instead. Capture the cheapest flight price for a flight with a stopover.

**Technical Specification**

You'll need to modify the main.py, flight_search.py and the flight_data.py files so that you:

* Search for indirect flights only if there are no direct flights.

* Modify the `check_flights()` function so that it has a parameter called `is_direct` that has a default value of `True`  :

1. def check_flights(self, origin_city_code, destination_city_code, from_time, to_time, is_direct=True):

* Look at the flight_search.py. The Amadeus API has a query parameter called "nonStop". Set this to the string "true" and "false" depending on your needs.

* In the flight_data.py, add a variable called `stops` to your `__init__()` method to capture how many stops a flight has.

* Update the  `destination` so that you get the airport code from the final destination, not just from the stopover. Hint: In Amadeus an itinerary with a single segment is a direct flight. If there is more than 1 segment then the flight has stopovers.

# Step 3 - Retrieve your customer emails

Your customers are submitting their data to your google sheet.

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-17_18-41-15-5f05ae1b59a5f9e0316b9b1481762f32.png)

1. Make a note of the column name that contains the email addresses. The name comes from what you used in the Google form.

**Objective**

Retrieve the emails from your google sheet as a Python list inside your main.py

**Technical requirements**

You should make changes to your data_manager.py, your main.py and your .env file.

* Add your endpoints for your "prices" and your "users" sheets to your .env file.

* Add a method called `get_customer_emails()` to your data_manager.py. This should return the data on your "users" spreadsheet.

* Update the `__init()__` method so that you retrieve all the environment variables in one place. This should include things like your `SHEETY_USERNAME` , your password, but also your endpoints.

In the next step we'll send out emails to all our customers that we've retrieved from the Google sheet!

# Step 4 - Email all our customers

Now that our program is working as expected, all that's left to do is to notify our customers when there is a good deal!

![](https://img-c.udemycdn.com/redactor/raw/article_lecture/2024-06-17_18-55-46-450bb5ee393bda3f4639255f7f895454.png)

For this step you'll need to use what you have learnt about smtplib and sending emails (we covered this in day 32). This is the final part of the project!

**Objective**

Send all our customers in the "users" sheet from Google Sheets an email that contains the flight deal.

**Technical requirements**

1. Update your .env file with your SMTP address, your email, and your app password.

2. In the notification_manager.py, update your `__init__()` method so that you retrieve all the environment variables in one place.

3. Create a method in the NotificationManager called `send_emails()` .

NOTE: when sending emails, it won't like the "£" symbol, you might get an error like the one below:

![](https://img-c.udemycdn.com/redactor/raw/2020-07-31_11-28-22-f3e28e0bd21481439a976bb9749bcda3.png)

Use "GBP" instead of the "£" symbol. You can also solve this by encoding the message with UTF-8 e.g. [https://stackoverflow.com/questions/9942594/unicodeencodeerror-ascii-codec-cant-encode-character-u-xa0-in-position-20#answer-9942885](https://stackoverflow.com/questions/9942594/unicodeencodeerror-ascii-codec-cant-encode-character-u-xa0-in-position-20#answer-9942885)

4. In your main.py, craft a different message depending on whether the flight is direct or has a stopover.
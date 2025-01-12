# Making Calls

APIs provide us with an interface to request information from another source or endpoint, for example we can request the position of the ISS by making a request to the ISS Current Location API hosted [here](http://open-notify.org/Open-Notify-API/ISS-Location-Now/).

We can use the `requests` module to make this request and the specific request that we will be making will be a 'get' request using the `get()` method.

```python
import requests

response = requests.get(url="http://api.open-notify.org/iss-now.json")
print(response) #<response [200]>
```

The print statement returns 'response 200' because that is the code which informs us that our request was successful, code 200 means **OK**.
# HTTP Codes

You may have come across the ubiquitous '404' code, this means the information that was requested was not found. Generally these codes are grouped by their first digit for example:

- 1XX - Hold On
- 2XX - Here You Go
- 3XX - Go Away
- 4XX - You Screwed Up
- 5XX - I Screwed Up

From the requests module we can access the status code of our object by tapping into the `status_code` attribute:

```python
import requests

response = requests.get(url="http://api.open-notify.org/iss-now.json")
print(response.status_code) # 200
```

Let's see what happens when we make a get request to an endpoint that doesn't exist:

```python
import requests

response = requests.get(url="http://api.open-notify.org/ss-now.json")
print(response.status_code) # 404                       ^ typo

```
# Raising Exceptions

In the event that have an unsuccessful request we may want to raise an exception and notify the user of this issue, we could always use the `raise` keyword and raise an exception by using an `if` statement to check for a specific status code, or if the code was not 200. However, there are many different status codes leading to either the need to write too many conditions or to raise exceptions too broadly, fortunately for us the `requests` module provides a method for raising exceptions on unsuccessful request.

```python
import requests

response = requests.get(url="http://api.open-notify.org/ss-now.json")
response.raise_for_status()

# Output:
#Traceback (most recent call last):
#  File "/home/sins/Documents/Programming/Python-Learning/Day 33/API Requests/main.py", line 4, in <module>
#    response.raise_for_status()
#  File "/home/sins/Documents/Programming/Python-Learning/.venv/lib/python3.12/site-packages/requests/models.py", line 1024, in raise_for_status
#    raise HTTPError(http_error_msg, response=self)
#requests.exceptions.HTTPError: 404 Client Error: Not Found for url: http://api.open-notify.org/ss-now.json
```

In this example we have the same typo and now we can see that we raise an exception and right at the end of the output you can see the status code along with the URL where the unsuccessful request was made.
# Formatting the Response

This API endpoint supplies us with `json` formatted data which is very similar to a python dictionary. The `requests` module provides us with a method to convert this `json` data into a dictionary.

```python
import requests

response = requests.get(url="http://api.open-notify.org/iss-now.json")
data = response.json()

print(type(data)) # <class 'dict'>
print(data) # {'timestamp': 1732412661, 'iss_position': {'longitude': '-24.0732', 'latitude': '-2.8540'}, 'message': 'success'}
```
# API Parameters

Some APIs can take parameters as arguments in their request to modify what is returned.

```python nums
parameters = {
    "lat": MY_LAT,
    "lng": MY_LONG,
    "formatted": 0,
}

response = requests.get(
	"https://api.sunrise-sunset.org/json", 
	params=parameters
)
```

In this example we're calling an API that returns a sunrise and sunset time when we pass in our location as longitude and latitude. We also modify the output by passing in a key named `formatted` with a value of 0 to indicate that the time that is returned should not be formatted. Notice that in this instance we are passing parameters in as a dictionary.

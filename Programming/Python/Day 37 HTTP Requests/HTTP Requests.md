So far we have been mainly using `get` requests when working with APIs however there are other kinds of requests that can be made.

- `get`
- `post`
- `put`
- `delete`

# Post Request

When we want to push data to the endpoint we would use a `post` request:

```python
pixela_endpoint = "https://pixe.la/v1/users"

user_params = {
    "token": os.getenv("pixela_auth"),
    "username": "bradlycarpenterza",
    "agreeTermsOfService": "yes",
    "notMinor": "yes",
}

response = requests.post(url=pixela_endpoint, json=user_params)
```

In this example we are attempting to create a Pixela account and so we are using a `post` request to send our token and username to their API to create an account on their service.

Upon printing the code and message we see the following:

```
Attemping to Post to Pixela, Status: 200
{'message': "Success. Let's visit https://pixe.la/@bradlycarpenterza , it is your profile page!", 'isSuccess': True}
```

Navigating to the link and we can see that a blank user has been created for us:

![](Pictures/HTTP%20Requests%20-%20Pixela%20User%20Page.png)

# HTTP Headers

We generally want to provide authentication keys via HTTP Headers. The reason for this is that when we provide our auth tokens via parameters it's equivalent to typing your auth key into your browser URL bar and having it be visible in your browsing history. This makes it very easy for bad actors to gain access to these authentication keys.

In order to provide the authentication key in the HTTP Header for Pixela we will do it as follows:

```python
graph_endpoint = f"{pixela_endpoint}/{USERNAME}/graphs"

graph_config = {
    "id": "graph1",
    "name": "Cycling Graph",
    "unit": "Km",
    "type": "float",
    "color": "sora"
}

headers = {
    "X-USER-TOKEN": TOKEN
}

response = requests.post(url=graph_endpoint, json= graph_config, headers=headers)
```

It is passed in as the keyword argument `headers`.
# Put Request

In order to update existing data at the endpoint we will put in a `put` request.

```python
update_endpoint = f"{pixel_creation_endpoint}/{today_date}"

update_data = {
    "quantity": "19"
}

response = requests.put(url=update_endpoint, json=update_data, headers=headers)
```
# Delete Request

Finally to request the deletion of data from the endpoint we will put in a `delete` request.

```python
response = requests.delete(url=update_endpoint, headers=headers)
 ```

Notice no data is required to passed in to this request, only the endpoint and authentication via the header.
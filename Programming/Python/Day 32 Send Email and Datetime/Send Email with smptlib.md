We can use the smptlib library to send an email.

```python
import smtplib

my_email = "fl0586114@gmail.com"
my_password = "yourapppassword"

with smtplib.SMTP("smtp.gmail.com", port=587) as connection:
    connection.starttls()
    connection.login(user=my_email, password=my_password)
    connection.sendmail(
        from_addr=my_email,
        to_addrs="blah5115@yahoo.com",
        msg="Subject: Totally Not Spam\n\nThis is really not a spam mail",
    )
```

Note the port is important for google, it may vary per provider.

The password used is not an account password but rather an "app" password which you will need to register and generate for your provider. The `starttls()` module will encrypt the rest of the SMTP session if the server supports it.

The rest of the methods are self explanatory however do note that in order to write a message in your Subject Line you will need to provide `Subject:` followed by your subject and then for the message body you will need to create two new lines with `\n\n` and thereafter you may write your message body.
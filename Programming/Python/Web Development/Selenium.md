# Scraping with Selenium

[Selenium](https://selenium-python.readthedocs.io/) is a **Web Driver** which is a programming interface and protocol that allows you to control web browsers through code. 

When using Selenium you will notice your web browser of choice open and perform actions that you specify in your code. The benefit of this is that sites will be accessed by your web browser providing all the necessary headers to be seen as more authentic.
## Creating the Web Driver Object

```python
from selenium import webdriver
chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)

driver = webdriver.Chrome(options=chrome_options)
driver.get("https://www.python.org/")
```

We can create the basic browser window using the `webdriver` class from Selenium, in this example we are using **Chrome**. We create two objects, an options object to use the "detach" feature and the Web Driver object itself by creating a Chrome Web Driver object and initializing it with our specified options by passing in the Options object during initialization. Finally we use the `.get()` method to access the web page of our choosing.
## Accessing Web Page Elements

Just as with Beautiful Soup, we can access elements by name, class name, ID, CSS Selectors.

```python
# Class Name
price_dollar = driver.find_element(By.CLASS_NAME, value="a-price-whole").text
# Name
search_bar = driver.find_element(By.NAME, value="q")
# ID
button = driver.find_element(By.ID, value="submit")
# CSS Selector
documentation_link = driver.find_element(
    By.CSS_SELECTOR, value=".documentation-widget a"
)
 ```

We can also access elements by *XPATH*. Similar to the path to a file in a conventional file directory we can access elements by going through the path or tree of elements they are found in.

![](Pictures/Selenium%20-%20Accessing%20XPATH.png)

XPath: `/html/body/div/div[3]/div/section/div[2]/div[2]/p[2]/a`

```python
# XPath
download_link = driver.find_element(
    By.XPATH, value="/html/body/div/div[3]/div/section/div[2]/div[2]/p[2]/a"
)
```

Now all we need to do to retrieve the information we want from these elements is suffix our objects with `.text` for text or call the `.get_attribute()` to access attributes such as links via `href`.

## Closing The Browser

We can close the browser windows programmatically by calling the `.quit()` method on our driver object. We can also call `.close()` to close tabs.



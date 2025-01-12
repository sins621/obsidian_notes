Instead of just serving HTML elements with our Flask apps we can also serve static web-pages.

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.get("/")
def home(name=None):
    return render_template('index.html', name=name)

if __name__=="__main__":
    app.run(debug=True)
```

We can use the `render_template()` method for this purpose. Note however that it is vital that our file-tree match the specification for serving static web-pages via flask.

```
folder structure:
server.py
|___templates
    |___index.html
|___static
	|___styles.css
	|___picture.png
```

**Note:** When referencing files inside of our `index.html` file we will simply point to the `static/` directory for our files such as the style-sheet or any media files.
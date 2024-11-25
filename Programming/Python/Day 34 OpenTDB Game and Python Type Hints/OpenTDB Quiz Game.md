# Json with HTML Entities

In his example we are making a project that requests 10 true or false questions from the Open Trivia Database. Here's how we are making the request:

```python nums
import requests

parameters = {
    "amount": 10,
    "category": 31,
    "type": "boolean",
}

response = requests.get(
	"https://opentdb.com/api.php", 
	params=parameters
)

data = response.json()
question_data = data["results"]
```

Here is a snippet of the output:

```json
[
    {
        "type": "boolean",
        "difficulty": "easy",
        "category": "Entertainment: Japanese Anime &amp; Manga",
        "question": "Studio Ghibli is a Japanese animation studio responsible for the films &quot;Wolf Children&quot; and &quot;The Boy and the Beast&quot;.",
        "correct_answer": "False",
        "incorrect_answers": [
            "True"
        ]
    },
    {
        "type": "boolean",
        "difficulty": "easy",
        "category": "Entertainment: Japanese Anime &amp; Manga",
        "question": "The anime &quot;Lucky Star&quot; follows the story of one girl who is unaware she is God.",
        "correct_answer": "False",
        "incorrect_answers": [
            "True"
        ]
    },
]
```

At first glance everything seems in order however you may notice some odd words and markings present in the strings that were returned for the category and question such as `&amp`, `&quot`. This is a result of API returning 'HTML Entities'.

We can use the `html` module and more specifically the `unescape()` method to remove these odd markings and replace them with the correct symbols such as ampersands and quotes in this example.

```python
for question in question_data:
    question["question"] = html.unescape(question["question"])
```

**Note:** We are only making these changes for the questions as the categories won't be displayed to the end user.

Let's have a look at the output now:

```json
[
    {
        "type": "boolean",
        "difficulty": "medium",
        "category": "Entertainment: Japanese Anime &amp; Manga",
        "question": "The animated film \"Spirited Away\" won the Academy Award for Best Animated Feature at the 75th Academy Awards in 2003.",
        "correct_answer": "True",
        "incorrect_answers": [
            "False"
        ]
    },
    {
        "type": "boolean",
        "difficulty": "easy",
        "category": "Entertainment: Japanese Anime &amp; Manga",
        "question": "Studio Ghibli is a Japanese animation studio responsible for the films \"Wolf Children\" and \"The Boy and the Beast\".",
        "correct_answer": "False",
        "incorrect_answers": [
            "True"
        ]
    },
]
```

As you can see the odd markings have correctly been replaced by backlashes and quotes, the backslashes necessary to avoid the text being incorrectly interpreted as separate strings.
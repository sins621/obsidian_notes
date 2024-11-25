# Type Hints

Soooooooooooo........... Python has type syntax???????????????????????????????????????????????????????????????????

In our Quiz Game we created a class for our UI using Tkinter, here is what we have written thus far:
```python nums {11}
import tkinter as Tk
from quiz_brain import QuizBrain

THEME_COLOR = "#375362"
FONT = ("Arial", 20, "italic")
PADDING = 20
PATH = "./Day 34/Trivia App"


class QuizInterface:
    def __init__(self, quiz_brain: QuizBrain):
        self.quiz_brain = quiz_brain

        self.window = Tk.Tk()
        self.window.title("Quizzler")
        self.window.config(padx=PADDING, pady=PADDING, bg=THEME_COLOR)

        self.score = 0
        self.score_label = Tk.Label(text=f"Score: {self.score}")
        self.score_label.config(bg=THEME_COLOR, fg="white")
        self.score_label.grid(row=0, column=1)

        self.canvas = Tk.Canvas(width=300, height=250)
        self.canvas.grid(row=1, column=0, columnspan=2, pady=PADDING)
        self.question_text = self.canvas.create_text(
            150, 125, text="Placeholder", font=FONT, width=280
        )

        false_image = Tk.PhotoImage(file=f"{PATH}/images/false.png")
        self.false_button = Tk.Button(
            image=false_image,
            bg=THEME_COLOR,
            highlightthickness=0,
            bd=0,
        )
        self.false_button.grid(row=2, column=0)

        true_image = Tk.PhotoImage(file=f"{PATH}/images/true.png")
        self.true_button = Tk.Button(
            image=true_image,
            bg=THEME_COLOR,
            highlightthickness=0,
            bd=0,
        )
        self.true_button.grid(row=2, column=1)

        self.get_next_question()
        self.window.mainloop()

    def get_next_question(self):
        q_text = self.quiz_brain.next_question()
        self.canvas.itemconfig(self.question_text, text=q_text)

```

Now you may notice some odd syntax on line 11, we have an expected argument for the initialization of our class which is `quiz_brain`. Next to this initialization the `:` symbol is being used followed by the name of the class that is expected, the QuizBrain class. Yes ladies and gentlemen, it is expecting an argument of  **type** class.

We have type hints in Python.

![](Pictures/Python%20Type%20Hints%20-%20Cinema.png)

This allows us to use our language server for auto completion of the QuizBrain methods, attributes and will also provide inlay errors when they are present, beautiful.
# Variables

We can add type hints to variables just as we have earlier using the type annotation operator (`:`).

```python
age:int = 18
age = "eighteen" # LSP will provide a warning.
```
# Functions

We can also provide type hints for type arguments with the type annotation operator but it's also possible to provide type hints for return types using the return type annotation operator (`->`).

```python
def foo(bar:int) -> bool:
    if bar > 18:
        return True
    else:
        return False
```
# Limitations

Unfortunately, these type hints are purely decorative and won't produce exceptions at runtime when breaking the type rules you have set out that wouldn't naturally create exceptions.
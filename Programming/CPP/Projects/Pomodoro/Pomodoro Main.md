# Introduction

The plan is to make a Console based Pomodoro Timer in C++.
## To do:
- [x] 1. Run a Timer with Splits
	- [x] Work Split with Break Split
	- [x] Progress Bar
	- [x] Dynamically Updating the Same Line
	- [x] Dynamically Updating Multiple Lines

- [ ] 2. Log Splits to a Text File
	- [ ] Create Text File
	- [ ] Read from Text File
	- [ ] Write Split Log to File

- [ ] 3. Offset Current Time by Time Woken Up

- [ ] 4. Add Ability to Pause, Restart, Change Splits

**Bonus?**
- [ ] Walking and Sleeping Cat Animation
# 1. Run a Timer with Splits:

## Dynamically Updating the Same Line:

> Edit: There are some issues with this approach:
> 
> ![](Pictures/Pomodoro%20Main%20-%20Line%20Updating%20Issue.png)
> 
> Unfortunately the remnant of the last line doesn't seem to get cleared when using the `flush()` function, an alternative method may need to be investigated.
>
> Possible Solutions Include:
> - `system("clear")` to clear the terminal each second.
> - Ansi Escape Characters to move the cursor and redraw each second.

A combination of the carriage return operator `"\r"` and the `fflush()` function can be used to print information on a line and continuously overwrite it while displaying the output.

```cpp nums {2,3}
for (size_t count{0}; count < 11; ++count) {
cout << count << "\r";
fflush(stdout); // Flash buffer to display numbers sequentially
this_thread::sleep_for(chrono::seconds(1)); // Freeze for 1 second
}
```
### Carriage Return Operator `"\r"`

This operator returns the cursor to the beginning of the line allowing us to overwrite the previous information present in the line however I am unsure how this will effect drawing multiple lines.

### The `fflush()` Function

If we don't use the flush function in this instance we won't be able to see the output that we're attempting to draw with our for loop. The reason for this is that output will only be drawn when either a new line (`\n`) is encountered, the buffer is full or the program reaches it's end.

### `this_thread::sleep_for()` function

This is used to pause the program, the time it's paused for in this instance is 1 second provided by the `chrono` library.
## Dynamically Updating Multiple Lines:

The problem outlined under the previous heading can be addressed by taking a different approach, using **Ansi Escape Codes** instead. 

### Ansi Escape Codes

> ANSI escape sequences are a standard for in-band signaling to control cursor location, color, font styling, and other options on video text terminals and terminal emulators.

https://en.wikipedia.org/wiki/ANSI_escape_code

We are mainly interested in manipulating the cursor position to allow us to draw over lines that we have previously written. We can achieve this with the following two escape codes:

- `ESC[#A` Which moves the cursor up # lines.
- `ESC[0J` Which erases from the cursor to the end of the line.

We will substitute `ESC` in these examples with `/x1B` in our `std::cout` statements.

We will no longer need to use `fflush()` as we can now use the new line code `\n` which will clean the buffer and print the line each second.

Here's a code snippet example:

```cpp nums {4,5}
for (size_t i{seconds}; i > 0; --i) {
	cout << "\x1b[91m" << i << " Seconds remaining\n";
	this_thread::sleep_for(chrono::seconds(1)); // Freeze for 1 second
    cout << "\n";
	cout << "\x1B[1A"; // Move the Cursor up one line
	cout << "\x1B[0K"; // Erase Text from the Cursor to the end of the                                  // Line
}
```

List of Codes can be found here:

https://gist.github.com/fnky/458719343aabd01cfb17a3a4f7296797

## Process Loop

I'm still unsure about how to structure the the looping resets for the application. While `this_thread::sleep_for(chrono::seconds(1));` allows us to pause the program for one second, providing dual functionality of allowing time for the user to see what is being drawn and allowing for us to loop by using regular integers to count seconds, it unfortunately complicate matters.

Freezing the program every second with this function means that we have to design our entire program around this function and so figuring out where best to place it is important. I have the idea of placing inside timer functions and then using `system("clear")` to clean the display instead of escape characters, let's see how that goes.

> **Update:** It seems as though the solution was to use a combination of escape codes and clearing the screen. Escape codes can be used when the intention is to keep something that is currently written on screen present while the clear command can be used to move to different sections of the program.

## Progress Bar

# Introduction

The plan is to make a Console based Pomodoro Timer in C++.
## To do:
- [ ] 1. Run a Timer with Splits
	- [ ] Work Split with Break Split
	- [ ] Progress Bar
	- [x] Dynamically Updating the Same Line
	- [ ] Dynamically Updating Multiple Lines

- [ ] 2. Log Splits to a Text File
	- [ ] Create Text File
	- [ ] Read from Text File
	- [ ] Write Split Log to File

- [ ] 3. Offset Current Time by Time Woken Up

- [ ] 4. Add Ability to Pause, Restart, Change Splits

**Bonus?**
- [ ] Walking and Sleeping Cat Animation
# 1. Run a Timer with Splits:

## Basic Function
The `<chrono>` feature of C++ can be used to track time, let's test that out based on this snippet from w3:

```cpp nums

```

## Dynamically Updating the Same Line:

> Edit: There are some issues with this approach:
> 
> ![](Pictures/Pomodoro%20Main%20-%20Line%20Updating%20Issue.png)
> 
> Unfortunately the remnant of the last line doesn't seem to get cleared when using the `flush()` function, an alternative method may need to be investigated.

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
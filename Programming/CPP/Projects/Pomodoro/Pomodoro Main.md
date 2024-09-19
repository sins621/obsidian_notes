The plan is to make a Console based Pomodoro timer with the following features:

- Select Pomodoro Splits
- Show Timer or Progress Bar
- Log Splits to a Text File
- Show Current Time Offset by the Time I Woke Up
- Encouraging Messages

# File Management

Documentation on File Management in C++:
https://www.w3schools.com/cpp/cpp_files.asp

```cpp nums
// Create  File Object
ifstream MyFile;
MyFile.open("Record.txt");
if (!MyFile) {
ofstream MyFile("Record.txt");
} else {
cout << "File Exists\n";
}
// Close File
MyFile.close();
```
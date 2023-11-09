# Printing
- The `cout <<` command sends your output to your computer’s default output which is the computer console or terminal
- `endl` is used to go to a new line on the terminal

- The below code accesses `cout` from std without defining it
```cpp
#include <iostream>

int main()
{
    std::cout << "Hello, world!";
}
```

- The below implicitly defines the std namespace so you can just write `cout`
```cpp
#include <iostream>
using namespace std;

int main()
{
    cout << "Hello, world!";
}
```

#### Printing Variables
```cpp
#include <iostream>
using namespace std;

int main(int argc, char** argv) {
  
  string greeting = argv[1];
  string dayOfWeek = argv[2];
  string month = argv[3];
  int day = atoi(argv[4]);
  int currentWaitMinutes = atoi(argv[5]);
  
  cout << greeting << " Today is " << dayOfWeek << ", " << month << " " << day << "." << endl;
  cout << "The current wait time is " << currentWaitMinutes << " minutes." << endl;
  
  return 0;
  
}
```
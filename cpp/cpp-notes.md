# CPP notes

`auto` should be used to declare a variable.

`const` should be used rather than `#define`
```cpp
const pi = 3.14; // rather than
// #define PI = 3.14
```

`using` defines an alias for another type
```cpp
using str_t = std::string;
class a {}
using b::a; // b is alias for a
```

`smart pointers`

exit functions:
- `exit` <stdlib.h> EXIT_SUCCESS & EXIT_FAILURE
- `abort` <stdlib.h> 
- `atexit`

`sizeof(x)`

`templates`

When creating a generic class, all the code should be in the a normal .h file with the methods in a .tpp file.

`thread <thread>`

```cpp
std::thread thread1 (foo, 10);
std::thread thread2 (foo, 5);

join.thread1();
join.thread2();

cout << "All threads are done ..." << endl;
```


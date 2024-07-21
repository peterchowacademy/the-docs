---
title: 31 C++ Nooby Habits
layout: default
parent: Coding Practices
has_children: true
---
## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# Things you should avoid when coding in C++!

## 1. `using namespace std;`

```c++
// DON'T do this :()
#include xxx

void using_namespace_std() {
    using namespace std;
    string s{"hello, world"};
    cout << s << endl;
}
```

```c++
// Do this :)
#include xxx
using namespace std;

void using_namespace_std() {
    string s{"hello, world"};
    cout << s << endl;
}
```
TLDR:
- Please use `using namespace std;` on a GLOBAL level
- Avoid `using namespace std;` in header files, as it will force all your imports to read everything in uncessarily
- Try to import only the stds you need

```c++
// Do this :) EVEN BETTER!
#include xxx
using namespace std::string, std::cout, std::endl;

void using_namespace_std() {
    string s{"hello, world"};
    cout << s << endl;
}
```

## 2. `std::endl`

`std::endl` print a new line + flushes the buffer = taking more time
instead just use `\n` the new line character

```c++
// DON'T do this :(
#include xxx

void print_range(int start, int end) {
   for (auto i = start; i != end; ++i ) {
    std::cout << i << std::endl; // BAD
   }
}
```

```c++
// Do this :)
#include xxx

void print_range(int start, int end) {
   for (auto i = start; i != end; ++i ) {
    std::cout << i << '\n'; // GOOD
   }
}
```


## 3. use a range based for-loop (avoid for-loop by index)

```c++
// DON'T do this :(
#include xxx

void range_based_for_loop(const std::vector<int> &data, auto &model) {
   for (std::size_t i = 0; i < data.size(); ++i) {
    model.update(data[i]); // BAD, we don't care about idx here
   }
}
```

```c++
// DO this :)
#include xxx

void range_based_for_loop(const std::vector<int> &data, auto &model) {
   for (const auto &x: data) {
    model.update(x); // GOOD, no index = less room for error
   }
}
```

## 4. Use std pre-built algorithims!

```c++
// DON'T do this :(
#include xxx

void std_algos() {
   for (std::size_t i = 0; i < data.size(); ++i) {
    model.update(data[i]); // BAD, we don't care about idx here
   }
}
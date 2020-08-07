# awkward-cpp
A curated list of awkward C++ (or C) syntax, standard library, ways of doing things, best practices, etc.

## Motivation
Even learning and using C++ for years, you would definitely have times when C++ surprises you with weird looking syntax that you never used, simple ways to do complicating things  you never expect or hard to find bugs that you encounter again and again. This is a curated list of these sorts of things. You can read one everyday and learn C++ better.


## List

### Name Lookup

- [Qualified name lookup can be used to access a class member that is hidden by a nested declaration or by a derived class](https://en.cppreference.com/w/cpp/language/qualified_lookup)

```c++
struct B { virtual void foo(); };
struct D : B { 
  void foo() override; 
  void bar() {
    B::foo(); // This is commonly used to call B::foo() (static dispatch)
  }
};
int main() {
    D x;
    B& b = x;
    b.foo(); // calls D::foo (virtual dispatch)
    b.B::foo(); // Do you know this syntax before? calls B::foo (static dispatch)
}
```

### Misc

- [0.1+0.2](https://0.30000000000000004.com/)
```c++
#include <iomanip>
#include <iostream>

int main() {
  std::cout << std::setprecision(17) << 0.1 + 0.2; // -> 0.30000000000000004
}
```

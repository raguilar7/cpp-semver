## cpp-semver

Semver implemented in C++

 * attempt to implement [NPM's Semver](https://docs.npmjs.com/misc/semver) feature in C++11
 * optinoal using [PEGTL parser](https://github.com/taocpp/PEGTL)
 * implemented API functions
   * ```semver::intersects( string[, string] )```: Return true if the given version ranges or comparators intersect.
   * ...

### demo

```c++
#include "cpp-semver.hpp"
#include <iostream>

int main()
{
  {
    const std::string ver1 = "1.0.0 || 1.5 - 3.0";
    const std::string ver2 = ">1.1 <2.0";

    const bool intersected = semver::intersects(ver1, ver2);

    std::cout << "\"" << ver1
      << "\" and \"" << ver2
      << "\" are " << (intersected ? "" : "not ")
      << "intersected." << std::endl;
  }

  {
    const std::string comp = "<1.* >2.2";

    const bool intersected = semver::intersects(comp);

    std::cout << "\"" << comp
      << "\" is " << (intersected ? "" : "not ")
      << "intersected." << std::endl;
  }

  return 0;
}
```


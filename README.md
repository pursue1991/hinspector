# hinspector

C++ one-header library to inspect cpu and memory usage (Windows only)


## Snippet

```cpp
#include <iostream>

#include <hinspector/hinspector.hpp>



int main() {

  using namespace  std;

  auto const machine = hinspector::machine::identify();

  cout << machine << endl;

  if(machine.processor.is_intel())
    cout << "Intel" << endl;
  else if(machine.processor.is_amd())
    cout << "AMD" << endl;
  else
    cout << machine.processor.vendor << endl;

  hinspector::usage::machine usage;
  cout << "Usage: " << usage.slice() << endl;

  return 0;
}
```

Possible output:
```
processor: Intel(R) Core(TM) i7-10510U CPU @ 1.80GHz (8 cores), memory: 16 Gb, system: Windows 10
Intel
Usage: processor: 51%, memory: 2 Mb (total 59%)
```


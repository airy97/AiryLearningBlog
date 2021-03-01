1. 运行计时
``` cpp  
#include <ctime>
auto startTime = clock();
auto runtime = (double)(clock() - startTime) / CLOCKS_PER_SEC / 1000.0;
```

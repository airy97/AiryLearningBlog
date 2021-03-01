1. 运行计时
``` cpp  
#include <ctime>
auto startTime = clock();
auto runtime = (double)(clock() - startTime) / CLOCKS_PER_SEC / 1000.0;
```

2. C++随机数
``` cpp
#include <random>
using namespace std;
std::mt19937 e;
e.seed(std::random_device()());
default_random_engine e(time(NULL));
cout << e() << endl;//随机非负数，unsigned

uniform_int_distribution<int> u(0, 9);
cout << e(u) << endl;//闭区间内随机整数

uniform_real_distribution<double> u(0.0, 1.0);
cout << e(u) << endl;//随机浮点数

bernoulli_distribution u;
cout << e(u) << endl;//构造函数只有一个参数，表示该类返回 true 的概率，该参数默认为 0.5
```
1. 运行计时
``` cpp 
#include <chrono> 
template <class T>
	void measure(T&& fun)
	{
		auto starttime = std::chrono::steady_clock::now();
		fun();
		std::chrono::duration<double> diff = std::chrono::steady_clock::now() - starttime;
		std::cout << "Elapsed: " << diff.count() * 1000.0 << " ms. " << std::endl;
	}
```

#### 1. 运行计时
\#include \<ctime>
clock_t startTime,endTime;
startTime = clock();
endTime = clock();
cout << "The run time is: " <<(double)(endTime - startTime) / 1000.0 / CLOCKS_PER_SEC << " ms" << endl;
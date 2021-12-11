# c++ time.h

## 获得当前时间

```c++
#include <ctime>
#include <sys/time.h>
#include <iostream>


struct Timestamp_st
{
    __uint16_t evtID; // 0x0001
    __uint16_t time_year;
    __uint8_t time_month;
    __uint8_t time_day;
    __uint8_t time_hour;
    __uint8_t time_min;
    __uint8_t time_sec;
};

void GetPackTimeStamp(Timestamp_st *time_stamp)
{
    struct timeval curr_tm;
    gettimeofday(&curr_tm, NULL);
    struct tm curr_time;
    localtime_r(reinterpret_cast(time_t *)&curr_tm.tv_sec, &curr_time);
    time_stamp->evtID = 0x0001;
    time_stamp->time_year = curr_time.tm_year + 1900;
    time_stamp->time_month = curr_time.tm_mon + 1;
    time_stamp->time_day = curr_time.tm_mday;
    time_stamp->time_hour = curr_time.tm_hour;
    time_stamp->time_min = curr_time.tm_min;
    time_stamp->time_sec = curr_time.tm_sec;
}
int main()
{
    Timestamp_st time_stamp;
	GetPackTimeStamp(time_stamp);
    std::cout << "time:" << time_stamp.time_year + 1900 << "-"
              << time_stamp.time_month + 1 << "-" << time_stamp.time_day << "-"
              << time_stamp.time_hour << "-" << time_stamp.time_min << "-"
              << time_stamp.time_sec << std::endl;
    std::ofstream mt("./time.txt", std::ifstream::binary|std::ifstream::in);
    mt.write(reinterpret_cast<char *>(&time_stamp),sizeof(Timestamp_st));
    mt.close();
    std::ifstream mm("./time.txt", std::ifstream::binary|std::ofstream::out);
    Timestamp_st aaa;
    mm.read(reinterpret_cast<char *>(&aaa), sizeof(Timestamp_st));
    mm.close();
    return 0;
}
```


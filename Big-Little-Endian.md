```c++
#include<iostream>
#include<cstdio>
#include<cstdlib>
#include<cstring>
#include<string>
#include<queue>
#include<algorithm>
#include<map>
#include<iomanip>
#include<stdlib.h>
#define INF 99999999
using namespace std;
 
int panduan_1(){
    int a = 0x12345678;
    char *c = (char*)&a;
    for(int i = 0;i<4;i++){
        printf("%x\n",c[i]);
    }
    return ((c[0]==0x78)&&(c[1]==0x56)&&(c[2]==0x34)&&(c[3]==0x12));
}
union p{
    int a;
    char b;
};
int panduan_2(){
    p p1;
    p1.a = 1;
    return p1.a==p1.b;
}
int main(){
 
    if(panduan_1()){
        cout<<"little duan"<<endl;
    }else{
        cout<<"big duan"<<endl;
    }
    if(panduan_2()){
        cout<<"little duan"<<endl;
    }else{
        cout<<"big duan"<<endl;
    }
    system("pause");
    return 0;
}
```


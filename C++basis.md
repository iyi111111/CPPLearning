## 1 初识
### 1.1 Hello World
基本框架
```ruby
#include<iostream>
  using namespace std;
  int main(){
  
  cout<<"Hello World"<<endl;
  system("pause");
  
  return 0;
 } 
```

### 1.2 注释
```
//单行注释  用于对一行代码进行说明

/*

多行注释，用于对代码整体进行说明。

*/
```

### 1.3 变量
```
作用：给一段指定的内存空间取名，方便操作这一段内存
语法： 数据类型  变量名 = 变量的初始值
注意：C++创建变量时必须给定初始值，不然报错。
```

### 1.4 常量
```
1. #defined定义的宏常量   #define 常量名 常量值（没有分号）   通常在文件上方定义，表示一个常量
2. const 修饰的变量   const 数据类型 常量名 = 常量值；  通常在变量定义前加关键字const，修饰该变量为常量，不可修改
```

### 1.5 关键字
```
又叫标识符，是C++中预先保留的单词。在定义变量或常量时，不要用关键字！！！
```
### 1.6标识符（变量，常量）命名规则
```
1.标识符不能是关键字
2.标识符只能由字母，数字，下划线组成。
3.第一个字符只能是字母或下划线
4.区分大小写

tips:最好做到见名知意。
```

## 2 数据类型
数据类型为了给变量分配合适的内存空间
### 2.1整型
```
表示整数类型的数据。常用的有一下四种，区别在于所占内存空间的不同
short            2字节          -2^15~2^15-1(-32768~32767)
int              4字节          -2^31~2^31-1
long      
long long        8字节          -2^63~2^63-1

short a = 32768
输出:  a=-32768
```
### 2.2 sizeof
```
统计数据类型所占内存的大小 
sizeof(数据类型/变量)
整型结论：short <int <= long <= long long
```
### 2.3 实型（浮点型）
用于表示小数
```
浮点数的两种表示类型 
float  单精度     4字节    7位有效数字
double 双精度     8字节    15~16位有效数字
c++会默认小数是double型，所有定义float型时 习惯 float f1 = 3.14f 加一个f。
```
### 2.4 字符型
用于显示单个字符
```
语法 char ch = 'a';  
注意：1.通过单引号括起来  2.里面只有一个字符

char 所占用的内存为1个字节

字符型变量并不是把字符本身放到内存中存储，而是将对应的ASCII码放入存储单元 其中：A -- 65  a -- 97
ASCII码0-31分配了控制字符，用于控制外围设备。
ASCII码32-126分配给了能在键盘上打印的字符，查看或者打印文档时可以看到
```
### 2.5 转义字符
用于表示一些不能显示出来的ASCII字符
```
现阶段常用的转义字符有：
\n  换行符
\\  用于输出\
\t  水平制表符  空格和之前的字符加起来凑够8个字符 超过8个就凑16个，每次加一个字节也就是8位。
```
### 2.6 字符串型
用于表示一串字符
```
C风格字符串   char 变量名[] = "字符串值"；
注意事项： 1.字符串名后要加[] 2. 等号后使用的是双引号

C++风格字符串 string 变量名 = "字符串值"；
注意事项: #include<string>
```
### 2.7 布尔类型bool
代表真或假，C++中，除了0都是真。
```
布尔类型只有两个值：
true  真（本质是1）
false 假（本质是0）
bool类型占用一个字节大小
```
### 2.8 数据的输入
用于从键盘获取数据
```
关键字 cin  
语法   cin >> 变量
```
## 3 运算符
用于执行代码的运算

### 3.1 算数运算符
用于处理四则运算
```
/ 除
注意：1.两个整数相除结果依然是整数小数部分去除掉  2. 除数不可以为0   3.两个小数可以相除得到小数
% 取模
注意：1.% 取模运算的本质是求余数    2.除数不为0    3.两个小数无法进行取模运算，只有整型变量可以进行取模运算
前置递增 ++a  后置递增 a++
前置递增先递增，再计算表达式；后置递增先计算表达式再递增。
```
### 3.2 赋值运算符 
将表达式的值赋值给变量：= += -= *= /= %=

### 3.3 比较运算符
用于表达式的比较，返回真值或者假值：== != > < >= <=
```
注意：由于优先级的问题要加括号 cout<< (a==b) << endl;
```
### 3.4 逻辑运算符
根据表达式的值返回真值或假值： 与（&&）  或（||） 非（!）
## 4 程序流程结构
最基本的三种运行结构：顺序结构，选择结构，循环结构。

### 4.1 选择结构 
if
```
if(条件){   }
```

三目运算符：
```
表达式1？表达式2：表达式3;
```
1真则执行表达式2，返回表达式2的结果；假则执行3。三目运算符返回的是变量，可以继续赋值。（a>b）?a:b=100;

switch语句：
```
switch(表达式)
{
  case 结果1:执行语句; break;
  case 结果2:执行语句; break;
  ...
  default:   执行语句; break;
}
```
注意：

（1）switch中表达式类型只能是整型或者字符型

（2）case中如果没有break,程序会一直向下执行

（3）与if相比，switch结构更清晰效率更高，但是不能判断区间。

### 4.2 循环结构
while
```
while(循环条件){ 循环语句 }
```
生成随机数
```
#include<ctime>

srand((unsigned int)time(NULL)); // 添加随机数种子，利用当前系统时间生成随机数，防止每次随机数都一样。
int num = rand() % 100 + 1 ; //生成1到100的随机数
```

do ... while...  先执行一次循环语句，再判断循环条件
```
do {循环语句} while(循环条件);
```
Tips:获取三位数的百位十位个位:
```
153 % 10 = 3
153 / 10 % 10 = 5      //整除要好好用
153 / 100 = 1
```
for 循环
```
for(起始表达式；条件表达式；末尾循环体){循环语句；} //循环中的表达式用分号分隔  for循环较while do while条理清晰
```
break;
```
（1） switch语句中，终止case跳出switch。
（2）循环语句中，跳出当前循环
（3）嵌套语句，跳出最内层循环。
```
continue;
```
跳过本循环中未执行的语句，执行下一次循环。
break会跳出循环，continue不会使循环终止。
```
goto 标记
```
goto FLAG;
FLAG:
```
1.标记约定俗成使用一个纯大写的单词       2.不建议使用。

## 5 数组
存放相同数据元素的集合。
特点：
（1） 数组中的数据元素都是相同的数据类型
（2） 数组占用一块连续的存储空间
### 5.1 一维数组
一维数组定义的三种方式
```
数据类型 数组名[数组长度];
数据类型 数组名[数组长度]={值1，值2，...};   //如果值的数量比数组长度小，填充0。
数据类型 数组名[]={值1，值2，...};
```
一维数组数组名
```
sizeof(arr)                  //统计整个数组在内存中的长度
sizeof(arr)/sizeof(arr[0])   //数组的长度
cout<<arr<<endl;             //获取数组在内存中的首地址 数组名是一个常量，不可以进行赋值！！！
```
找数组中的最大值：
```
先设定一个max,再遍历数组将数组中的元素和max进行比较。
```
元素逆置
```
双指针
1.记录起始下标位置
2.记录终止下表位置
3.起始下标终止下表互换
4.++起始；--终止；
5.回到1，直到起始>=终止
```
冒泡排序
```
1.比较相邻元素，如果第一个比第二个大就交换他们的位置
2.对每一对相邻元素执行同样的操作，找出第一个最大值
3.重复以上步骤，每次比较次数减一直到不需要比较

排序总轮数=元素个数-1
对比次数=元素个数-轮数-1
```
### 5.2 二维数组
四种定义方式
```
数据类型 数组名[行][列];
数据类型 数组名[行][列]={ {数据1，数据2},{数据3，数据4} };
数据类型 数组名[行][列]={ 数据1，数据2，数据3，数据4 };
数据类型 数组名[][列]={ 数据1，数据2,数据3，数据4 };
```
二维数组数组名
```
行数    sizeof(arr)/sizeof(arr[0])
列数    sizeof(arr[0])/sizeof(arr[0][0])
首地址           cout<<arr<<endl;
第一行首地址      cout<<arr[0]<<endl;
第一个元素首地址  cout<<&arr[0][0]<<endl;
```
## 6 函数
### 函数的定义
```
返回类型 函数名 （参数列表）{
  函数体语句；
  return 表达式；
}
```
### 函数的调用
```
函数名（参数值）;
```
函数定义时，括号中的参数称为形式参数，形参；函数调用时，括号中的参数称为实际参数实参。
### 值传递
函数调用时将实参的数值传入形参。

因为，实参会分配一块内存空间，值传递时形参也会分配一块内存空间，所以形参发生改变，不会影响实参。
### 函数的声明
```
返回类型 函数名 （参数列表）;
```
函数的声明可以多次，定义只能有一次
### 函数的分文件编写
```
1.创建后缀名为.h的头文件
2.创建后缀名为.cpp的源文件
3.在头文件中写函数声明
4.在源文件中写函数定义
```
写函数声明时要包括include的库，.cpp中要#include  .h 文件。使用时#include  .h 文件即可。

```
#include " "  双引号代表文件是自己写的
```
## 7 指针
可以通过指针间接访问内存（指针就是一个地址）
### 指针的定义
数据类型 * 变量名
```
int a = 10;
int *p;
p = &a;             // &取地址
cout<<*p<<endl;     // *解引用
```
### 指针所占用的内存空间
指针也是种数据类型

在32位（x86）操作系统下，指针占4个字节空间大小，不管什么数据。

在64位（x64）操作系统下，指针占8个字节空间大小。
### 空指针
空指针用于给指针变量初始化
```
int *p = NULL;
```
空指针是不可以访问的，0~255之间的内存编号是系统占用的，因此不可以访问。
### 野指针
指针指向非法的内存空间
```
int *p = (int*)0x1100;
cout<<*p<<endl;   //访问野指针会报错
```
空指针和野指针都不是我们申请的空间，因此不要访问它。
### const 修饰指针
```
int a = 10;
int b = 20;
//const 修饰指针 常量指针
const int * p1 = &a;
//常量指针 指针指向的值不可以改，指针的指向可以改
p1 = &b;    // *p1 = 20;错误
int * const p2 = &a;
//指针常量 指针的值可以改，指针的指向不可以改
*p2 = 100;  //p2 = &b; 错误 
//const 修饰指针和常量
const int* const p3 = &a;
//*p3 = 100 ; p3 = &b; 错误
```
看const后跟的是指针还是常量，是指针就是常量指针，是常量就是指针常量。
### 指针和数组
利用指针访问数组中的元素
```
int arr[5]={1,2,3,4,5};
int *p = arr;
for(int i=0;i<5;++i){
  cout<<*p<<endl;
  ++p;    //这里是整型指针，相当于往后移动4个字节。 解引用的时候也是解4个字节。
}
```
### 地址传递 
可以修改实参
```
void swap(int *p1,int *p2);


int num1 = 10;
int num2 = 20;
swap(&num1,&num2)  //指针p1保存的num1的地址，p2保存的num2的地址  解引用*p1就是找p1内存指向的数据。
```
如果不想修改实参就用值传递，想修改实参就用地址传递。

函数中的形参改为指针可以节省内存空间，而且不会复制新的副本出来。
## 8 结构体
### 定义和使用
```
struct 结构体名 {
  结构体成员列表
}；
```
创建结构体变量的方式：
```
struct 结构体名 变量名;
struct 结构体名 变量名{成员1值，成员2值...};
定义结构体时顺便定义变量： struct 结构体名{结构体成员列表} 变量;
```
定义结构体时，struct关键词不可以省略；创建时可以省。结构体变量通过操作符“.”访问成员。
### 结构体数组
将结构体放入数组中方便维护
```
struct 结构体名称 数组名[] = { {},{},...{} };    //创建方式结合数组的定义还有结构体的定义就行
```
### 结构体指针
利用->操作符通过结构体指针访问结构体属性。
### 嵌套结构体
结构体中的成员可以是另一个结构体。
### 结构体做函数参数
值传递  地址传递
### const 结构体
加入const之后一旦有修改操作就会报错，防止误操作。
```
void printStudent(const student * stu){ }
```
### 结构体案例1

学校正在做毕设项目，每名老师带领5个学生，总共有3名老师，需求如下

设计学生和老师的结构体，其中在老师的结构体中，有老师姓名和一个存放5名学生的数组作为成员

学生的成员有姓名、考试分数，创建数组存放3名老师，通过函数给每个老师及所带的学生赋值

最终打印出老师数据以及老师所带的学生数据。

```ruby
#include<iostream>
#include<string>
using namespace std;

struct student {
	string name;
	int score;
};
struct teacher {
	string name;
	student sArray[5];
};
void allocateSpace(teacher tArray[], int len) {
	for (int i = 0; i < len; ++i) {
		string nameSeed = "ABCDE";
		tArray[i].name = "teacher_";
		tArray[i].name += nameSeed[i];
		for (int j = 0; j < 5; ++j) {
			tArray[i].sArray[j].name = "student_";
			tArray[i].sArray[j].name += nameSeed[j];   //起名字方式很好
			int random = rand() % 61 + 40;
			tArray[i].sArray[j].score = random;
		}
	}
}
void printTeachers(teacher tArray[], int len) {
	for (int i = 0; i < len; ++i) {
		cout << tArray[i].name << ":" << endl;
		for (int j = 0; j < 5; ++j) {
			cout <<"\t"<< tArray[i].sArray[j].name << " : " << tArray[i].sArray[j].score << endl;
		}
	}
}

int main() {
	srand((unsigned int)time(NULL));
	teacher tArray[3];
	int len = sizeof(tArray) / sizeof(tArray[0]);
	allocateSpace(tArray, len);
	printTeachers(tArray,len);

	system("pause");
	return 0;
}
```
### 结构体案例2 
设计一个英雄的结构体，包括成员姓名，年龄，性别;创建结构体数组，数组中存放5名英雄。

通过冒泡排序的算法，将数组中的英雄按照年龄进行升序排序，最终打印排序后的结果。
```ruby
#include<iostream>
#include<string>
using namespace std;

struct hero {
	string name;
	int age;
	string sex;
};

void printHero(hero hArray[], int hlen) {
	for (int i = 0; i < hlen; ++i) {
		cout << hArray[i].name << " " << hArray[i].age << " " << hArray[i].sex << endl;
	}
}

void bubbleSortHero(hero hArray[], int len) {
	for (int i = 0; i < len - 1; ++i) {
		for (int j = 0; j < len - 1 - i; ++j) {
			if (hArray[j].age > hArray[j + 1].age) {
				hero tempHero = hArray[j];
				hArray[j] = hArray[j + 1];
				hArray[j + 1] = tempHero;
			}
		}
	}
}

int main() {
	hero hArray[5] = {
		{"刘备",23,"男"},
		{"关羽",22,"男"},
		{"张飞",20,"男"},
		{"赵云",21,"男"},
		{"貂蝉",18,"女"}
	};
	int hlen = sizeof(hArray) / sizeof(hArray[0]);
	printHero(hArray, hlen);
	bubbleSortHero(hArray, hlen);
	cout << endl;
	printHero(hArray, hlen);

	system("pause");
	return 0;
}
```

```
#include<iostream>
#include<string>
#include<vector>
#include<algorithm>
using namespace std;

class Hero {
public:
	Hero(string name, int age, string sex) :m_Name(name),m_Age(age), m_Sex(sex) {}
	string m_Name;
	int m_Age;
	string m_Sex;
};

class HeroPrint {
public:
	void operator()(Hero &h1) {
		cout << h1.m_Name << " " << h1.m_Age << " " << h1.m_Sex << endl;
	}
};

class MyCompare {
public:
	bool operator()(Hero h1,Hero h2) {
		return h1.m_Age > h2.m_Age;
	}
};

void BubbleSort(vector<Hero>& v) {
	for (int i = 0; i < v.size()-1; ++i) {
		for (int j = 0; j < v.size() - 1 - i; ++j) {
			if (v[j].m_Age > v[j+1].m_Age) {
				Hero htemp = v[j];
				v[j] = v[j+1];
				v[j+1] = htemp;
			}
		}
	}
}

int main() {
	vector<Hero>v;
	Hero h1 = { "刘备",23,"男" };
	Hero h2 = { "关羽",22,"男" };
	Hero h3 = { "张飞",29,"男" };
	Hero h4 = { "赵云",21,"男" };
	Hero h5 = { "貂蝉",98,"女" };
	v.push_back(h1);
	v.push_back(h2);
	v.push_back(h3);
	v.push_back(h4);
	v.push_back(h5);

	for_each(v.begin(), v.end(), HeroPrint());
	cout << "--------------------" << endl;

	sort(v.begin(), v.end(), MyCompare());
	for_each(v.begin(), v.end(), HeroPrint());
	cout << "--------------------" << endl;
	BubbleSort(v);
	for_each(v.begin(), v.end(), HeroPrint());

	system("pause");
	return 0;
}
```







































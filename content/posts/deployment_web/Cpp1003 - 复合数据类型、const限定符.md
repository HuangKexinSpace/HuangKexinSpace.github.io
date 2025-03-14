---
title: Develop - Cpp - 复合数据类型、const限定符
date: 2024-10-03
description:
tags:
  - Cpp
---
# Cpp
## 2.3  复合数据类型
- 引用 
	- 引用就是**起别名**，引用的量必须先初始化。
	- 一旦引用，引用值就和初始值绑定在一起，对其所有的操作都是在与之绑定的对象上（**不能和字面值或者表达式的结果绑定**）完成的。
	- 引用不是对象，**没有引用的引用**。
	- **引用的类型必须与它所引用的对象的类型严格匹配。（除了两个特殊情况）**
 - 引用代码example
``` cpp
int ival = 6;
int &renameival = ival;
renameival = 999;
std::cout<<ival<<std::endl;
//输出会是999，所有的操作都是对ival完成的
```
- 指针
	- 指针是一个对象，无需在定义时赋初值。因为引用不是对象，没有实际地址，所以不能定义指向引用的指针。
	- 除特殊情况外，指针的类型需要和其指向的对象严格匹配。	
	-  指针的状态：
			- 指向一个对象
			- 指向紧邻对象所占空间的下一个位置（p++）
			- 空指针
			- 无效指针，也就是除了上述情况的其他值
	- 指针相等的三种可能：都为空/都指向同一个对象/都指向同一个对象的下一地址
- void* 指针
	- void*  是一种特殊的指针类型，可用于存放任意对象的地址，不同的是我们对该地址中到底是个什么类型的对象并不了解。
	- void* 只能做：与别的指针比较、作为函数的输入或输出、或者赋值给另一个void* 指针。**不能直接操作void* 指针所指的对象，因为不知道它是啥类型的。** 要用的话必须进行显式的类型转换，转换为具体的类型指针后才能操作数据。
- 指针代码example
```cpp
// 定义空指针
int *p = nullptr;
int i = 42;
int *p= &i;
std::cout<< *p << " " << i << " " << p <<std::endl;

// void* 指针用法示例1：与别的指针比较
#include<iostream>
int main(){
// std::cout<<"111";
// int v1;
// std::cin>>v1;
// std::cout<<v1<<std::endl;
int i = 42;
int j = 9;
int *p= &i;
void *q = &j;
if (p == q){
std::cout<< "一样" <<std::endl;
} else{
std::cout<< "不一样" <<std::endl;
}
return 0;
}

// void* 指针用法示例2：作为函数的输入或输出
#include <iostream>
void printValue(void* data, char type) {
    // 根据类型来决定如何处理 void*，必须先进行强制类型转换
    switch (type) {
        case 'i':  // int 类型
            std::cout << "Integer: " << *static_cast<int*>(data) << std::endl;
            break;
        case 'f':  // float 类型
            std::cout << "Float: " << *static_cast<float*>(data) << std::endl;
            break;
        case 'c':  // char 类型
            std::cout << "Char: " << *static_cast<char*>(data) << std::endl;
            break;
        default:
            std::cout << "Unknown type." << std::endl;
            break;
    }
}
int main() {
    int x = 5;
    float y = 3.14f;
    char z = 'A';
    // 使用 void* 作为函数输入
    printValue(&x, 'i');
    printValue(&y, 'f');
    printValue(&z, 'c');
    return 0;
}
//赋值给另一个void* 指针
#include <iostream>
int main() {
    int x = 100;
    void* ptr1 = &x;  // 将 int* 赋值给 void*
    void* ptr2 = ptr1;  // 将 void* 赋值给另一个 void*

    // 由于我们不能直接操作 void*，需要将它转换回来
    std::cout << "Value of x through ptr2: " << *static_cast<int*>(ptr2) << std::endl;

    return 0;
}
```
-  指向指针的引用
	- 问：为什么第二句 不是&* p 这样，为啥 * 要在前
	- 答：如果你写 &* p，那么它的意思是：先解引用 p，得到 p 所指向的对象，然后对这个对象取地址。也就是说，&* p 结果是 p 自己，因为解引用后再取地址，最终还是原来的指针。这在语义上是有意义的，但在这种情况下并不需要。
	- **要理解r的类型，从右往左阅读r的定义。离变量名最近的符号对便利的类型有最直接的影响。声明符的其余部份用以确定r的引用的类型是什么。**
- 指向指针的引用 代码example
```cpp
int *p; 
int *&r = p;//r是一个对指针p对引用
```
## 2.4 Const 限定符
- 因为**const对象一旦创建后其值就不能再改变**，所以const对象必须初始化：
	- const int k; //大错特错，因为没有初始化
	- const int j = get_size(); //对的，运行时初始化
- 默认状态下，const对象仅在当前文件内有效；若要在多个文件中共享const对象，必须在变量的定义之前添加extern关键词。
- 初始化和对const的引用
	- 引用的类型必须与其所引用的对象的类型一致，但例外1：在初始化**常量引用**时允许用任意表达式作为初始值。
	- 例外2: 对const的引用可能引用一个并非const的对象
- 常量引用（const T&）是某个对象的引用，但它**不允许通过该引用修改对象的值**。
- **常量引用可以绑定非常量对象**，即使该对象不是常量，也可以将其值赋值给该引用，这属于值拷贝，不影响该对象本身。
- 指针和const
	- 要想存放常量对象的地址，只能使用指向常量的指针。
	- 指针类型必须与其所指对象的类型一致，但例外1：允许令一个指向常量的指针指向一个非常量对象。
	- 常量指针必须初始化，一旦初始化完成，它的值就不能再改变了。
```cpp
#include<iostream>
int main(){
// std::cout<<"111";
// int v1;
// std::cin>>v1;
// std::cout<<v1<<std::endl;
double dval = 3.14;
const int &i = dval;
std::cout<< dval <<std::endl;
std::cout<< i <<std::endl;
return 0;
}
```

---
title: "__sealed | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__sealed_cpp"
  - "__sealed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sealed 关键字 [C++]"
  - "__sealed 关键字"
ms.assetid: 9e5f778a-4ad8-468d-9c44-783e576fb49b
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __sealed
> [!NOTE]
>  本主题仅适用于 C\+\+ 托管扩展的版本 1。 此语法应仅用于维护版本 1 代码。 请参阅 [sealed](/visual-cpp/windows/sealed-cpp-component-extensions) 有关新语法中使用的等效功能的信息。  
  
 防止方法被重写或类成为基类。  
  
## 语法  
  
```  
  
__sealed   
class-specifier  
__sealed   
struct-specifier  
__sealed   
function-declarator  
  
```  
  
## 备注  
 `__sealed` 关键字指定某个类方法不能被重写或某个类不能为基类。  
  
 使用 `__sealed` 关键字时，请牢记以下几点：  
  
-   `__sealed` 虚拟方法不能被重写。  
  
-   如果将非虚拟成员方法标记为 `__sealed`，则忽略 `__sealed` 限定。  
  
-   `__sealed` 方法不能是纯的。  
  
-   **\_\_Sealed** 一起使用时，不允许使用关键字 [\_\_interface](/visual-cpp/cpp/interface) 关键字。  
  
 在使用 `__sealed` 标记类（或结构）时，类不能用作基类。 例如：  
  
```  
__sealed __gc class A {  
   // ...  
};  
// error: cannot derive from a sealed class  
__gc class B : public A { /* ...*/ };  
```  
  
> [!NOTE]
>  在用于 `__sealed` 关键字时，不允许使用 `__abstract` 关键字。  
  
## 示例  
 在下面的示例中，声明了密封的虚方法 \(`f`\)。 然后在 `main()` 中重写函数，这会导致编译器错误：  
  
```  
// keyword__sealed.cpp  
// compile with: /clr:oldSyntax  
  
#using <mscorlib.dll>  
extern "C" int printf_s(const char*, ...);  
  
__gc struct I  
{  
    __sealed virtual void f()  
    {   
        printf_s("I::f()\n");   
    }  
    virtual void g()  
    {  
        printf_s("I::g()\n");  
    }  
};  
  
__gc struct A : I   
{  
    void f() // C3248 sealed function  
    {   
        printf_s("A::f()\n");   
    }     
    void g()  
    {  
        printf_s("A::g()\n");  
    }  
};  
  
int main()  
{  
    A* pA = new A;  
  
    pA->f();  
    pA->g();  
}  
```
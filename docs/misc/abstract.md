---
title: "__abstract | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__abstract_cpp"
  - "__abstract"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "抽象类 [c + +]"
  - "__abstract 关键字"
ms.assetid: fc6eee5e-9f07-4438-97f7-f2e124263575
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __abstract
> [!NOTE]
>  本主题仅适用于 C\+\+ 托管扩展的版本 1。 此语法应仅用于维护版本 1 代码。 请参阅 [abstract](/visual-cpp/windows/abstract-cpp-component-extensions) 有关新语法中使用的等效功能的信息。  
  
 声明不能直接实例化的托管类。  
  
## 语法  
  
```  
  
__abstract   
class-specifier  
__abstract   
struct-specifier  
  
```  
  
## 备注  
 `__abstract` 关键字声明目标类只能用作另一类的基类。 将 `__abstract` 应用于类或结构并不表示该结果是 \_\_gc 类或 \_\_gc 结构。  
  
 不同于[抽象](/visual-cpp/cpp/abstract-classes-cpp)基类的 C\+\+ 概念，使用 `__abstract` 关键字的类可以定义其成员函数。  
  
> [!NOTE]
>  当与 `__abstract` 或 `__value` 关键字一起使用时，`__sealed` 关键字是不允许使用的，而与 `__interface` 关键字一起使用时，则是冗余的。  
  
## 示例  
 在下面的示例中，`Derived` 类派生自抽象基类 \(`Base`\)。 然后，尝试对两者进行实例化，但仅 `Derived` 会成功。  
  
```  
// keyword__abstract.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__abstract __gc class Base {  
   int BaseFunction() {  
      return 0;  
   }  
};  
  
__gc class Derived: public Base {};  
  
int main() {  
   Base* MyBase = new Base();   // C3622 can't BAse is abstract  
   Derived* MyDerived = new Derived();  
}  
```
---
title: "实现 CObject 派生类时的编译器错误 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "编译源代码, CObject 派生类"
  - "错误 [C++]"
  - "错误 [C++], 编译器"
  - "CObject 类, 派生类的编译器错误"
ms.assetid: 9f249b52-aeff-41a1-8a74-a52aa08c4fcf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# 实现 CObject 派生类时的编译器错误
当你实现派生自 `CObject` 的类，且编写代码，使类的复制构造函数或赋值运算符需要进行调用，则编译器可能会报告类似以下的错误：  
  
```  
error C2660: 'CSample::CSample' : function does not take 1 parameters error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 可以通过编译下面的“示例代码”部分中的示例再现该问题。  
  
> [!NOTE]
>  这篇文章中所示的代码示例生成以下错误消息：  
  
```  
error C2558: 'CSample::CSample' : no copy constructor available error C2582: 'CSample' : 'operator =' function is unavailable  
```  
  
 编译器错误的原因在于 `CObject` 在 AFX.h 文件中声明了一个私有复制构造函数和赋值运算符。 因此，编译器不生成 `CObject` 派生类的默认复制构造函数和赋值运算符。 因为编译器没有找到在类中声明的这些函数，因此它报告错误。  
  
 若要避免编译器错误，你需要实现 `CObject` 派生类的复制构造函数和赋值运算符。 下面的示例代码对此进行了阐释。 你可通过对示例代码中指示的行取消注释来避免这些错误。  
  
## 代码示例  
  
```  
// _error_Compiler_Errors_when_Implementing_a_CObject.2d.Derived_Class.cpp /* Compile options needed: /c */ // replace with #define _CONSOLE when compiling for Windows NT #define _DOS #include <afx.h> class CSample : public CObject { private: short m_nValue; public: // uncomment the lines below to avoid the compiler errors //    CSample() {} //    CSample( const CSample &s )  // copy ctor //        { m_nValue = s.m_nValue; } //    CSample& operator=( const CSample &s )  // assignment operator //        { m_nValue = s.m_nValue; return *this; } }; int main() { CSample a; CSample b = a; a = b; }  
  
```  
  
## 请参阅  
 [编译器警告s C4600 Through C4999](/visual-cpp/error-messages/compiler-warnings/compiler-warnings-c4600-through-c4799)
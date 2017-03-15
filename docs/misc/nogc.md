---
title: "__nogc | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__nogc_cpp"
  - "__nogc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__nogc 类型声明"
  - "非托管类型的类 [c + +]"
  - "非托管的类的声明"
  - "非托管类"
ms.assetid: 3e7f1b09-0fc3-4a8f-9458-a22f7a38ce45
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __nogc
> [!NOTE]
>  本主题仅适用于 C\+\+ 托管扩展的版本 1。 此语法应仅用于维护版本 1 代码。 在新语法中，不需要显式将类型标记为非托管。  
  
 显式声明非托管类型。  
  
## 语法  
  
```  
  
__nogc   
class-specifier  
__nogc   
struct-specifier  
__nogc  
interface-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
__nogc  
new  
  
```  
  
## 备注  
 `__nogc` 关键字用于显式指定在标准 C\+\+ 堆中分配对象。 此关键字是可选的。 如果在类声明前未指定 `__gc` 或 `__nogc`，则它默认为 `__nogc`。  
  
 此类型的对象类似于从标准 C\+\+ 堆分配且不受托管对象限制的标准 C\+\+ 对象。  
  
 在标准 C\+\+ 堆中显式分配 \_\_value 类型的对象时，也可使用 `__nogc` 关键字。  
  
```  
// keyword__nogc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__value struct V {   
   int i;  
};  
int main() {  
   V * v = __nogc new V;  
   v->i = 10;  
   delete v;  
}  
```  
  
> [!NOTE]
>  `__nogc` 关键字还可应用于数组和指针类型。  
  
 gc 指针不能是 `__nogc` 类的成员。 有关在 `__nogc` 类中嵌入值类型的指导信息，请参阅 [\_\_value](../misc/value.md)。  
  
## 示例  
 在下面的示例中，声明了非托管类 \(`X`\) 并且实例化和修改了对象：  
  
```  
// keyword__nogc_2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__nogc class X {  
public:  
   int i;  
};  
  
int main() {  
   X* x;   // declares an unmanaged pointer of type X  
   x = new X();   // creates unmanaged object of type X on the C++ heap  
   Console::WriteLine(x->i);  
  
   x->i = 4;   // modifies unmanaged object  
   Console::WriteLine(x->i);  
  
   delete x;   // call C++ delete operator to clean up resource  
}  
```  
  
 **48378256 4**
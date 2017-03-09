---
title: "__property | Microsoft Docs"
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
  - "__property_cpp"
  - "__property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__property 关键字"
  - "托管类"
  - "属性 [c + +]，托管类"
ms.assetid: 235e3574-6882-4c52-8301-270277b9216d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __property
> [!NOTE]
>  本主题仅适用于 C\+\+ 托管扩展的版本 1。 此语法应仅用于维护版本 1 代码。 请参阅 [属性](/visual-cpp/windows/property-cpp-component-extensions) 有关新语法中使用的等效功能的信息。  
  
 声明用于托管类的标量或索引属性。  
  
## 语法  
  
```  
  
__property  
function-declarator  
  
```  
  
## 备注  
 `__property` 关键字引入属性声明，且可以出现在类、接口或值类型中。 属性可以具有 getter 函数（只读）、setter 函数（只写）或二者（读写）。  
  
> [!NOTE]
>  属性名称不能与包含它的托管类的名称匹配。 getter 函数的返回类型必须与相应的 setter 函数的最后一个参数的类型匹配。  
  
## 示例  
 在下面的示例中，将标量属性 \(`Size`\) 添加到 `MyClass` 声明。 然后，使用 `get_Size` 和 `set_Size` 函数隐式设置和检索属性：  
  
```  
// keyword__property.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class MyClass {  
public:  
   MyClass() : m_size(0) {}  
   __property int get_Size() { return m_size; }  
   __property void set_Size(int value) { m_size = value; }  
   // compiler generates pseudo data member called Size  
protected:  
   int m_size;  
};  
  
int main() {  
   MyClass* class1 = new MyClass;  
   int curValue;  
  
   Console::WriteLine(class1->Size);  
  
   class1->Size = 4;   // calls the set_Size function with value==4  
   Console::WriteLine(class1->Size);  
  
   curValue = class1->Size;   // calls the get_Size function  
   Console::WriteLine(curValue);  
}  
```  
  
## 输出  
  
```  
0  
4  
4  
```
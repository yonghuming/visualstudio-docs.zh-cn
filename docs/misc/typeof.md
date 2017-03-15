---
title: "__typeof | Microsoft Docs"
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
  - "__typeof_cpp"
  - "__typeof"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__typeof 关键字"
ms.assetid: d71b9603-35d0-4c62-b5b4-90ffc2305a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __typeof
**注意** 本主题仅适用于 C\+\+ 托管扩展的版本 1。 此语法应仅用于维护版本 1 代码。 请参阅 [typeid](/visual-cpp/windows/typeid-cpp-component-extensions) 有关新语法中使用的等效功能的信息。  
  
 返回指定类型的 **System::Type**。  
  
```  
  
__typeof(  
typename  
)  
  
```  
  
 其中：  
  
 *typename*  
 您希望用来命名 **System::Type** 的托管类型的名称。 请注意，在托管程序中，某些本机类型别名为公共语言运行时中的类型。 例如，`int` 是 **System::Int32** 的别名。  
  
## 备注  
 利用 **\_\_typeof** 运算符，您可获取自己指定的类型的 **System::Type** 类型。**\_\_typeof** 还可用于返回自定义特性块中的 **System::Type** 的值。 有关创建自己的特性的详细信息，请参阅[特性](/visual-cpp/windows/attribute)。  
  
## 示例  
 在以下示例中，\(`AtClass`\) 自定义特性将应用于 \_\_gc 类 \(`B`\)。 随后使用了 **\_\_typeof** 检索自定义特性的值：  
  
```  
// keyword__typeof.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
public __gc class MyClass {};  
  
[attribute(All)]  
__gc class AtClass {  
public:  
   AtClass(Type*) {  
      Console::WriteLine("in Type * constructor");  
   }  
  
   AtClass(String*) {}  
   AtClass(int) {}  
};  
  
[AtClass(__typeof(MyClass))]   // Apply AtClass attribute to class B  
__gc class B {};  
  
int main() {  
   Type * mytype = __typeof(B);  
   Object * myobject __gc[] = mytype -> GetCustomAttributes(true);  
   Console::WriteLine(myobject[0]);  
}  
```  
  
## 输出  
  
```  
in Type * constructor  
AtClass  
```
---
title: "__box | Microsoft Docs"
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
  - "__box"
  - "__box_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__box 关键字"
  - "Boxing — 装箱"
  - "Unboxing — 取消装箱"
  - "装箱，__box 关键字"
ms.assetid: 935b4a4d-fc45-484c-87c6-d95cfc67cc9d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __box
> [!NOTE]
>  本主题仅适用于 C\+\+ 托管扩展的版本 1。 此语法应仅用于维护版本 1 代码。 请参阅 [装箱](/visual-cpp/windows/boxing-cpp-component-extensions) 有关新语法中使用的等效功能的信息。  
  
 创建 \_\_value 类对象的托管副本。  
  
## 语法  
  
```  
  
__box(  
value-class identifier  
)  
  
```  
  
## 备注  
 `__box` 关键字用于从现有 \_\_value 类对象创建托管对象（派生自 **System::ValueType**）。 当 `__box` 关键字应用于 \_\_value 类时：  
  
-   在公共语言运行时堆上分配托管对象。  
  
-   \_\_value 类对象的当前值按位复制到托管对象。  
  
-   返回新托管对象的地址。  
  
 此过程称为装箱。 它使任何 \_\_value 类对象都能在适用于任何托管对象的一般例程中使用，因为托管对象间接继承自 **System::Object**（因为 **System::ValueType** 继承自 **System::Object**）。  
  
> [!NOTE]
>  新创建的装箱对象是 \_\_value 类对象的副本。 因此，对已装箱对象的值的更改不会影响 \_\_value 类对象的内容。  
  
## 示例  
 下面是执行装箱和取消装箱的示例：  
  
```  
// keyword__box.cpp  
// compile with: /clr:oldSyntax  
#using < mscorlib.dll >  
using namespace System;  
  
int main() {  
  Int32 i = 1;  
  System::Object* obj = __box(i);  
  Int32 j = *dynamic_cast<__box Int32*>(obj);  
}  
```  
  
 在以下示例中，非托管值类型 \(`V`\) 被装箱并作为托管参数传递给 `Positive` 函数。  
  
```  
// keyword__box2.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__value struct V {  
   int i;  
};  
void Positive(Object*) {}   // expects a managed class  
  
int main() {  
   V v={10};   // allocate and initialize  
   Console::WriteLine(v.i);  
  
   // copy to the common language runtime heap  
   __box V* pBoxedV = __box(v);  
   Positive(pBoxedV);   // treat as a managed class  
  
   pBoxedV->i = 20;   // update the boxed version  
   Console::WriteLine(pBoxedV->i);  
}  
```  
  
 **10 20**
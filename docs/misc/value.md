---
title: "__value | Microsoft Docs"
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
  - "__value_cpp"
  - "__value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__value 关键字"
  - "值类型声明"
  - "__value 关键字语法"
ms.assetid: b14b64f7-5db6-4e92-a144-fcbf67572b49
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __value
> [!NOTE]
>  本主题仅适用于 C\+\+ 托管扩展的版本 1。 此语法应仅用于维护版本 1 代码。 请参阅 [类和结构 \(托管\)](/visual-cpp/windows/classes-and-structs-cpp-component-extensions) 有关新语法中使用的等效功能的信息。  
  
 将类声明为 \_\_value 类型。  
  
## 语法  
  
```  
  
__value  
 class-specifier  
__value  
 struct-specifier  
__nogc  
array-specifier  
__nogc  
pointer-specifier  
  
```  
  
## 备注  
 `__value` 类型不同于 `__gc` 类型，该 `__value` 类型变量直接包含其数据，而托管变量指向其数据，这将存储在公共语言运行时堆中。  
  
 以下情况适用于 `__value` 类型：  
  
-   `__value` 关键字无法应用于某个接口。  
  
-   `__value` 类型可从任意数量的接口中继承，并且无法从其他类型或 `__value` 类型中继承。  
  
-   `__value` 类型由定义进行密封。 有关详细信息，请参阅 [\_\_sealed](../misc/sealed.md)。  
  
-   在允许托管类型的任意位置使用 `__value` 类型是有效的。  
  
> [!NOTE]
>  在用于 `__value` 关键字时，不允许使用 `__abstract` 关键字。  
  
 可以将 `__value` 类型显式连接到 **System::Object** 指针。 这称为“装箱”。  
  
 在 `__nogc` 类型中嵌入值类型时，以下准则将适用：  
  
-   值类型必须具有 **LayoutSequential** 或 **LayoutExplicit**。  
  
-   值类型不能具有 gc 指针成员。  
  
-   值类型不能具有私有数据成员。  
  
 在 C\+\+ 托管扩展中，C\# 类和 C\# 结构的等效项如下所示：  
  
|C\+\+ 托管扩展|C\#|更多相关信息|  
|----------------|---------|------------|  
|\_\_gc 结构<br /><br /> \- 或 \-<br /><br /> \_\_gc 类|类|[class](/dotnet/csharp/language-reference/keywords/class) 关键字|  
|\_\_value 结构<br /><br /> \- 或 \-<br /><br /> \_\_value 类|struct|[struct](/dotnet/csharp/language-reference/keywords/struct) 关键字|  
  
## 示例  
 在下面的示例中，声明一个 `__value` 类型 \(`V`\)，然后操作 `__value` 类型的两个实例：  
  
```  
// keyword__value.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value struct V {   
   int m_i;  
};  
  
int main() {  
   V v1, v2;  
   v1.m_i = 5;  
   v2 = v1;   // copies all fields of v1 to v2  
   v2.m_i = 6;   // does not affect v1.m_I  
}  
```
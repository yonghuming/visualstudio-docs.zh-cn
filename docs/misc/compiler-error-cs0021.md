---
title: "编译器错误 CS0021 | Microsoft Docs"
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
  - "CS0021"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0021"
ms.assetid: 4eb5fa24-8261-4962-b36a-224be5074217
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 编译器错误 CS0021
无法将带 \[\] 的索引应用于“type”类型的表达式  
  
 尝试针对不支持[索引器](/dotnet/csharp/programming-guide/indexers/index)的数据类型使用索引器访问值。  
  
 在 C\+\+ 程序集中尝试使用索引器时，可能会遇到 CS0021。 在这种情况下，请用 `DefaultMember` 特性修饰 C\+\+ 类，让 C\# 编译器能够识别默认索引器。 下面的示例生成 CS0021。  
  
## 示例  
 此文件将编译为 .dll 文件（注释掉了 `DefaultMember` 特性）以生成该错误。  
  
```  
// CPP0021.cpp // compile with: /clr /LD using namespace System::Reflection; // Uncomment the following line to resolve //[DefaultMember("myItem")] public ref class MyClassMC { public: property int myItem[int] { int get(int i){  return 5; } void set(int i, int value) {} } };  
```  
  
## 示例  
 下面是调用 .dll 文件的 C\# 文件。 此文件尝试通过索引器访问类，但由于没有将任何成员声明为要使用的默认索引器，所以产生了此错误。  
  
```  
// CS0021.cs // compile with: /reference:CPP0021.dll public class MyClass { public static void Main() { MyClassMC myMC = new MyClassMC(); int j = myMC[1]; // CS0021 } }  
```
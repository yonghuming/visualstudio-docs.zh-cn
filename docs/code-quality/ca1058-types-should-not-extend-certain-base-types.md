---
title: "CA1058：类型不应扩展某些基类型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypesShouldNotExtendCertainBaseTypes"
  - "CA1058"
helpviewer_keywords: 
  - "CA1058"
  - "TypesShouldNotExtendCertainBaseTypes"
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# CA1058：类型不应扩展某些基类型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|TypesShouldNotExtendCertainBaseTypes|  
|CheckId|CA1058|  
|类别|Microsoft.Design|  
|是否重大更改|是|  
  
## 原因  
 外部可见的类型扩展某些基类型。  目前，此规则报告从下列类型派生的类型：  
  
-   <xref:System.ApplicationException?displayProperty=fullName>  
  
-   <xref:System.Xml.XmlDocument?displayProperty=fullName>  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.Queue?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Stack?displayProperty=fullName>  
  
## 规则说明  
 对于 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 版本 1，建议从 <xref:System.ApplicationException> 派生新异常。  此建议已更改，新异常应当从 <xref:System.Exception?displayProperty=fullName> 或者 <xref:System> 命名空间中它的某个子类派生。  
  
 如果您希望创建基础对象模型或数据源的 XML 视图，则不要创建 <xref:System.Xml.XmlDocument> 的子类。  
  
### 非泛型集合  
 请尽可能使用和\/或扩展泛型集合。  不要在代码中扩展非泛型集合，除非以前就已发布。  
  
 **不正确用法示例**  
  
```c#  
public class MyCollection : CollectionBase  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollectionBase  
{  
}  
```  
  
 **正确用法示例**  
  
```c#  
public class MyCollection : Collection<T>  
{  
}  
  
public class MyReadOnlyCollection : ReadOnlyCollection<T>  
{  
}  
```  
  
## 如何解决冲突  
 若要修复与该规则的冲突，请从一个不同的基类型或泛型集合派生该类型。  
  
## 何时禁止显示警告  
 对于与 <xref:System.ApplicationException> 有关的冲突，不要禁止显示该规则发出的警告。  对于与 <xref:System.Xml.XmlDocument> 有关的冲突，可以安全地禁止显示与该规则有关的警告。  如果代码是以前发布的，可以安全地禁止显示有关非泛型集合的警告。
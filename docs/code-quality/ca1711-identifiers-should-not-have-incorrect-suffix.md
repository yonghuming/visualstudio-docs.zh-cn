---
title: "CA1711：标识符应采用正确的后缀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
helpviewer_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1711：标识符应采用正确的后缀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|IdentifiersShouldNotHaveIncorrectSuffix|  
|CheckId|CA1711|  
|类别|Microsoft.Naming|  
|是否重大更改|是|  
  
## 原因  
 某标识符具有错误的后缀。  
  
## 规则说明  
 按照约定，只有扩展某些基类型或实现某些接口的类型的名称或者从这些类型派生的类型的名称，应该以特定的保留后缀结尾。  其他类型名称不应使用这些保留的后缀。  
  
 下表列出了保留后缀以及与这些保留后缀关联的基类型和接口。  
  
|后缀|基类型\/接口|  
|--------|-------------|  
|特性|<xref:System.Attribute?displayProperty=fullName>|  
|Collection|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|事件处理程序委托。|  
|例外|<xref:System.Exception?displayProperty=fullName>|  
|权限|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|  
|堆栈|<xref:System.Collections.Stack?displayProperty=fullName>|  
|流|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 另外，不应使用下列后缀：  
  
-   Delegate  
  
-   Enum  
  
-   Impl \- 改用“Core”  
  
-   Ex 或类似后缀，用于区别于同一类型的早期版本  
  
 命名约定为所有针对公共语言运行时的库提供了通用的外观。  这提高了学习新软件库的效率，并使客户进一步认为该软件库是由某位具有开发托管代码专门技术的人员所开发。  
  
## 如何解决冲突  
 将后缀从类型名称中移除。  
  
## 何时禁止显示警告  
 除非后缀在应用程序域中具有明确的含义，否则不要禁止来自此规则的警告。  
  
## 相关规则  
 [CA1710：标识符应具有正确的后缀](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md)  
  
## 请参阅  
 [特性](../Topic/Attributes1.md)   
 [事件和委托](http://msdn.microsoft.com/zh-cn/d98fd58b-fa4f-4598-8378-addf4355a115)
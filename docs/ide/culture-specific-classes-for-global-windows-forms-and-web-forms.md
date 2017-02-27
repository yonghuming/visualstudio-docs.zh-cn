---
title: "全球 Windows 窗体和 Web 窗体的区域性特定类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "全球化 [Windows 窗体], 类"
  - "Web 应用程序 [.NET Framework], 全球化"
  - "区域性, 特定于区域性的类"
  - "数字, 国际化"
  - "本地化 [Windows 窗体], 类"
  - "全球化 [Visual Studio], 特定于区域性的类"
  - "Windows 窗体, 本地化"
  - "国际应用程序 [Visual Studio], 数据格式"
  - "时间 [Visual Studio], 国际化"
  - "日期 [Visual Studio], 国际化"
  - "区域性"
  - "国际字符"
  - "货币格式"
  - "ASP.NET, 全球化"
  - "类 [Visual Studio], 区域性特定"
  - "本地化 [Visual Studio], 特定于区域性的类"
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>全球 Windows 窗体和 Web 窗体的区域性特定类
每个区域性都具有有关显示日期、时间、数字、货币和其他信息的不同约定。 <xref:System.Globalization> 命名空间包含某些类，这些类可用于修改区域性特定的值的显示方式，如 <xref:System.Globalization.DateTimeFormatInfo>、**Calendar** 和 <xref:System.Globalization.NumberFormatInfo>。  
  
## <a name="using-the-culture-setting"></a>使用区域性设置  
 但大多数情况下，将使用存储在应用程序或“区域选项”控制面板中的区域性设置，自动在运行时确定约定并相应设置信息的格式。 有关设置区域性的详细信息，请参阅[如何：为 Windows 窗体全球化设置区域性和 UI 区域性](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0)或[如何：为 ASP.NET 网页全球化设置区域性和 UI 区域性](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0)。 根据区域性设置自动设置信息格式的类称为特定于区域性的类。 某些区域性特定的方法为 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>、<xref:System.Console.WriteLine%2A?displayProperty=fullName> 和 <xref:System.String.Format%2A?displayProperty=fullName>。 特定于区域性的函数（在 Visual Basic 语言中）中包括 `MonthName` 和 `WeekDayName`。  
  
 例如，下面的代码演示如何使用 <xref:System.IFormattable.ToString%2A> 方法为当前的区域性设置货币格式：  
  
```vb#  
' Put the Imports statements at the beginning of the code module  
Imports System.Threading  
Imports System.Globalization  
' Display a number with the culture-specific currency formatting  
Dim MyInt As Integer = 100  
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))  
  
```  
  
```c#  
// Put the using statements at the beginning of the code module  
using System.Threading;  
using System.Globalization;  
// Display a number with the culture-specific currency formatting  
int myInt = 100;  
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));  
```  
  
 如果该区域性设置为“fr-FR”，会在输出窗口中看到：  
  
 `100,00`  
  
 如果该区域性设置为“en-US”，会在输出窗口中看到：  
  
 `$100.00`  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>   
 <xref:System.Globalization.DateTimeFormatInfo>   
 <xref:System.Globalization.NumberFormatInfo>   
 <xref:System.Globalization.Calendar>   
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>   
 <xref:System.String.Format%2A?displayProperty=fullName>   
 [对应用程序进行全球化和本地化](../ide/globalizing-and-localizing-applications.md)


<!--HONumber=Feb17_HO4-->



---
title: "CA1305：指定 IFormatProvider | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyIFormatProvider"
  - "CA1305"
helpviewer_keywords: 
  - "CA1305"
  - "SpecifyIFormatProvider"
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1305：指定 IFormatProvider
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|类型名|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大更改|  
  
## 原因  
 某方法或构造函数调用具有可接受 <xref:System.IFormatProvider?displayProperty=fullName> 参数的重载的一个或多个成员，且该方法或构造函数不调用采用 <xref:System.IFormatProvider> 参数的重载。  该规则忽略对 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 方法（记录为忽略 <xref:System.IFormatProvider> 参数）以及下列其他方法的调用：  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## 规则说明  
 如果未提供 <xref:System.Globalization.CultureInfo?displayProperty=fullName> 或 <xref:System.IFormatProvider> 对象，则重载成员提供的默认值可能不会在所有区域设置中产生想要的影响。  另外，[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 成员会根据对您的代码来说可能不正确的假设来选择默认区域性和格式设置。  要确保代码在您的环境中按预期运行，应根据下列准则提供区域性特定的信息：  
  
-   如果值将显示给用户，请使用当前区域性。  请参见 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>。  
  
-   如果值将由软件（与文件或数据库相关）存储和访问，请使用固定区域性。  请参见 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>。  
  
-   如果不知道值的目标，请让数据使用者或数据提供者来指定区域性。  
  
 请注意，<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 仅用于使用 <xref:System.Resources.ResourceManager?displayProperty=fullName> 类的实例检索本地化资源。  
  
 即使重载成员的默认行为适合您的需要，也最好显式调用区域性特定的重载，这样您的代码将是自描述代码且更易于维护。  
  
## 如何解决冲突  
 要修复与该规则的冲突，请使用以 <xref:System.Globalization.CultureInfo> 或 <xref:System.IFormatProvider> 为参数的重载，并根据以上列出的准则指定参数。  
  
## 何时禁止显示警告  
 如果确定默认区域性\/格式提供者的确是正确选择，且代码可维护性不是开发时应优先考虑的重要问题，则可以安全地禁止显示此规则发出的警告。  
  
## 示例  
 在下面的示例中，`BadMethod` 将导致与此规则冲突的两种情况。  `GoodMethod` 通过将固定区域性传递到 <xref:System.String.Compare%2A> 来更正第一个冲突，并通过将当前区域性传递到 <xref:System.String.ToLower%2A> 来更正第二个冲突，因为 `string3` 将显示给用户。  
  
 [!code-cs[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## 示例  
 下面的示例演示当前区域性对 <xref:System.DateTime> 类型选择的默认 <xref:System.IFormatProvider> 的影响。  
  
 [!code-cs[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 该示例产生下面的输出。  
  
  **6\/4\/1900 12:15:12 PM**  
**06\/04\/1900 12:15:12**   
## 相关规则  
 [CA1304：指定 CultureInfo](../Topic/CA1304:%20Specify%20CultureInfo.md)  
  
## 请参阅  
 [NIB: Using the CultureInfo Class](http://msdn.microsoft.com/zh-cn/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
---
title: "CA1305： 指定 IFormatProvider |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3bb11846ed204ee15525266a750b218295c8d662
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305：指定 IFormatProvider
|||  
|-|-|  
|TypeName|SpecifyIFormatProvider|  
|CheckId|CA1305|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 某方法或构造函数调用具有重载，以接受的一个或多个成员<xref:System.IFormatProvider?displayProperty=fullName>参数，该方法或构造函数不调用采用的重载<xref:System.IFormatProvider>参数。 此规则将忽略对调用[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]记录为忽略方法<xref:System.IFormatProvider>参数还此外包含以下方法：  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## <a name="rule-description"></a>规则说明  
 当<xref:System.Globalization.CultureInfo?displayProperty=fullName>或<xref:System.IFormatProvider>未提供对象，则重载成员提供的默认值可能没有要包含在所有区域设置的效果。 此外，[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]成员选择默认区域性和格式设置基于可能不为你的代码正确的假设。 若要确保代码按预期适合你的方案运行，还应提供区域性特定信息根据下列准则：  
  
-   如果将向用户显示的值，则使用当前区域性。 请参阅<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>。  
  
-   如果将存储的值，并通过软件 （保存到文件或数据库），使用固定区域性。 请参阅<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>。  
  
-   如果不知道的值的目标，具有数据使用者或提供程序指定的区域性。  
  
 请注意，<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>仅用于通过使用的实例中检索本地化的资源<xref:System.Resources.ResourceManager?displayProperty=fullName>类。  
  
 即使重载的成员的默认行为是适合你的需求，则最好显式调用的特定于区域性的重载，因此，你的代码是自我说明且更易于维护。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，使用采用重载<xref:System.Globalization.CultureInfo>或<xref:System.IFormatProvider>和指定的自变量，根据前面已列出的准则。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告时确定的默认区域性/格式提供程序是正确的选择，并且代码可维护性不是重要的开发优先级。  
  
## <a name="example"></a>示例  
 在下面的示例中，`BadMethod`导致冲突的此规则的两种情况。 `GoodMethod`通过将传递到固定区域性更正第一次冲突<xref:System.String.Compare%2A>，并通过将传递到当前区域性更正第二个冲突<xref:System.String.ToLower%2A>因为`string3`向用户显示。  
  
 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_1.cs)]  
  
## <a name="example"></a>示例  
 下面的示例演示上默认值为当前区域性的效果<xref:System.IFormatProvider>已选择通过<xref:System.DateTime>类型。  
  
 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1305-specify-iformatprovider_2.cs)]  
  
 本示例生成以下输出。  
  
 **6/4/1900年 12:15:12 PM**  
**06/04/1900 12:15:12**   
## <a name="related-rules"></a>相关的规则  
 [CA1304：指定 CultureInfo](../code-quality/ca1304-specify-cultureinfo.md)  
  
## <a name="see-also"></a>另请参阅  
[使用 CultureInfo 类](/dotnet/standard/globalization-localization/globalization#Cultures)  
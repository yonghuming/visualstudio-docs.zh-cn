---
title: "CA1304： 指定 CultureInfo |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4cd654145fed46594fd2fcd076a20b30e393a23b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304：指定 CultureInfo
|||  
|-|-|  
|TypeName|SpecifyCultureInfo|  
|CheckId|CA1304|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 某方法或构造函数调用的成员有接受的重载<xref:System.Globalization.CultureInfo?displayProperty=fullName>参数，该方法或构造函数不调用采用的重载<xref:System.Globalization.CultureInfo>参数。 此规则将忽略对以下方法的调用：  
  
-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>  
  
-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>  
  
## <a name="rule-description"></a>规则说明  
 当<xref:System.Globalization.CultureInfo>或<xref:System.IFormatProvider?displayProperty=fullName>未提供对象，则重载成员提供的默认值可能没有要包含在所有区域设置的效果。 此外，[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]成员选择默认区域性和格式设置基于可能不为你的代码正确的假设。 若要确保代码按预期方式适合你的方案，应提供区域性特定信息根据下列准则：  
  
-   如果将向用户显示的值，则使用当前区域性。 请参阅<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>。  
  
-   如果将存储的值，并通过软件，即保存到文件或数据库，使用固定区域性。 请参阅<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>。  
  
-   如果不知道的值的目标，具有数据使用者或提供程序指定的区域性。  
  
 请注意，<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>仅用于通过使用的实例中检索本地化的资源<xref:System.Resources.ResourceManager?displayProperty=fullName>类。  
  
 即使重载的成员的默认行为是适合你的需求，则最好显式调用的特定于区域性的重载，因此，你的代码是自我说明且更易于维护。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，使用采用重载<xref:System.Globalization.CultureInfo>或<xref:System.IFormatProvider>和指定的自变量，根据前面已列出的准则。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 则可以安全地禁止显示此规则的警告时某些默认的区域性/格式提供程序正确的选择，并且该代码可维护性不重要的开发优先级。  
  
## <a name="example"></a>示例  
 在下面的示例中，`BadMethod`导致冲突的此规则的两种情况。 `GoodMethod`通过将固定区域性传递到 System.String.Compare，更正第一次冲突并通过将传递到当前区域性更正第二个冲突<xref:System.String.ToLower%2A>因为`string3`向用户显示。  
  
 [!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]  
  
## <a name="example"></a>示例  
 下面的示例演示上默认值为当前区域性的效果<xref:System.IFormatProvider>已选择通过<xref:System.DateTime>类型。  
  
 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]  
  
 本示例生成以下输出。  
  
 **6/4/1900年 12:15:12 PM**  
**06/04/1900 12:15:12**   
## <a name="related-rules"></a>相关的规则  
 [CA1305：指定 IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md)  
  
## <a name="see-also"></a>另请参阅  
[使用 CultureInfo 类](/dotnet/standard/globalization-localization/globalization#Cultures)  
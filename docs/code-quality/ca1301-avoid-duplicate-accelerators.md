---
title: "CA1301： 避免快捷键重复 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13d2f36014ab15aea3148ab4175a89b77deb4846
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301：避免快捷键重复
|||  
|-|-|  
|TypeName|AvoidDuplicateAccelerators|  
|CheckId|CA1301|  
|类别|Microsoft.Globalization|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 类型扩展<xref:System.Windows.Forms.Control?displayProperty=fullName>和包含两个或多个具有相同访问密钥存储在资源文件中的顶级控件。  
  
## <a name="rule-description"></a>规则说明  
 访问键也称为快捷键，它通过使用 Alt 键来实现对控件的键盘访问。 如果多个控件具有重复的访问键，则访问键的行为定义不正确。 用户可能无法访问目标的控件使用的访问密钥，并可能启用旨在以外的控件。  
  
 此规则的当前实现将忽略菜单项。 但是，相同子菜单中的菜单项不应具有相同访问密钥。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 若要修复与此规则的冲突，定义所有控件的唯一访问的密钥。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 不禁止显示此规则发出的警告。  
  
## <a name="example"></a>示例  
 下面的示例演示包含具有相同的访问键的两个控件的最小表单。 密钥存储在资源文件中，而不会显示;但是，其值出现在注释掉`checkBox.Text`行。 可以通过交换检查重复快捷键的行为`checkBox.Text`与其注释掉的对应项的行。 但是，在这种情况下，该示例将不会生成警告从规则。  
  
 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [桌面应用中的资源](/dotnet/framework/resources/index)
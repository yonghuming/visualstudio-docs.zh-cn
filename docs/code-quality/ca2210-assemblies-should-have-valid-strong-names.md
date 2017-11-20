---
title: "CA2210： 程序集应具有有效的强名称 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 11e50cb87364a85d0c97ae5e566b1209696febbd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210：程序集应具有有效的强名称
|||  
|-|-|  
|TypeName|AssembliesShouldHaveValidStrongNames|  
|CheckId|CA2210|  
|类别|Microsoft.Design|  
|是否重大更改|非重大更改|  
  
## <a name="cause"></a>原因  
 程序集不具有强名称签名无法验证强名称，或强名称是无当前计算机的注册表设置无效。  
  
## <a name="rule-description"></a>规则说明  
 此规则检索并验证强名称程序集。 如果以下任何一种情况，则会发生冲突：  
  
-   程序集没有强名称。  
  
-   程序集签名后已发生更改。  
  
-   程序集是延迟签名。  
  
-   程序集签名错误，或签名失败。  
  
-   程序集需要注册表设置以通过验证。 例如，强名称工具 (Sn.exe) 用于跳过程序集的验证。  
  
 强名称可避免客户端在不知情的情况下加载已被篡改的程序集。 除非极为有限的几种情况，否则不应部署没有强名称的程序集。 如果共享或发布未正确签名的程序集，则该程序集可能被篡改，公共语言运行时可能不会加载该程序集；而用户可能必须在他/她的计算机上禁用验证。 没有强名称程序集具有以下缺点：  
  
-   无法验证其来源。  
  
-   公共语言运行时无法警告用户如果更改了程序集的内容。  
  
-   无法加载到全局程序集缓存。  
  
 请注意，如果要加载和分析延迟签名的程序集，必须先禁用该程序集的验证。  
  
## <a name="how-to-fix-violations"></a>如何解决冲突  
 **若要创建的密钥文件**  
  
 使用以下过程之一：  
  
-   使用提供的程序集链接器工具 (Al.exe) [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK。  
  
-   有关[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]v1.0 或 1.1 版，请使用<xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>或<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>属性。  
  
-   有关[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]，可以使用两种`/keyfile`或`/keycontainer`编译器选项[/KEYFILE （指定密钥或密钥对程序集进行签名）](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly)或[/KEYCONTAINER （指定密钥容器程序集进行签名）](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) c + + 中的链接器选项)。  
  
 **使用 Visual Studio 中强名称程序集进行签名**  
  
1.  在[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，打开你的解决方案。  
  
2.  在**解决方案资源管理器**，右键单击你的项目，然后单击**属性。**  
  
3.  单击**签名**选项卡，然后选择**对程序集签名**复选框。  
  
4.  从**选择强名称密钥文件**，选择**新建**。  
  
     **创建强名称密钥**窗口将显示。  
  
5.  在**密钥文件名称**，键入你的强名称密钥的名称。  
  
6.  选择是否要使用密码保护密钥，然后单击**确定**。  
  
7.  在**解决方案资源管理器**，右键单击你的项目，然后单击**生成**。  
  
 **使用 Visual Studio 外强名称程序集进行签名**  
  
-   使用强名称工具 (Sn.exe) 提供的[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]SDK。 有关详细信息，请参阅 [Sn.exe （强名称工具）](/dotnet/framework/tools/sn-exe-strong-name-tool)。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 如果环境中使用程序集仅禁止显示此规则的警告篡改的内容并不是问题的位置。  
  
## <a name="see-also"></a>另请参阅  
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>   
 <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>   
 [如何：使用强名称为程序集签名](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)   
 [Sn.exe（强名称工具）](/dotnet/framework/tools/sn-exe-strong-name-tool)
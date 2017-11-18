---
title: "CA1824： 将程序集用 NeutralResourcesLanguageAttribute 标记 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c1d2138065946bfd14abfedbbffdd2dc5b433d89
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824：用 NeutralResourcesLanguageAttribute 标记程序集
|||  
|-|-|  
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|  
|CheckId|CA1824|  
|类别|Microsoft.Performance|  
|是否重大更改|非重大|  
  
## <a name="cause"></a>原因  
 程序集包含**ResX**-基于资源但不具有<xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName>应用于它。  
  
## <a name="rule-description"></a>规则说明  
 **NeutralResourcesLanguage**特性通知**ResourceManager**用于显示程序集的非特定区域性的资源的语言。 查找与特定资源语言中，相同的区域性中的资源时**ResourceManager**会自动使用位于主程序集的资源。 而不是具有当前线程的当前用户接口区域性的附属程序集搜索做到这一点。 这将改进所加载的第一个资源的查找性能，并缩小工作集。  
  
## <a name="fixing-violations"></a>修复冲突  
 若要修复与此规则的冲突，将属性添加到该程序集，并指定非特定区域性的资源的语言。  
  
## <a name="specifying-the-language"></a>指定的语言  
  
#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>若要指定非特定区域性的资源语言  
  
1.  在**解决方案资源管理器**，右键单击你的项目，然后单击**属性**。  
  
2.  从左侧的导航栏中选择**应用程序**，然后单击**程序集信息**。  
  
3.  在**程序集信息**对话框框中，选择的语言从**非特定语言**下拉列表。  
  
4.  单击“确定”。  
  
## <a name="when-to-suppress-warnings"></a>何时禁止显示警告  
 它是允许禁止显示此规则的警告。 但是，可能会降低启动性能。
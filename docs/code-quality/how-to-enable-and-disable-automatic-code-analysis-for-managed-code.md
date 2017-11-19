---
title: "如何： 启用和禁用自动代码分析的托管代码 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c22d194-5fea-4f23-b02d-19344fa64a64
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ad960a490d92e84efdfbd73e9aa23d7b41dc0dd1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>如何：启用和禁用托管代码的自动代码分析
你可以配置代码分析，以在托管的代码项目的每个生成之前运行。 你可以为每个设置不同的代码分析属性[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]配置。  
  
### <a name="to-enable-or-disable-automatic-code-analysis"></a>若要启用或禁用自动代码分析  
  
1.  在**解决方案资源管理器**，右键单击该项目，然后单击**属性**。  
  
2.  在项目属性对话框中，单击**代码分析**。  
  
3.  指定中的生成类型**配置**和中的目标平台**平台**。  
  
4.  若要启用或禁用自动代码分析，请选择或清除**启用生成代码分析 （定义 CODE_ANALYSIS 常量）**复选框。
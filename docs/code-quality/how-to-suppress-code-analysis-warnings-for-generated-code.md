---
title: "如何： 禁止显示生成的代码的代码分析警告 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24b94c0c4ce6031876f5ad26ce01a22299f7056a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>如何：禁止显示所生成代码的代码分析警告
托管的代码编译器通常会生成添加到项目，以便加快代码的开发的代码。 此外，开发人员通常使用第三方工具来帮助快速开发应用程序。 这些工具还生成添加到项目的代码。  
  
 你可能想要看到生成的代码中的代码分析发现的规则冲突。 但是，你可能不想以查看它们是否能查看和维护包含冲突的代码。  
  
 **禁止显示生成代码产生的结果**项目的代码分析属性页上的复选框使您能够选择是否想要查看由第三方工具生成的代码中的代码分析警告。  
  
> [!NOTE]
>  此选项不会取消代码分析错误和警告从生成的代码时的错误和警告出现在窗体和模板。 可以查看和维护窗体或模板的源代码。  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>若要禁止显示的项目中生成代码的警告  
  
1.  右键单击解决方案资源管理器中的项目，然后单击**属性**。  
  
2.  单击**代码分析**。  
  
3.  选择**禁止显示生成代码产生的结果**复选框。
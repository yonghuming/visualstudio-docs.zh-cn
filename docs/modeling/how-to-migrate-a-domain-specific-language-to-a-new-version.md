---
title: "如何︰ 将域特定语言迁移到新版本 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 14
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 397efd1049ea52b2e7c67a46509d2a088c6fa488
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>如何：将域特定语言迁移至新版本
您可以将迁移项目的定义和使用特定于域的语言设置为[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]从版本的[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]一起分发[!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]。  
  
 作为的一部分提供的迁移工具[!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]。 该工具将转换[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目和解决方案使用，或定义 DSL 工具。  
  
 您必须显式运行迁移工具︰ 它就不会启动自动打开中的解决方案时[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在此路径中可以找到工具和详细的指导文档︰  
  
 **%程序 Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>你之前迁移你的 DSL 项目  
 迁移工具修改[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目文件 (**.csproj**) 和解决方案文件 (**.sln**)。  
  
#### <a name="to-prepare-projects-for-migration"></a>若要准备迁移项目。  
  
-   请确保**.csproj**和**.sln**可以写入文件。 如果它们是受源代码管理，请确保在签出。  
  
-   制作一份你想要迁移的文件夹。  
  
## <a name="migrating-a-collection-of-projects"></a>迁移项目的集合  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>若要将 DSL 项目和解决方案迁移到 Visual Studio 2010  
  
1.  启动 DSL 迁移工具。  
  
    -   您可以双击该工具在 Windows 资源管理器 （或文件资源管理器），或从命令提示符下启动该工具。 该工具位于以下位置︰  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  选择包含解决方案和您想要转换的项目的文件夹。  
  
    -   在工具，顶部的框中输入的路径或单击**浏览**。  
  
     迁移工具将显示树中的定义或使用 Dsl 的项目。 在树中包括使用每个项目**Microsoft.VisualStudio.Modeling.Sdk**或**TextTemplating**程序集。  
  
3.  查看树中的项目，并取消选中不想要转换的项目。  
  
    -   选择项目或解决方案，以查看该工具将进行更改的列表。  
  
        > [!NOTE]
        >  显示文件夹名称旁边的复选框没有任何影响。 必须展开要检查项目和解决方案的文件夹。  
  
4.  将项目转换。  
  
    1.  单击**转换**。  
  
         每个项目文件时，将转换的一个副本之前*项目***.csproj**另存为*项目***。 vs2008.csproj**  
  
         每个副本*解决方案***.sln**另存为*解决方案***。 vs2008.sln**  
  
    2.  调查报告任何失败的转换。  
  
         在文本窗口会报告失败。 此外，树视图可以显示一个红色标志，未能转换每个节点上。 您可以单击节点来获取有关该失败的详细信息。  
  
5.  **转换所有模板**解决方案中包含已成功转换的项目。  
  
    1.  打开的解决方案。  
  
    2.  单击**转换所有模板**解决方案资源管理器的标头中的按钮。  
  
        > [!NOTE]
        >  您可以使本步骤不必要。 有关详细信息，请参阅[如何实现自动化转换所有模板](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a)。  
  
6.  更新自定义代码在转换后的项目中。  
  
    -   尝试生成项目，并调查任何故障。  
  
    -   测试您的设计器。  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>另请参阅  
 [相关的博客文章](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)



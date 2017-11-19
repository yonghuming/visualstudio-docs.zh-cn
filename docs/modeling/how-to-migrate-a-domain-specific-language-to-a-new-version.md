---
title: "如何： 迁移到新版本的域特定语言 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: "14"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 397efd1049ea52b2e7c67a46509d2a088c6fa488
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>如何：将域特定语言迁移至新版本
你可以迁移项目的定义和使用到的域特定语言[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]的版本中的[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]，随之发行[!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]。  
  
 作为的一部分提供迁移工具[!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]。 该工具将转换[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目和解决方案使用，或定义 DSL 工具。  
  
 必须显式运行迁移工具： 它将不自动启动时打开一种解决方案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在此路径中可以找到的工具和详细的指南文档：  
  
 **%程序 Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>之前将 DSL 项目的迁移  
 迁移工具修改[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]项目文件 (**.csproj**) 和解决方案文件 (**.sln**)。  
  
#### <a name="to-prepare-projects-for-migration"></a>若要准备迁移项目。  
  
-   请确保**.csproj**和**.sln**可以写入文件。 如果它们是在源代码管理下，请确保在签出。  
  
-   使你想要迁移的文件夹的副本。  
  
## <a name="migrating-a-collection-of-projects"></a>迁移项目的集合  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>若要将 DSL 项目和解决方案迁移到 Visual Studio 2010  
  
1.  启动 DSL 迁移工具。  
  
    -   可以双击 Windows 资源管理器 （或文件资源管理器） 中的工具，也可以从命令提示符启动该工具。 该工具位于以下位置：  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  选择包含解决方案和你想要转换的项目的文件夹。  
  
    -   在工具，顶部的框中输入的路径或单击**浏览**。  
  
     迁移工具显示的定义或使用 Dsl 的项目的树。 树包括使用每个项目**Microsoft.VisualStudio.Modeling.Sdk**或**TextTemplating**程序集。  
  
3.  查看树中的项目，并取消选中不想要转换的项目。  
  
    -   选择一个项目或解决方案，以查看该工具将进行的更改的列表。  
  
        > [!NOTE]
        >  显示在文件夹名称旁边的复选框没有任何效果。 你必须展开文件夹以检查项目和解决方案。  
  
4.  转换项目。  
  
    1.  单击**转换**。  
  
         每个项目文件转换，一份之前*项目***.csproj**另存为*项目***。 vs2008.csproj**  
  
         每个副本*解决方案***.sln**另存为*解决方案***。 vs2008.sln**  
  
    2.  调查报告任何失败的转换。  
  
         失败会在文本窗口报告。 此外，该树视图显示红色标志未能转换每个节点上。 你可以单击要获取有关该故障的详细信息的节点。  
  
5.  **转换所有模板**解决方案中包含已成功转换项目。  
  
    1.  打开的解决方案。  
  
    2.  单击**转换所有模板**解决方案资源管理器的标头中的按钮。  
  
        > [!NOTE]
        >  你可以进行此步骤不必要。 有关详细信息，请参阅[如何自动转换所有模板](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a)。  
  
6.  更新自定义代码在转换后的项目中。  
  
    -   尝试生成项目，并调查任何故障。  
  
    -   测试您的设计器。  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>另请参阅  
 [相关的博客文章](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)


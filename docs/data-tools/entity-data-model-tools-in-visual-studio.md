---
title: "Visual Studio 中的实体框架工具 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: eb4ca4445af3970828f4212c69c11d9d173d5650
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="entity-framework-tools-in-visual-studio"></a>Visual Studio 中的实体框架工具
实体框架是一种对象关系映射技术，使.NET 开发人员能够通过使用特定于域的对象处理关系数据。 它消除了对大多数开发人员通常需要编写数据访问代码的需求。 实体框架成为建模为新的.NET 应用程序的技术建议的对象关系映射 (ORM)。  
  
实体框架工具旨在帮助你构建 Entity Framework (EF) 应用程序。 用于实体框架的完整文档是此处： [EF 核心和 EF 6](https://docs.microsoft.com/ef/)。  
  
使用实体框架工具，您可以创建*概念模型*从现有数据库，然后以图形方式直观显示和编辑概念模型。 或者，您可以首先以图形方式创建概念模型，然后生成支持模型的数据库。 无论哪种情况，您都可以在基础数据库更改时自动更新模型，并为应用程序生成对象层代码。 数据库生成和对象层代码生成是可自定义的。  
  
实体框架工具安装的一部分**数据存储和处理**在 Visual Studio 安装程序中的工作负荷。 也可以将它们安装作为 indvidual 组件下**Sdk、 库和框架**类别。  
 
这些是组成 Visual Studio 中的实体框架工具的特定工具：  
  
-   你可以使用[!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]设计器**(**实体设计器**) 可以直观地创建和修改实体、 关联、 映射和继承关系。 **实体设计器**还会生成[!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)]或[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]对象层代码。  
  
-   你可以使用**[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]向导**从现有数据库生成概念模型并将数据库连接信息添加到你的应用程序。  
  
-   你可以使用**创建数据库向导**首先创建概念模型，然后创建支持模型的数据库。  
  
-   你可以使用**模型更新向导**更新概念模型、 存储模型和映射到基础数据库中进行了更改时。  
  
    > [!NOTE]
    >  从 Visual Studio 2010 开始，不支持实体框架工具[!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)]。  
  
这些工具生成或修改.edmx 文件。 此.edmx 文件包含描述概念模型、 存储模型中，以及它们之间的映射的信息。 有关详细信息，请参阅[EDMX](https://msdn.microsoft.com/data/jj650889.aspx)。  
  
[实体框架 Power 工具](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4)帮助你生成应用程序使用实体数据模型。 增强工具可以生成概念模型、 验证现有模型、 生成包含基于概念模型中，对象类的源代码文件和生成源代码文件，其中包含该模型生成的视图。 有关详细信息，请参阅[Pre-Generated 映射视图](https://msdn.microsoft.com/data/dn469601.aspx)。  
  
## <a name="related-topics"></a>相关主题  
  
|标题|描述|  
|-----------|-----------------|  
|[ADO.NET 实体框架](/dotnet/framework/data/adonet/ef/index)|介绍如何使用[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]工具，其中[!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]提供，来创建应用程序。|  
|[实体数据模型](/dotnet/framework/data/adonet/entity-data-model)|提供用于处理上构建应用程序使用的数据链接和信息[!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]。|  
|[实体框架 (EF) 文档）](https://msdn.microsoft.com/library/ee712907(v=vs.113).aspx)|提供视频、 教程和高级的文档帮助你充分利用实体框架的索引。|  
|[ASP.NET 5 应用程序指向新数据库](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|描述如何使用实体框架 7 创建新的 ASP.NET 5 应用程序。|  
  
## <a name="see-also"></a>另请参阅  
 [适用于 NET 的 Visual Studio Data Tools](../data-tools/visual-studio-data-tools-for-dotnet.md)
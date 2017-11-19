---
title: "适用于.NET 的 visual Studio data tools |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 6b48b16d33c62c2d0ca96eb1d55ce22682458029
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="visual-studio-data-tools-for-net"></a>适用于.NET 的 visual Studio data tools
Visual Studio 和.NET Framework 一起提供大量的 API 和工具用于连接到数据库、 在内存中，数据建模和用户界面中显示数据的支持。 提供数据访问功能的.NET Framework 类称为[ADO.NET](https://msdn.microsoft.com/library/e80y5yhx.aspx)。 ADO.NET 中，Visual Studio 中的数据以及最初设计主要是为了支持关系数据库和 XML。 如今，许多 NoSQL 数据库供应商或第三方提供 ADO.NET 提供程序。  
  
[.NET 核心](https://www.dotnetfoundation.org/netcore)支持 ADO.NET 中，数据集和相关的类型除外。 如果你要以.NET 核心为目标，并且需要对象关系映射 (ORM) 层，使用[实体框架核心](https://docs.microsoft.com/ef/core/)。  
  
下图显示的基本体系结构的简化的视图：  
  
![ADO.NET 体系结构](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata ADO.NET 体系结构关系图")  
  
这是典型的工作流：  
  
1.  在本地计算机上安装的开发或测试数据库。 请参阅[安装数据库系统、 工具和示例](../data-tools/installing-database-systems-tools-and-samples.md)。 如果你使用的 Azure 数据服务，则不需要此步骤。  
  
2.  在 Visual Studio 中测试到的数据库 （或服务或本地文件） 的连接。 请参阅[添加新连接](../data-tools/add-new-connections.md)。  
  
3.  （可选）使用工具来生成并配置新的模型。 基于实体框架的模型是新的应用程序的默认建议。 模型中，任何一种使用，是与应用程序交互的数据源。 模型在逻辑上位于数据库或服务和应用程序之间。  请参阅[添加新数据源](../data-tools/add-new-data-sources.md)。  
  
4.  从数据源拖动**数据源**窗口拖到 Windows 窗体、 ASP.NET 或 Windows Presentation Foundation 设计图面上以生成将在你指定的方式向用户显示的数据的数据绑定代码。 请参阅[将控件绑定到 Visual Studio 中的数据](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
5.  添加操作，如业务规则、 搜索和数据验证，或要利用的基础数据库公开的自定义功能的自定义代码。  
  
你可以跳过步骤 3 和程序.NET 应用程序直接向数据库，而不是使用模型发出命令。 在这种情况下，你将找到相关的文档： [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx.aspx)。 请注意，你仍可以使用的数据源配置向导和设计器时填充内存，然后数据将 UI 控件绑定到这些对象中你自己的对象生成数据绑定代码。
  
## <a name="see-also"></a>请参阅
[在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)
---
title: "处理在 n 层应用程序中的数据集 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 85062fe6ea82a73fbc2d64e1d1ce9136d16831cf
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="work-with-datasets-in-n-tier-applications"></a>处理在 n 层应用程序中的数据集
*N 层数据应用程序*是以数据为中心的应用程序分成多个逻辑层 (或*层*)。 换句话说，N 层数据应用程序是分离到多个项目中的应用程序，数据访问层、业务逻辑层和表示层都在各自的项目中。 有关详细信息，请参阅[N 层数据应用程序概述](../data-tools/n-tier-data-applications-overview.md)。  
  
类型化数据集经过改进，现在可以在相互独立的项目中生成 TableAdapter 和数据集类。 这使你可以快速分离各应用程序层及生成 N 层数据应用程序。  
  
N 层中类型化数据集的支持可以迭代开发到 n 层设计的应用程序体系结构。它还会删除手动将代码分离到多个项目的要求。 首先，通过使用设计的数据层**数据集设计器**。 如果你已准备好好应用程序体系结构采用 n 层设计，设置**数据集项目**的数据集以在另一个项目中生成数据集类的属性。  
  
## <a name="reference"></a>参考  
<xref:System.Data.DataSet>  
<xref:System.Data.TypedTableBase%601>  
  
## <a name="see-also"></a>请参阅
[N 层数据应用程序概述](../data-tools/n-tier-data-applications-overview.md)  
[演练：创建 N 层数据应用程序](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
[向 N 层应用程序中的 TableAdapter 添加代码](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[向 N 层应用程序的数据集添加代码](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
[向 N 层数据集添加验证](../data-tools/add-validation-to-an-n-tier-dataset.md)  
[将数据集和 TableAdapter 分离到不同的项目中](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
[分层更新](../data-tools/hierarchical-update.md)  
[Visual Studio 中的数据集工具](../data-tools/dataset-tools-in-visual-studio.md)  
[在 Visual Studio 中访问数据](../data-tools/accessing-data-in-visual-studio.md)  
[创建和配置 Tableadapter](../data-tools/create-and-configure-tableadapters.md)  
[N 层和远程应用程序而 LINQ to SQL](http://msdn.microsoft.com/Library/854a1cdd-53cb-45f5-83ca-63962a9b3598)
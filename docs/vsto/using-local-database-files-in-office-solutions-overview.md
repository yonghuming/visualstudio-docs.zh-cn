---
title: "使用 Office 解决方案概述中的本地数据库文件 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
ms.assetid: 7a920e6b-f0c3-4a62-b5dd-02668a6177b6
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e90143904c8d628e4288e24602907a75ae4bc59
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="using-local-database-files-in-office-solutions-overview"></a>在 Office 解决方案中使用本地数据库文件概述
  Office 解决方案中，可以包括数据库文件，如 SQL Server Express (.mdf) 文件或 Microsoft Office Access (.mdb) 文件。 这使最终用户能够在其中维护中央的数据库不是必需的例如在使用仅一台计算机的本地清单解决方案的情况下对本地数据库进行维护。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="importing-the-database-file-into-a-project"></a>将数据库文件导入项目  
 若要将数据库文件导入你的项目，使用**数据源配置向导**创建数据源基于的数据库文件。 向导将数据库文件和一个类型化数据集添加到你的项目。  
  
## <a name="deploying-the-database-file"></a>部署数据库文件  
 **数据源配置向导**使用相对路径来创建连接到本地数据库文件。 这使您可以将解决方案从一台计算机复制到另一个，如果维护文件的相对位置。  
  
 如果你将你的解决方案部署到服务器，然后将分发到每个最终用户的文档，必须手动分发数据库文件，并将其安装在同一位置相对于文档。 这意味着，最终用户不能将文档移到新位置他或她在计算机上，除非他或她也会移动数据库文件。  
  
## <a name="local-database-files-and-caching-the-dataset"></a>本地数据库文件和缓存数据集  
 在 Microsoft Office Excel 和 Microsoft Office Word 文档级解决方案中，你可以通过将标记该特性的数据集实例中缓存文档中的数据集<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>。 当你将数据库文件添加到你的项目使用**数据源配置向导**，类型化数据集自动添加到你的项目。 很少需要应用<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>到此数据集，因为已存在用户的计算机上本地数据。 有关更多信息，请参见 [Caching Data](../vsto/caching-data.md)。  
  
## <a name="see-also"></a>另请参阅  
 [将数据绑定到 Office 解决方案中的控件](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [如何： 用数据库中的数据填充文档](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [如何： 使用主机控件中的数据更新数据源](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)   
 [缓存数据](../vsto/caching-data.md)  
  
  
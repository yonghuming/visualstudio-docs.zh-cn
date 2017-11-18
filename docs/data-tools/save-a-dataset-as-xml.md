---
title: "将数据集另存为 XML |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 1e41e0481325838b5de60b76ed1c7c1fc617f48e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="save-a-dataset-as-xml"></a>将数据集另存为 XML
可以通过对数据集调用可用 XML 方法访问 XML 数据集中的数据。 若要以 XML 格式保存数据，你可以调用<xref:System.Data.DataSet.GetXml%2A>方法或<xref:System.Data.DataSet.WriteXml%2A>方法<xref:System.Data.DataSet>。  
  
 调用<xref:System.Data.DataSet.GetXml%2A>方法返回一个字符串，包含格式化为 XML 数据集中的所有数据表中的数据。  
  
 调用<xref:System.Data.DataSet.WriteXml%2A>方法可发送到你指定的文件中的 XML 格式的数据。  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>数据数据集作为 XML 保存到变量  
  
-   <xref:System.Data.DataSet.GetXml%2A>方法返回<xref:System.String>。这意味着声明类型的变量的<xref:System.String>并将其分配的结果<xref:System.Data.DataSet.GetXml%2A>方法。  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>若要在数据集中的数据作为 XML 保存到文件  
  
-   <xref:System.Data.DataSet.WriteXml%2A>方法有多个重载。 下面的代码演示如何将数据保存到文件。声明变量并将其分配保存到文件的有效路径。  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## <a name="see-also"></a>另请参阅  
 [将数据保存回数据库](../data-tools/save-data-back-to-the-database.md)
---
title: "如何：将数据集另存为 XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "数据 [Visual Studio], 保存为 XML"
  - "数据集 [Visual Basic], 保存为 XML"
  - "保存数据"
  - "XML [Visual Basic], 数据集"
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：将数据集另存为 XML
可以通过调用数据集上可用的 XML 方法访问该数据集中的 XML 数据。  若要以 XML 格式保存数据，可用调用 <xref:System.Data.DataSet> 的 <xref:System.Data.DataSet.GetXml%2A> 方法或 <xref:System.Data.DataSet.WriteXml%2A> 方法。  
  
 调用 <xref:System.Data.DataSet.GetXml%2A> 方法会返回一个字符串，它包含在格式化为 XML 的数据集中所有数据表的数据。  
  
 调用 <xref:System.Data.DataSet.WriteXml%2A> 方法会将 XML 格式的数据发送给您指定的文件。  
  
### 将数据集中的数据作为 XML 保存到变量中  
  
-   <xref:System.Data.DataSet.GetXml%2A> 方法返回一个 <xref:System.String>，如此声明类型 <xref:System.String> 的变量，并将它分配给 <xref:System.Data.DataSet.GetXml%2A> 方法的结果。  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-cs[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### 将数据集中的数据作为 XML 保存到文件  
  
-   <xref:System.Data.DataSet.WriteXml%2A> 方法有若干次重载。  下面的代码演示如何将数据保存到文件中，如此声明变量并将其分配到要将文件保存到的有效路径。  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-cs[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## 请参阅  
 [DataSet、DataTable 和 DataView](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)   
 [Visual Studio 中的 XML 工具](../xml-tools/xml-tools-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [连接到 Visual Studio 中的数据](../data-tools/connecting-to-data-in-visual-studio.md)   
 [准备应用程序以接收数据](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [将数据获取到应用程序](../data-tools/fetching-data-into-your-application.md)   
 [在 Visual Studio 中将控件绑定到数据](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [在应用程序中编辑数据](../data-tools/editing-data-in-your-application.md)   
 [验证数据](../Topic/Validating%20Data.md)   
 [保存数据](../data-tools/saving-data.md)
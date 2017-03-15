---
title: "关于异常的疑难解答：System.Data.ReadOnlyException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ReadOnlyException 类"
ms.assetid: 1ac5da38-c5af-4fec-8fe1-1b9dd5069e59
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Data.ReadOnlyException
尝试更改只读数据列的值时，将引发 <xref:System.Data.ReadOnlyException> 异常。  
  
## 相关提示  
 **将列更改为读\/写列。**  
 此异常在尝试更改只读数据列中的值时引发。 有关详细信息，请参阅<xref:System.Data.DataColumn>。  
  
 **确保您正在修改正确列中的数据。**  
 此异常在尝试更改只读数据列中的值时引发。 有关详细信息，请参阅<xref:System.Data.DataColumn>。  
  
## 请参阅  
 <xref:System.Data.ReadOnlyException>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)
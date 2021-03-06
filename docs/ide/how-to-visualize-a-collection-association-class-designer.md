---
title: "如何：可视化集合关联（类设计器） | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 53eb6ed7e8025ee6cc9a9a3ee8161078accbc457
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-visualize-a-collection-association-class-designer"></a>如何：可视化集合关联（类设计器）
属于其他类型的集合的属性和字段可在类图上作为集合关联显示。 普通关联可将字段或属性显示为行，此行将拥有的类链接到字段的类型，与此不同，集合关联作为行显示，此行将拥有的类链接到已收集的类型。  
  
### <a name="to-create-a-collection-association"></a>创建集合联合  
  
1.  在代码中，创建一个属性或字段，其本身属于强类型集合。  
  
2.  在类图中扩展类，以便显示属性和字段。  
  
3.  在类中，右键单击该字段或属性，然后选择“显示为集合关联”。  
  
     此属性或字段将显示为链接到已收集类型的关联行。  
  
## <a name="see-also"></a>另请参阅  
 [如何：创建类型之间的关联（类设计器）](../ide/how-to-create-associations-between-types-class-designer.md)   
 [设计类和类型（类设计器）](../ide/designing-classes-and-types-class-designer.md)   
 [查看类型和关系（类设计器）](../ide/viewing-types-and-relationships-class-designer.md)
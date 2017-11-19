---
title: "属性&lt;属性名称&gt;无法删除，因为它参与关联&lt;关联名称&gt;|Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 150d176c105e8368fc97f36a19774824dcb91c3e
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>属性&lt;属性名称&gt;无法删除，因为它参与关联&lt;关联名称&gt;
所选的属性被设置为**关联属性**错误消息中指示的类之间关联。 如果属性参与了数据类之间的关联，则无法删除。  
  
 设置**关联属性**为数据类，可以成功删除删除的所需的属性的另一个属性。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  在 O/R 设计器中选择连接错误消息中指示的数据类的关联连线。  
  
2.  双击该连线以打开**关联编辑器**对话框。  
  
3.  删除从属性**关联属性**。  
  
4.  再次尝试删除该属性。  
  
## <a name="see-also"></a>请参阅
[O/R 设计器消息](../data-tools/o-r-designer-messages.md)  
[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
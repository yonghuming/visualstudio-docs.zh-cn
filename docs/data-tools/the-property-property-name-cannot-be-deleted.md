---
title: "属性&lt;属性名称&gt;无法删除 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: b3a896e64e048a5104bca84b726c730d4d9d524a
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2017
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>属性&lt;属性名称&gt;无法删除
属性\<属性名称 > 无法删除，因为它被设置为**鉴别器属性**之间的继承\<类名称 > 和\<类名称 >  
  
 所选的属性被设置为**鉴别器属性**错误消息中指示的类之间的继承。 如果属性参与数据类之间的继承配置，则无法删除这些属性。  
  
 设置**鉴别器属性**为数据类，可以成功删除删除的所需的属性的另一个属性。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  在 O/R 设计器中选择连接错误消息中指示的数据类的继承连线。  
  
2.  设置**鉴别器**为另一个属性的属性。  
  
3.  再次尝试删除该属性。  
  
## <a name="see-also"></a>请参阅
[O/R 设计器消息](../data-tools/o-r-designer-messages.md)  
[Visual Studio 中的 LINQ to SQL 工具](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
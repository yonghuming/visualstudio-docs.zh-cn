---
title: "如何： 以编程方式在 Outlook 中移动项 |Microsoft 文档"
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
helpviewer_keywords: Outlook folders [Office development in Visual Studio], moving items
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fc7afe28e435e0dcdd58c7403f6282ebf3609a23
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>如何：以编程方式在 Outlook 中移动项
  此示例将从的未读的电子邮件**收件箱**到名为的文件夹**测试**。 此示例仅移动消息包含有词语**测试**中`Subject`字段。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>示例  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   Outlook 邮件文件夹名为**测试**。  
  
-   电子邮件到达以单词**测试**中`Subject`字段。  
  
## <a name="see-also"></a>另请参阅  
 [使用文件夹](../vsto/working-with-folders.md)   
 [如何： 以编程方式检索按名称的文件夹](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何： 以编程方式在特定文件夹中搜索](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [如何：以编程方式在收到电子邮件后执行操作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  
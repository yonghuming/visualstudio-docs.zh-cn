---
title: "如何： 以编程方式发送电子邮件 |Microsoft 文档"
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
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 98b0eefafa86fdaf8f7a664ac75a2f7c71a43549
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-send-e-mail"></a>如何： 以编程方式发送电子邮件  
  此示例将一封电子邮件发送给具有域名的联系人**example.com**电子邮件地址中。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>示例  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   具有域名的联系人**example.com**电子邮件地址中。  
  
## <a name="robust-programming"></a>可靠编程  
 不删除搜索域名称的筛选器代码**example.com**。如果删除筛选器，你的解决方案将向你的联系人的所有发送电子邮件。  
  
## <a name="see-also"></a>另请参阅  
 [使用邮件项](../vsto/working-with-mail-items.md)   
 [如何： 以编程方式创建电子邮件项](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [如何： 以编程方式访问 Outlook 联系人](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [如何：以编程方式在收到电子邮件后执行操作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  
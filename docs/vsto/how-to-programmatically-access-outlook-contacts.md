---
title: "如何： 以编程方式访问 Outlook 联系人 |Microsoft 文档"
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
helpviewer_keywords: contacts [Office development in Visual Studio], searching
ms.assetid: ea2297ea-6802-40e4-af1a-1e511a71ec75
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8ee2c597c1a3b6a7c068c8206a87195779877461
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>如何：以编程方式访问 Outlook 联系人
  本示例查找其姓氏包含指定的搜索字符串的所有联系人。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>示例  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   联系人姓氏和名字包含字符串"**Na"** (例如，Tzipi Butnaru) 中**联系人**文件夹。  
  
## <a name="see-also"></a>另请参阅  
 [使用联系人项](../vsto/working-with-contact-items.md)   
 [如何： 以编程方式向 Outlook 联系人添加项](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [如何： 以编程方式搜索特定联系人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [如何： 以编程方式在联系人中电子邮件地址搜索](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [如何：以编程方式删除 Outlook 联系人](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  
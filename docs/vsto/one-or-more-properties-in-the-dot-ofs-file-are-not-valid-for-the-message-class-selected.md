---
title: ".Ofs 文件中的一个或多个属性对于选定的消息类不可用 |Microsoft 文档"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
ms.assetid: ca9e2ec1-df96-45ca-9611-cec47edfe1e4
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ddaad272326c4cd77e0e54bd7216974181c77a72
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>.ofs 文件中的一个或多个属性对于选定的消息类无效
  如果导入在 Outlook 中设计的窗体区域，但是该窗体区域的一个或多个字段与在“新建窗体区域”  向导最后一页上选择的邮件类不兼容，则会出现此错误。  
  
 例如，你可能在“新建窗体区域”  向导最后一页上选择了“任务(IPM.Task)”  。 如果窗体区域包含“办公地址”  字段，则会出现此错误，这是因为任务是没有办公地址的。 因此，“办公地址”字段  与 IPM.Task 邮件类不兼容。  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
-   在“新建窗体区域”  向导最后一页上，选择与窗体区域上的字段兼容的邮件类。  
  
-   在 Outlook 的窗体设计器中，删除与要在“新建窗体区域”  向导最后一页上选择的邮件类不兼容的字段。  
  
## <a name="see-also"></a>另请参阅  
 [演练：导入在 Outlook 中设计的窗体区域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  
---
title: "如何： 设置以便为 Office 解决方案的配置信息 |Microsoft 文档"
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
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a8c2e0a904ad3cdbef3e70072d263cc26274de52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>如何：为 Office 解决方案设置配置信息
  配置文件可用于配置特定于你的 Office 解决方案的设置。 你可以指定设置，如程序集绑定策略、 远程处理对象、 调试和跟踪设置。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>若要添加到你的 Office 项目的配置文件  
  
1.  在 **“项目”** 菜单上，单击 **“添加新项”**。  
  
2.  在**类别**窗格中，单击**常规**。  
  
3.  在**模板**窗格中，选择**应用程序配置文件**。  
  
4.  在**名称**框中，键入相同的名称为程序集加上扩展名.config。例如，调用 ExcelWorkbook1.dll Excel 项目程序集的配置文件将被命名为 ExcelWorkbook1.dll.config。  
  
5.  单击 **“添加”**。  
  
6.  创建你根据应用程序配置文件架构的配置文件。 有关详细信息，请参阅[的.NET Framework 配置文件架构](/dotnet/framework/configure-apps/file-schema/index)。  
  
 有配置文件中使用的 Office 项目没有特别的注意事项。  
  
## <a name="see-also"></a>另请参阅  
 [.NET Framework 的配置文件架构](/dotnet/framework/configure-apps/file-schema/index)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)  
  
  
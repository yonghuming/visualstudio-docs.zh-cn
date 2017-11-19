---
title: "合作开发 Office 解决方案 |Microsoft 文档"
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
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
ms.assetid: c493354b-17d3-4e50-85f0-968b104bc978
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 94313e1e7cb8d6f36c5c8bfb505d280f4e235a3b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="collaborative-development-of-office-solutions"></a>合作开发 Office 解决方案
  多个开发人员可以处理 Office 项目中与它们在其他 Visual Studio 项目协作的方式相同。 即使在不同位置中安装 Office，visual Studio 正确定位每台计算机上的 Microsoft Office 安装。 但是，有需要注意的一些重要注意事项。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>调试属性不会将共享  
 调试属性不在源控件下的多个用户中共享。 Visual Basic 和 Visual C# 项目的调试属性存储在特定于用户的文件中 (*ProjectName*。 vbproj.user 或*ProjectName*。 csproj.user)，但此文件不在源代码管理下。 如果有多个用户正在调试，则每个用户都必须手动输入调试属性。  
  
 如果项目驻留在网络共享，而不是在源代码管理中，必须执行一些额外的步骤启用合作的开发人员打开解决方案，然后测试程序集。  
  
## <a name="source-control-requires-checking-out-all-files"></a>源代码管理需要签出的所有文件  
 如果你的项目使用源代码管理，你应查看下中的代码文件的文件的所有**解决方案资源管理器**（如对 ThisDocument、 ThisWorkbook 或 ThisAddIn 代码文件） 每次更改代码文件中，即使默认情况下隐藏的文件。 如果检查出仅顶级代码文件时，所做的更改可能会丢失。  
  
 进行更改后，检查的所有文件备份中。 有关项目中的隐藏的代码文件的详细信息，请参阅[Visual Studio 环境中的 Office 项目](../vsto/office-projects-in-the-visual-studio-environment.md)。  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>在网络上的非正式协作的安全性  
 在网络位置的所有文档级解决方案 (如\\ \\ *Servername*\\*Sharename*)，必须将完全限定的位置添加到你正在使用 Microsoft Office 应用程序中的受信任的文件夹列表。 选择选项以包括的主文件夹下的子目录或专门添加调试和生成文件夹到受信任的文件夹列表。 有关如何执行此操作的详细信息，请参阅[向文档授予信任](../vsto/granting-trust-to-documents.md)。  
  
 在生成时自动生成的临时证书不受密码保护。 证书中包含开发人员的登录名和其他个人信息。 如果部署由临时证书签名的自定义项，其他人可以访问此信息。  
  
## <a name="see-also"></a>另请参阅  
 [保护 Office 解决方案](../vsto/securing-office-solutions.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [生成 Office 解决方案](../vsto/building-office-solutions.md)  
  
  
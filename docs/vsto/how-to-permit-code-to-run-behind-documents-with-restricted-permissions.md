---
title: "如何：允许代码在具有受限制权限的文档的后台运行"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "代码 [Visual Studio 中的 Office 开发], 在限制的文档后运行"
  - "文档 [Visual Studio 中的 Office 开发], 受限权限"
  - "信息权限管理 [Visual Studio 中的 Office 开发]"
  - "IRM [Visual Studio 中的 Office 开发]"
  - "Office 文档 [Visual Studio 中的 Office 开发, 受限权限"
  - "权限 [Visual Studio 中的 Office 开发]"
ms.assetid: d037eae5-cf83-4be0-85ba-05e9f7d570e1
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# 如何：允许代码在具有受限制权限的文档的后台运行
  您可以使用 Microsoft Office 的信息权限管理 \(IRM\) 功能来限定文档或工作簿的权限。  默认情况下，不允许受限 Microsoft Office Word 文档或 Microsoft Office Excel 工作簿后面的代码运行。  可以对此默认设置进行更改，以使您的托管代码扩展能够访问该对象模型，并使解决方案能够工作。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 您必须是该文档或工作簿的作者或具有“完全控制”访问权限，才能更改权限设置。  
  
### 允许代码使用受限权限在文档的后台运行  
  
1.  在 Word 或 Excel 中打开文档或工作簿。  
  
2.  单击 **文件** 选项，指向 **准备**，指向 **限制权限**，然后单击 **限制访问**。  
  
    > [!NOTE]  
    >  第一次使用时，会提示您安装 Windows 权限管理客户端。  安装了客户端后，您可能需要重复这些步骤。  
  
3.  在**“权限”**对话框中，选择**“限制对此文档的权限”**，然后单击**“更多选项”**。  
  
4.  在**“用户的附加权限”**下，选择**“以编程方式访问内容”**。  
  
 Word 或 Excel 将允许对该对象模型进行编程访问。  
  
## 请参阅  
 [信息权限管理与托管代码扩展概述](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [文档级解决方案中的文档保护](../vsto/document-protection-in-document-level-solutions.md)   
 [Office 文档的密码保护](../vsto/password-protection-on-office-documents.md)   
 [设计和创建 Office 解决方案](../vsto/designing-and-creating-office-solutions.md)   
 [保护 Office 解决方案的安全](../vsto/securing-office-solutions.md)   
 [部署 Office 解决方案](../vsto/deploying-an-office-solution.md)  
  
  
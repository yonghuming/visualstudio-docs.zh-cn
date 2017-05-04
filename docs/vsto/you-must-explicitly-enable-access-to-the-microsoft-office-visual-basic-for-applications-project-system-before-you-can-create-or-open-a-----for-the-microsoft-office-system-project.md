---
title: "必须显式启用对 Microsoft Office Visual Basic for Applications 项目系统的访问，然后才能创建或打开 Visual Studio Tools for the Microsoft Office System 项目 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vst.project.vbawrongversion"
  - "VST.Project.VBASecurityGenericError"
  - "VST.Project.VBASecurityPermissions"
  - "VST.SelectDocWizard.MissingCOM"
  - "VST.Project.VBASecurityNotSet"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 538021e6-1776-453d-9899-d7fca2f1f58f
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# 必须显式启用对 Microsoft Office Visual Basic for Applications 项目系统的访问，然后才能创建或打开 Visual Studio Tools for the Microsoft Office System 项目
  尽管 Office 开发项目并不使用 Visual Basic for Applications，但这些项目仍需访问 Microsoft Office Word 和 Microsoft Office Excel 中的 Visual Basic for Applications 项目系统。  Visual Basic 和 C\# 项目中控件的设计时支持均需依赖 Visual Basic for Applications 项目系统。  
  
 有些 Microsoft Office 宏病毒会尝试自动运行 Visual Basic for Applications 项目系统来进行传播。  如果启用对 Visual Basic for Applications 项目系统的访问，就失去了帮助防止宏病毒传播的安全保护。  不过，由于正常的宏安全性设置仍然起作用，因此你为 Office 应用程序维护的宏安全级别和受信任的发行者列表将确定是否有任何宏可以在计算机上运行。  
  
> [!NOTE]  
>  这仅适用于开发计算机。  最终用户计算机无需启用此选项即可运行 Office 解决方案。  
  
 值得注意的是，如果计算机此前已经感染宏病毒，则禁用对 Visual Basic for Applications 项目系统的访问本身并不会防止感染病毒，而只能帮助阻止某些病毒传播到其他文档。  默认情况下该选项为禁用状态，从而为你的计算机提供一层额外保护，但如果遵循以下最佳安全做法，即使启用该选项，也不会使你的计算机更易受病毒感染。  
  
 应对 Office 宏病毒的最佳做法是采用“高”或“非常高”安全级别运行 Office，仅信任来自已知的、经过验证的来源的宏，并且始终应用最新的安全修补程序和病毒扫描程序。  
  
 有关保护 PC 免受病毒和其他恶意代码攻击的详细信息，请参阅 [http:\/\/www.microsoft.com\/protect](http://www.microsoft.com/protect)。  
  
 可以手动启用或禁用**“信任对于‘Visual Basic 项目’的访问”**选项。  
  
 如果看到 VBA 或 COM 错误，则可以修复 Office 的安装。  
  
### 启用或禁用对 Visual Basic 项目的访问  
  
1.  在 Word 或 Excel 的**“工具”**菜单上指向**“宏”**，然后单击**“安全性”**。  
  
2.  在**“安全性”**对话框中，单击**“受信任的发行者”**选项卡。  
  
3.  选中**“信任对于‘Visual Basic 项目’的访问”**复选框以启用此选项，或者清除该复选框以禁用此选项。  
  
4.  单击“确定”。  
  
### 设置 Office 宏安全级别  
  
1.  在 Word 或 Excel 的**“工具”**菜单上指向**“宏”**，然后单击**“安全性”**。  
  
2.  在**“安全级”**选项卡上选择所需的设置。  
  
     **“安全级”**选项卡中包含有关各个级别的详细信息。  有关详细信息，请参阅“Office 帮助”中的“宏安全级”主题。  
  
### 通过 2007 Microsoft Office 系统安装 VBA  
  
1.  在控制面板中，运行**“添加或删除程序”**或**“程序和功能”**。  
  
2.  在**“当前安装的程序”**列表中选择 Office。  
  
3.  单击**“更改”**。  
  
4.  选择**“添加或移除功能”**，然后单击**“继续”**。  
  
5.  选择**“选择高级应用程序自定义”**，然后单击**“下一步”**。  
  
6.  在**“选择应用程序和工具的更新选项”**列表中展开**“Office 共享功能”**。  
  
7.  打开**“Visual Basic for Applications”**旁边的下拉菜单，然后单击**“从本机运行”**。  
  
8.  单击**“继续”**。  
  
9. 单击**“关闭”**。  
  
### 修复 Office 安装  
  
1.  在控制面板中，运行**“添加或删除程序”**或**“程序和功能”**。  
  
2.  在**“当前安装的程序”**列表中选择 Office 的版本。  
  
3.  单击**“更改”**。  
  
4.  选择**“重新安装或修复”**，然后单击**“下一步”**。  
  
5.  选择**“检测并修复 Office 安装中的错误”**，然后单击**“安装”**。  
  
## 请参阅  
 [保护 Office 解决方案的安全](../vsto/securing-office-solutions.md)  
  
  
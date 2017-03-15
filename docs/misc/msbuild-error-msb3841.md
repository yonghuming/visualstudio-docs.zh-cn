---
title: "MSBuild 错误 MSB3841 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.ResolveSDKReference.InvalidDependencyInPlatform"
ms.assetid: 80ed22a1-bd62-4ace-892f-6b6009dff8e5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3841
**MSB3841：SDK“{1}”依赖于 SDK“{0}”，后者与面向平台版本“{2}”的项目不兼容。**  
  
 当项目具有与其所面向的平台不兼容的依赖项时，MSBuild 将生成此错误。  依赖于不兼容的依赖项可能导致运行时出现故障或意外的应用行为  
  
### 为项目引用更正此错误  
  
1.  面向 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 应用商店项目的 Visual Basic、C\#、C\+\+ 和 JavaScript 项目不能引用面向 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 的 C\+\+ Windows 应用商店项目，因为这将导致运行时问题。  如果应用中的任何项目面向 [!INCLUDE[win81](../debugger/includes/win81_md.md)]，且你的应用由 C\+\+Windows 应用商店项目构成，则将需要执行以下步骤：  
  
2.  将应用中的所有项目的目标重定到 [!INCLUDE[win81](../debugger/includes/win81_md.md)]。  要实现此目标，可右键单击应用中的每个项目，选择**“重定目标到 Windows 8.1”**命令，然后在**“复查项目和解决方案更改”**对话框中单击**“确定”**。  
  
3.  右键单击依赖于 C\+\+ Windows 应用商店项目的每个 Visual Basic、C\# 和 JavaScript 项目，选择**“添加引用”**，依次转到**“Windows”**选项卡、**“扩展”**子选项卡，取消选中**“Microsoft Visual C\+\+ 运行时包 v11.0”**并选中**“Microsoft Visual C\+\+ 运行时包 v12.0”**，然后单击**“确定”**。  
  
4.  面向 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 的 Visual Basic、C\# 和 JavaScript Windows 应用商店项目可以引用面向 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 的 Visual Basic 和 C\# Windows 应用商店项目，前提是 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 应用商店项目不使用 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 中已弃用的 API。  请参阅[将 Windows 8 应用迁移到 Windows 8.1 预览版](http://msdn.microsoft.com/library/windows/apps/dn263113.aspx)，以便确定从 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 项目引用时，[!INCLUDE[win8](../debugger/includes/win8_md.md)] 应用商店项目是否继续按预期方式运行。  
  
     [!INCLUDE[win8](../debugger/includes/win8_md.md)] 应用商店项目不能依赖面向 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 的 Windows 应用商店项目或二进制文件。  
  
### 为扩展 SDK 引用更正此错误  
  
1.  面向 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 的 Visual Basic、C\#、C\+\+ 和 JavaScript Windows 应用商店项目不能引用依赖于 Microsoft Visual C\+\+ 运行时包 v11.0 的扩展 SDK，因为这会导致运行时问题。  可以通过以下方式查明扩展 SDK 是否依赖于 Microsoft Visual C\+\+ 运行时包 v11.0：创建新的 C\# Windows 应用商店项目，右键单击该项目并选择**“添加引用”**，依次转到**“Windows”**选项卡、**“扩展”**子选项卡，选择该扩展 SDK 并查看**“引用管理器”**的右窗格中是否将**“Microsoft.VCLibs, version \= 11.0”**列为依赖项。  
  
     面向 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 的 Visual Basic、C\# 和 JavaScript Windows 应用商店项目可以引用不依赖于 Microsoft Visual C\+\+ 运行时包 v11.0 的扩展 SDK，前提是这些扩展 SDK 不使用 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 中已弃用的 API。  请检查扩展 SDK 供应商站点，以确定它是否可被面向 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 的应用商店项目引用。  
  
     如果确定你的应用所引用的扩展 SDK 不受支持，则需执行以下步骤：  
  
2.  查看导致错误的项目的名称。  项目所面向的平台记录在项目名称旁的括号中。  例如，**“MyProjectName \(Windows 8.1\)”**表示项目 MyProjectName 面向 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 平台版本。  
  
3.  转到拥有不受支持的扩展 SDK 的供应商站点，安装具有与你的项目所面向的平台版本兼容的依赖项的扩展 SDK 版本。  
  
4.  如果之前安装的扩展 SDK 依赖其他扩展 SDK，请转到拥有这些依赖项的供应商站点，并安装与你的项目所面向的平台版本兼容的依赖项版本。  
  
    > [!NOTE]
    >  如果你的项目面向 [!INCLUDE[win81](../debugger/includes/win81_md.md)] 且之前安装的扩展 SDK 依赖 Microsoft Visual C\+\+ 运行时包，则与 Windows 8.1 兼容的 Microsoft Visual C\+\+ 运行时包版本是 v12.0，并且随 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 一同安装。  
  
    > [!NOTE]
    >  若要了解之前安装的扩展 SDK 是否依赖其他扩展 SDK，可重启 Visual Studio，创建一个新的 C\# Windows 应用商店项目，右键单击该项目并选择**“添加引用”**，依次转到**“Windows”**选项卡、**“扩展”**子选项卡，选择该扩展 SDK 并查看**“引用管理器”**的右窗格。  如果具有依赖关系，则将在该位置列出依赖关系。  
  
5.  重启 Visual Studio 并打开你的应用。  
  
6.  右键单击导致错误的项目，并选择 Visual Basic、C\# 或 JavaScript 项目下的**“添加引用”**，或 C\+\+ 项目下的**“引用”**。  对于 C\+\+ 项目，随后单击“添加新引用”按钮。  
  
7.  单击**“Windows”**选项卡，然后单击**“扩展”**子选项卡。  取消选中旧扩展 SDK 旁边的复选框，然后选中新扩展 SDK 旁边的复选框。  单击“确定”。
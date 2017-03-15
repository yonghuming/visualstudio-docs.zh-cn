---
title: "“未安装项目的目标框架”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.TargetFrameworkNotFound"
ms.assetid: 64ce8743-d5bd-447e-ba10-54b2aafe109e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# “未安装项目的目标框架”对话框
你已经打开了一个目标是你的计算机上未安装的框架的项目。 若要继续，必须在此对话框中选择其中一个选项。  
  
> [!NOTE]
>  无论何时下载并安装一个新的框架，都必须重新启动 Visual Studio。  
  
## Visual Basic 和 Visual C\#  
 如果打开了一个 Visual Basic 或 Visual C\# 项目，则选择以下选项之一。  
  
 **将目标更改为 .NET Framework 4.5。之后可以改回为 .NET Framework***版本*。  
 将项目重定目标到 .NET Framework 4.5。 之后可以重新安装以前的版本，然后重定项目目标。  
  
 **下载 .NET Framework \<版本\> 的目标包。该项目将不会更改。**  
 打开 Microsoft 下载中心网站，你可以在其中下载所需的 .NET Framework 的版本。 项目从解决方案中卸载。 下载并安装所需的框架后，必须重新启动 Visual Studio，然后重新打开该项目。  
  
 **“不要加载项目”。**  
 使该项目从解决方案中卸载。 可以之后安装所需的框架，然后重新加载项目。  
  
## Visual C\+\+  
 如果打开了一个 Visual C\+\+ 项目，则选择以下选项之一。  
  
 **下载 .NET Framework *版本* 的目标包 。该项目将不会更改。**  
 打开 Microsoft 下载中心网站，你可以在其中下载所需的 .NET Framework 的版本。 下载完成后，则项目将重定目标到该版本。 项目从解决方案中卸载。 下载并安装所需的框架后，必须重新启动 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，然后重新打开该项目。  
  
 **“不要加载项目”。**  
 使该项目从解决方案中卸载。 可以之后安装所需的框架，然后重新加载项目。  
  
## 请参阅  
 [如何：面向 .NET Framework 的某个版本](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [.NET Framework 目标错误疑难解答](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [添加引用](/visual-cpp/ide/adding-references-in-visual-cpp-projects)
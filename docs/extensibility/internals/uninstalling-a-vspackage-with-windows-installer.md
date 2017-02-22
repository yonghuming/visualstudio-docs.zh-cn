---
title: "卸载使用 Windows Installer VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "包卸载"
  - "Vspackage 卸载"
  - "卸载 Vspackage"
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 卸载使用 Windows Installer VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

大多数情况下，Windows 安装程序可以将卸载你的 VSPackage 只需通过"撤消"那样来安装你的 VSPackage。 自定义操作中所述 [必须在安装后运行的命令](../../extensibility/internals/commands-that-must-be-run-after-installation.md) 必须同时卸载后运行。 由于指向 devenv.exe 的调用就在安装和卸载的情况下了 InstallFinalize 标准操作之前进行，所以 CustomAction 和 InstallExecuteSequence 表条目用作这两种情况。  
  
> [!NOTE]
>  运行 `devenv /setup` 卸载 MSI 包之后。  
  
 作为一般规则是，如果将自定义操作添加到 Windows Installer 程序包时，您必须处理这些操作期间卸载和回滚。 如果添加自定义操作以便自行注册你的 VSPackage，例如，必须添加要先注销，太的自定义操作。  
  
> [!NOTE]
>  使用户能够安装你的 VSPackage，然后卸载版本的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 与它已集成。 可以帮助确保你的 VSPackage 卸载工作在这种情况下不在运行具有依赖项的代码的自定义操作，从而 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 处理启动条件在卸载时  
 LaunchConditions 标准操作读取 LaunchCondition 表以显示错误的行不满足的条件时消息。 启动条件通常用来确保已满足系统要求，则可以通常跳过启动条件在卸载过程通过添加条件，如 `NOT Installed`, ，LaunchCondition 表的 LaunchConditions 一行。  
  
 一种替代方法是添加 `OR Installed` 来启动卸载过程并不重要的条件。 这将确保该条件在卸载期间始终为 true，并且因此不会显示启动条件错误消息。  
  
> [!NOTE]
>  `Installed` 是 Windows 安装程序将设置当它检测到你的 VSPackage，已安装在系统上的属性。  
  
## 请参阅  
 [Windows Installer](http://msdn.microsoft.com/zh-cn/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [检测系统要求](../../extensibility/internals/detecting-system-requirements.md)
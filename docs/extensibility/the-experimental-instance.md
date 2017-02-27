---
title: "实验实例 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "实验性生成"
  - "Vspackage，实验性生成"
  - "VSIP，实验性生成"
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# 实验实例
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

为了保护您从未经测试的应用程序可以更改此报表的 Visual Studio 开发环境，VSSDK 提供了可用来进行试验的实验性空间。 与往常一样，使用 Visual Studio 开发新应用程序，但使用此实验实例来运行。  
  
 有一个 VSIX 包每个应用程序将启动在调试模式下的 Visual Studio 实验实例。  
  
 如果您想要启动 Visual Studio 的实验实例特定的解决方案之外，请在命令窗口中运行以下命令:  
  
 "*\< visual studio 安装路径 \>*\\Common7\\IDE\\devenv.exe"RootSuffix Exp  
  
> [!NOTE]
>  实验实例写入到注册表 `<version number>Exp` 和 `<version number>Exp_Config` 节点。 例如 Visual Studio 2015 实验注册表区域是  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` 和 `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 我们建议您在开发时，在实验实例中运行您的扩展。 当您部署该扩展时，它在开发实例中运行。 有关注册应用程序的详细信息，请参阅 [注册 Vspackage](../extensibility/internals/registering-vspackages.md)。
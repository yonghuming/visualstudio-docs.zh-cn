---
title: "实验实例 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2de242ed974716b0ba00918d30bc2679a36420fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="the-experimental-instance"></a>实验实例
为了防止未经测试的应用程序可能会更改它从 Visual Studio 开发环境，VSSDK 提供可用于试验的实验空间。 像往常一样，使用 Visual Studio 开发新应用程序，但你通过使用此实验实例运行它们。  
  
 具有 VSIX 包每个应用程序将启动在调试模式下的 Visual Studio 实验实例。  
  
 如果你想要启动特定的解决方案之外的 Visual Studio 实验实例，请在命令窗口运行以下命令：  
  
 "*\<Visual studio 安装路径 >*\Common7\IDE\devenv.exe"RootSuffix Exp  
  
> [!NOTE]
>  实验实例写入到下面的注册表`<version number>Exp`和`<version number>Exp_Config`节点。 例如 Visual Studio 2015 实验性注册表区域是  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` 和 `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 我们建议在开发时，在实验实例中运行你的扩展。 当你部署扩展时，它在开发实例中运行。 有关注册应用程序的详细信息，请参阅[注册 Vspackage](../extensibility/internals/registering-vspackages.md)。
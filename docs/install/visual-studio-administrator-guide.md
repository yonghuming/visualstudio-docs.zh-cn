---
title: "Visual Studio 管理员指南 | Microsoft Docs"
ms.custom: ""
ms.date: "01/12/2017"
ms.prod: "visual-studio-dev15"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "网络安装, Visual Studio"
  - "管理员指南, Visual Studio"
  - "安装 Visual Studio, 管理员指南"
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
caps.handback.revision: 68
---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017-rc"></a>适用于 Visual Studio 2017 RC 的 Visual Studio 管理员指南

只要每台目标计算机都满足[最低安装要求](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs)，就可以在网络上部署 Visual Studio。 可以通过使用 --layout 开关运行安装文件（如[创建 Visual Studio 的脱机安装](create-an-offline-installation-of-visual-studio.md)页所述），然后将其从本地计算机复制到网络共享来创建一个网络共享。   

 请注意，从网络共享进行安装会“记住”它们的源位置。 这意味着客户端计算机的修复可能需要返回最初从中安装客户端的网络共享。 请仔细选择网络位置，使其符合在组织中运行的 Visual Studio 2017 客户端的预期生存期。  

 > [!IMPORTANT]
 > 虽然一般情况下支持在生产环境中使用 Visual Studio 2017 RC，但安装 UI 中标记为“预览”的工作负载和组件不支持在生产环境中使用。

## <a name="see-also"></a>另请参阅
* [安装 Visual Studio 2017 RC](install-visual-studio.md)
* [使用命令行参数安装 Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md)
* [创建 Visual Studio 2017 RC 的脱机安装](create-an-offline-installation-of-visual-studio.md)
* [如何报告 Visual Studio 2017 RC 的问题](../ide/how-to-report-a-problem-with-visual-studio-2017.md)



<!--HONumber=Feb17_HO4-->



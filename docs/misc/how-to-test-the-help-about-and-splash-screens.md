---
title: "如何：测试帮助主题和初始屏幕 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "“关于”对话框"
  - "VSPackage, 初始屏幕"
  - "VSPackage, 外观方案"
ms.assetid: 2b959fa4-56d3-44f4-8c2d-9ea2e6fb269d
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# 如何：测试帮助主题和初始屏幕
在实现 **帮助** 之后，并且初始屏幕支持，可以在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]的实现。  
  
### 测试有关对话框的帮助  
  
1.  从 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令提示处，运行带有 **\/setup** 开关的 devenv.exe。  若要运行在实验环境中，键入:  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     ，才可以更改 **帮助** 屏幕信息时**注意**，必须重复此步骤。  
  
2.  运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在注册表根与前面所述，但是，不 **\/setup** 开关:  
  
     **devenv \/rootsuffix Exp**  
  
3.  在 **帮助** 菜单上，单击 **有关 Microsoft Visual Studio**。  
  
     VSPackage 的名称出现在 **安装的产品** 列表。  
  
4.  选择 VSPackage 从列表。  
  
     VSPackage 产品信息显示在 **产品详细信息** 文本框。  
  
### 测试初始屏幕  
  
1.  运行带有 **\/setup** 开关的 devenv.exe。  若要运行在实验环境中，键入:  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     ，才可以更改初始屏幕信息时**注意**，必须重复此步骤。  
  
2.  运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在注册表根与前面所述，但是，与 **\/splash** 开关而不是 **\/setup** 开关。  
  
     **devenv \/rootsuffix Exp \/splash**  
  
     VSPackage 产品信息和徽标出现在初始屏幕上。  
  
## 请参阅  
 [Vspackage 外观方案](/visual-cpp/misc/vspackage-branding)
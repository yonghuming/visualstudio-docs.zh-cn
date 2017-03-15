---
title: "MSBuild 错误 MSB3126 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.FileAssociationsNotInstalled"
helpviewer_keywords: 
  - "MSB3126"
ms.assetid: 0c92cbb6-9100-4433-8113-f2f3a1432243
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3126
**MSB3126: 应用程序正在使用文件关联，但未标记为安装。  文件关联无法用于未安装的应用程序\(如在 Web 浏览器中承载的应用程序\)。**  
  
 当应用程序配置为使用文件关联，但该应用程序的安装模式设置为仅限联机状态时，会发生此错误。  由于仅限联机状态的应用程序通常在浏览器中运行，因此文件关联不可用。  
  
### 更正此错误  
  
-   将**“安装模式和设置”**设置为**“该应用程序也可以脱机使用\(可以从“开始”菜单启动\)”**。  有关更多信息，请参见[如何：指定 ClickOnce 脱机或联机安装模式](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)。  
  
## 请参阅  
 [“项目设计器”\-\>“发布”页](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)
---
title: "如何：生成到公共输出目录 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "生成 [Visual Studio], 公共目录"
  - "公共目录"
  - "输出目录"
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：生成到公共输出目录
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

默认情况下，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 会在解决方案中每个项目自己的文件夹中生成项目。  可以更改项目的生成输出路径，以强制将所有输出放入同一个文件夹中。  
  
### 将所有解决方案输出放入一个公共目录中  
  
1.  单击解决方案中的某个项目。  
  
2.  在**“项目”**菜单上，单击**“属性”**。  
  
3.  根据项目的类型，单击**“编译”**选项卡或**“生成”**选项卡，然后将**“输出路径”**设置为用于解决方案中所有项目的文件夹。  
  
4.  对解决方案中的所有项目重复步骤 1\-3。  
  
## 请参阅  
 [在 Visual Studio 中构建应用程序](../ide/compiling-and-building-in-visual-studio.md)   
 [如何：更改生成输出目录](../ide/how-to-change-the-build-output-directory.md)
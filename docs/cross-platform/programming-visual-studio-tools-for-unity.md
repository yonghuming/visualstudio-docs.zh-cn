---
title: "Visual Studio Tools for Unity 编程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "crdun"
manager: "crdun"
---
# Visual Studio Tools for Unity 编程
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本部分将介绍使用 Visual Studio Tools for Unity API 的示例。  
  
## 示例  
 下面是一些演示 Visual Studio Tools for Unity ApI 使用方法的示例。  
  
### 自定义 VSTU 创建的项目文件  
 Visual Studio Tools for Unity 在项目文件生成期间提供 Unity 样式回调。  若要了解每当项目文件重新生成时可以如何修改它，请参阅[示例：项目文件生成](../cross-platform/customize-project-files-created-by-vstu.md)。  
  
### 与 VSTU 共享 Unity 日志回调  
 Visual Studio Tools for Unity 对 Unity 注册了一个日志回调，能够将其控制台流式传输到 Visual Studio。  如果编辑器脚本也对 Unity 注册了一个日志回调，则 VSTU 回调可能会妨碍此回调。  若要了解可以如何与 VSTU 共享 Unity 日志回调，请参阅[示例：日志回调](../cross-platform/share-the-unity-log-callback-with-vstu.md)。
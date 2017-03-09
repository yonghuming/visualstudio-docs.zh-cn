---
title: "Could not instantiate the licenses processor | Microsoft Docs"
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
  - "vs.tasklisterror.no_licx_generator"
ms.assetid: 9e95d590-f41f-4cfa-bc73-fadeacfdb879
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Could not instantiate the licenses processor
未能实例化用于将 .licx 文件转换为二进制资源的工具。  
  
 作为编译的一部分，项目系统将文本 .licx 文件转换为二进制资源，此二进制资源提供对 .NET 控件授权的支持。  然后该二进制资源将被嵌入到项目输出中。  
  
 若发生此错误，则生成进程将会失败。  
  
 每当将一个授权控件添加到窗体时，Windows 窗体设计器就会自动生成或更新 .licx 文件。  每个项目都有一个 .licx 文件；它总在根文件夹中，而且始终命名为 Licenses.licx。  
  
 **更正此错误**  
  
-   重新安装 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## 请参阅  
 [如何：授予组件和控件许可权限](../Topic/How%20to:%20License%20Components%20and%20Controls.md)
---
title: "Unable to read the resource information from the licx file | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.fail_reading_licx_file"
ms.assetid: e59f0965-fa1c-4852-bd39-63430d5b7d9f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to read the resource information from the licx file
项目系统未能读取 .licx 文件。  作为准备许可证的一部分，项目系统会将文本 .licx 文件转换为适于与 COM\+ 授权模型一起使用的二进制资源文件。  
  
 每当将一个授权控件添加到窗体时，Windows 窗体设计器就会自动生成或更新 .licx 文件。  每个项目都有一个 .licx 文件；它总在根文件夹中，而且始终命名为 Licenses.licx。  
  
 此错误的某些原因是：  
  
-   权限被拒绝。  
  
-   与 Web 项目的 Web 服务器失去通信。  
  
 若发生此错误，则生成进程将会失败。  
  
## 请参阅  
 [如何：授予组件和控件许可权限](../Topic/How%20to:%20License%20Components%20and%20Controls.md)
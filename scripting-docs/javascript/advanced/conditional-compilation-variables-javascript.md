---
title: "条件编译变量 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "条件编译, 变量"
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 条件编译变量 (JavaScript)
以下预定义变量可用于条件编译。  如果变量不为 **true**，则该变量是未定义的，并且在被访问时其行为与 `NaN` 相同。  
  
> [!WARNING]
>  Internet Explorer 11 之前的所有版本的 Internet Explorer 都支持条件编译。  从 Internet Explorer 11 标准模式开始，[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]应用不支持条件编译。  
  
## 变量  
  
|变量|说明|  
|--------|--------|  
|@\_win32|如果在 Win32 系统上运行，则为 true。|  
|@\_win16|如果在 Win16 系统上运行，则为 true。|  
|@\_mac|如果在 Apple Macintosh 系统上运行，则为 true。|  
|@\_alpha|如果在 DEC Alpha 处理器上运行，则为 true。|  
|@\_x86|如果在 Intel 处理器上运行，则为 true。|  
|@\_mc680x0|如果在 Motorola 680x0 处理器上运行，则为 true。|  
|@\_PowerPC|如果在 Motorola PowerPC 处理器上运行，则为 true。|  
|@\_jscript|始终为 true。|  
|@\_jscript\_build|包含 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 脚本引擎的生成号。|  
|@\_jscript\_version|包含 major.minor 格式的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 版本号。|
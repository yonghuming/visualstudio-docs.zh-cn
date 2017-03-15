---
title: "ToggleHUD | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ToggleHUD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

切换上的图形诊断 *HUD* （平视显示系统）覆盖打开或关闭。  
  
## 语法  
  
```cpp  
void ToggleHUD();  
```  
  
## 备注  
 图像诊断 HUD 显示在运行于图像诊断下的 app 的左上角。  它显示有关应用程序运行时的信息及有关图形信息捕捉，并通过调用 [AddMessage](../debugger/addmessage.md) 的成员函数添加消息运行时信息。  
  
 要切换HUD，你不必必须捕捉图像信息，也就是说，它可以通过 `VsgDbg` 类的实例来切换，但 [Init](../debugger/init.md) 成员函数不能先被调用。
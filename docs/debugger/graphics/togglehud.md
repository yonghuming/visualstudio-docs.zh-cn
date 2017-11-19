---
title: "ToggleHUD |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bf1e27b9385257203653f3bff5241f6c3875373
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="togglehud"></a>ToggleHUD
切换图形诊断*HUD* （提醒显示） 覆盖打开或关闭。  
  
## <a name="syntax"></a>语法  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>备注  
 图像诊断 HUD 显示在正在图形诊断下运行的应用的左上角。 它显示有关应用和图形信息捕获，并通过调用添加的消息的运行时信息[AddMessage](addmessage.md)成员函数。  
  
 若要切换 HUD，你不必主动捕获图形信息-即，可通过的实例切换`VsgDbg`类，但[Init](init.md)不必首先调用成员函数。
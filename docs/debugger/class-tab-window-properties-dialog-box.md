---
title: "“窗口属性”对话框 -&gt;“类”选项卡 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "“窗口属性”对话框，“类”选项卡"
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# “窗口属性”对话框 -&gt;“类”选项卡
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

使用“类”选项卡可以显示有关所选窗口的类的信息。  若要显示[“窗口属性”对话框](../debugger/window-properties-dialog-box.md)，请将焦点移动到[窗口视图](../debugger/windows-view.md)窗口。  在树中选择任何窗口节点，然后从“视图”菜单中选择“属性”。  
  
 “类”选项卡上提供了下列设置：  
  
|Entry|说明|  
|-----------|--------|  
|**类名**|窗口类的名称（或序号）。|  
|**类样式**|类样式代码的组合。|  
|**类字节**|与此窗口类关联的特定于应用程序的数据。|  
|**类原子**|**RegisterClass** 调用返回的类的原子。|  
|**实例句柄**|注册了类的模块的实例句柄。  实例句柄不唯一。|  
|**窗口字节**|与此类的每个窗口关联的额外字节数。  这些字节的含义由应用程序决定。  展开该列表框可按 DWORD 格式查看字节值。|  
|**窗口进程**|此类窗口的 **WndProc** 函数的当前地址。  如果已对窗口进行了子类化，则该设置与“常规”选项卡上的“窗口进程”不同。|  
|**菜单名称**|与此类的窗口关联的主菜单的名称（如果没有菜单，则为“无”）。|  
|**图标句柄**|与此类的窗口关联的图标的句柄（如果没有图标，则为“无”）。|  
|**光标句柄**|与此类的窗口关联的光标的句柄（如果没有光标，则为“无”）。|  
|**背景画笔**|与此类的窗口关联的，或与用于绘制窗口背景的某个预定义 COLOR\_\* 颜色关联的背景画笔的句柄（如果没有画笔，则为“无”）。|
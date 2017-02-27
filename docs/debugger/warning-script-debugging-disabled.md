---
title: "警告：脚本调试已禁用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.scriptdisabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 警告：脚本调试已禁用
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

脚本调试当前在 Internet Explorer 中禁用  
  
 尝试在未在 Internet Explorer 中启用脚本调试的情况下调试脚本时，会出现此警告。  出于安全考虑，默认情况下，Internet Explorer 禁用脚本调试。  
  
### 在 Internet Explorer 中启用脚本调试  
  
1.  在 Internet Explorer 的**“工具”**菜单上选择**“Internet 选项”**。  
  
2.  在**“Internet 选项”**对话框中，单击**“高级”**选项卡。  
  
3.  在**“高级”**选项卡上，在**“设置”**框中查找**“浏览”**类别。  
  
4.  清除**“禁用脚本调试\(Internet Explorer\)”**。  
  
5.  单击**“确定”**。  
  
6.  退出并重新启动 Internet Explorer。  
  
     新设置现在将生效。  
  
## 请参阅  
 [如何：附加到脚本](../debugger/how-to-attach-to-script.md)
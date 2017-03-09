---
title: "Configuration name is not valid. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALID_CFG_NAME"
  - "vs.message.0x800A00B7"
ms.assetid: aa439582-0863-41d3-825c-7c45b1773cde
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Configuration name is not valid.
该错误通常发生在为生成配置输入的名称包含非法字符时，例如 \<、\>、&#124; 和 \*。  
  
### 更正此错误  
  
1.  检查配置名称不包含以下字符：\<、\>、\*、&#124;、:、\\、\/、&、%、"、.、\#、? 或者前导或尾随空格。  此外，配置名不能使用为 Windows 或 DOS 保留的名称，例如“nul”、“aux”、“con”、“com\#”、“lpt\#”，等等。  
  
2.  重新键入名称。  
  
## 请参阅  
 [在 Visual Studio 中构建应用程序](../ide/compiling-and-building-in-visual-studio.md)
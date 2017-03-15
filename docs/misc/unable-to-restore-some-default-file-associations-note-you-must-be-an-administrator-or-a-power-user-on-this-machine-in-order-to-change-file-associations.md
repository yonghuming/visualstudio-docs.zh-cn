---
title: "无法还原某些默认文件关联。 注意：你必须是此计算机的管理员或超级用户才能更改文件关联。 | Microsoft Docs"
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
  - "VS.Message.0x00006A85"
  - "VS_E_RESTOREFILEASSOCS"
ms.assetid: 449c5608-83e3-4ddd-91f1-1061916995b3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 无法还原某些默认文件关联。 注意：你必须是此计算机的管理员或超级用户才能更改文件关联。
使用 devenv 命令行开关 \/AssociateFiles 时将发生此错误，但当前用户权限不允许访问注册表的 HKEY\_CLASSES\_ROOT 部分。 当在 [!INCLUDE[wiprlhext](../misc/includes/wiprlhext_md.md)] 上运行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 时，你必须以管理员身份使用 \/AssociateFiles \(devenv.exe\) 开关运行 devenv。  
  
### 更正此错误  
  
-   更改为管理凭据并重试。  
  
## 请参阅  
 [User Rights and Visual Studio](http://msdn.microsoft.com/zh-cn/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Devenv 命令行开关](../ide/reference/devenv-command-line-switches.md)
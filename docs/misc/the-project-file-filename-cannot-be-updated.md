---
title: "The project file &#39;&lt;filename&gt;&#39; cannot be updated | Microsoft Docs"
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
  - "vs.UpgradeErrors"
ms.assetid: ecd1e161-c51c-4aaa-ab80-8fc443bdad81
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project file &#39;&lt;filename&gt;&#39; cannot be updated
您尝试打开在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的早期版本中创建的项目。  必须将项目更新为当前格式，但是它在以下两种情况下无法更新：一是指定的项目文件 \(.vbproj\) 被标记为只读；二是该文件受源代码管理且当前被其他用户锁定。  
  
### 更正此错误  
  
1.  在文件资源管理器中，找到指定的项目文件。  
  
2.  在**“文件”**菜单上选择**“属性”**。  
  
3.  在**“属性”**对话框中取消选中**“只读”**特性。  
  
 如果该文件受源代码管理且被其他用户锁定，请等待直到文件可用后在本地将其签出。  
  
## 请参阅  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)
---
title: "“&lt;qualifiedcontainername&gt;”处项目级导入“&lt;qualifiedelementname&gt;”中存在错误：&lt;errormessage&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC30797"
  - "vbc30797"
helpviewer_keywords: 
  - "BC30797"
ms.assetid: 529f354f-f255-4adc-ab21-bd1796e58d69
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# “&lt;qualifiedcontainername&gt;”处项目级导入“&lt;qualifiedelementname&gt;”中存在错误：&lt;errormessage&gt;
某一语句访问在另一程序集中定义的编程元素，但未对该程序集进行项目引用。  
  
 例如，你的代码可能使用限定字符串 `otherNamespace.otherClass.desiredEnumeration` 访问名为 `desiredEnumeration` 的枚举。 如果编译器在项目引用中找不到 `otherNamespace.otherClass`，它就会生成此错误。  
  
 **错误 ID：**BC30797  
  
### 更正此错误  
  
1.  确保编程元素限定字符串中每个元素拼写正确。  
  
2.  确保你的项目对定义所需编程元素的程序集进行了引用。  
  
3.  参考错误信息并采取相应的操作。  
  
## 请参阅  
 [NOTINBUILD：当多个变量具有相同名称时解析引用](http://msdn.microsoft.com/zh-cn/9601e39f-1911-44e1-ace5-3f6e090408b9)   
 [NIB 如何：修改项目属性和配置设置](http://msdn.microsoft.com/zh-cn/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [NIB 如何：使用“添加引用”对话框添加或删除引用](http://msdn.microsoft.com/zh-cn/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
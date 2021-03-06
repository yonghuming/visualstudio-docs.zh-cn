---
title: "符合 CLS 的 &lt;classname&gt; 中不允许出现不符合 CLS 的“MustOverride”成员。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40034"
  - "vbc40034"
helpviewer_keywords: 
  - "BC40034"
ms.assetid: 4eb36b3a-1bbe-4e99-9ecb-a12b8729b128
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 符合 CLS 的 &lt;classname&gt; 中不允许出现不符合 CLS 的“MustOverride”成员。
类被标记为 `<CLSCompliant(True)>`，但它包含标记为 `<CLSCompliant(False)>` 或未标记的 `MustOverride` 属性或过程。  
  
 如果一个类符合[语言独立性和与语言无关的组件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\)，则使用该类的应用程序将仅访问同样标记为 `<CLSCompliant(True)>` 的成员而忽略无此标记的成员。 但是，应用程序无法忽略 `MustOverride` 属性或过程，因为它必须访问才能重写该属性或过程。  
  
 当将 <xref:System.CLSCompliantAttribute> 应用到编程元素中时，需要将该特性的 `isCompliant` 参数设置为 `True` 或 `False` 来指示符合或不符合性。 此参数没有默认值，必须为其提供一个值。  
  
 如果不将 <xref:System.CLSCompliantAttribute> 应用到元素，则它将被视为不符合规范。  
  
 默认情况下，此消息是一个警告。 有关隐藏警告或将警告视为错误的信息，请参见 [在 Visual Basic 中配置警告](../ide/configuring-warnings-in-visual-basic.md)。  
  
 **错误 ID：**BC40034  
  
### 更正此错误  
  
-   如果你需要 CLS 符合性并且可以控制类源代码，请将该成员标记为 `<CLSCompliant(True)>`。  
  
-   如果你需要 CLS 符合性而不能控制类源代码，或者不将其限制为符合规范，请在其他类中定义此成员。  
  
-   如果你需要此成员保持不符合规范，请从其定义中删除 `MustOverride` 关键字、从类定义中删除 <xref:System.CLSCompliantAttribute> 或将类标记为 `<CLSCompliant(False)>`。  
  
## 请参阅  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [\<PAVE OVER\>编写符合 CLS 的代码](http://msdn.microsoft.com/zh-cn/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
---
title: "An invalid cookie was passed to UnregisterExtenderProvider(). | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_EXT_NOEXTPROVREGISTERED"
ms.assetid: 6180376b-37b4-49e1-aea6-cbc5cf82e232
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# An invalid cookie was passed to UnregisterExtenderProvider().
您指定了不再有效的 Cookie。  
  
### 更正此错误  
  
1.  返回通过调用 RegisterExtenderProvider\(\) 得到的同一个 Cookie 值。  
  
## 请参阅  
 <xref:EnvDTE.ObjectExtenders.RegisterExtenderProvider%2A>   
 <xref:EnvDTE.ObjectExtenders>
---
title: "关于异常的疑难解答：System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException | Microsoft Docs"
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
  - "EHWRTTrackingProfileDeserialization"
helpviewer_keywords: 
  - "System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException 异常"
  - "TrackingProfileDeserializationException 异常"
ms.assetid: ce8fe4c1-43e3-4930-947e-74b8d94f32bf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 关于异常的疑难解答：System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException
如果 XML 文档无法通过 <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException> 反序列化为 <xref:System.Workflow.Runtime.Tracking.TrackingProfile>，将引发 <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> 异常。  
  
## 备注  
 当 <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> 引发此异常时，它会提供一条说明异常原因的消息。 在某些情况下，<xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> 会提供它在尝试反序列化 <xref:System.Workflow.Runtime.Tracking.TrackingProfile> 时遇到的验证错误和警告的列表。 如果提供此列表，<xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException.ValidationEventArgs%2A> 属性将会包含它。  
  
## 请参阅  
 <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)
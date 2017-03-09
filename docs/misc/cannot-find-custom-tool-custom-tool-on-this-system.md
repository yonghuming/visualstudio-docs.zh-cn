---
title: "Cannot find custom tool &#39;custom tool&#39; on this system | Microsoft Docs"
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
  - "vs.tasklisterror.cannot_instantiate_generator1"
ms.assetid: 51fe9bec-b8bc-4a4c-94aa-15a1f7cc8b6b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cannot find custom tool &#39;custom tool&#39; on this system
自定义工具无法由项目系统创建。  请求的自定义工具将不运行，原因是项目系统无法将其实例化。  确保正确安装和注册自定义工具。  
  
 引起此错误的原因可能是为特定文件的 `CustomTool` 属性指定了无效的自定义工具名。  也可能是由于编辑了项目文件 \(.vbproj\/.csproj\)，使得 `CustomTool` 属性值无效。  或者，可能使用了在另一计算机上开发的项目，该计算机上有自定义工具，但是您的计算机上却未安装此自定义工具。  有关 `CustomTool` 属性的更多信息，请参见 [File Properties](http://msdn.microsoft.com/zh-cn/013c4aed-08d6-4dce-a124-ca807ca08959)。  
  
 如果对自定义工具执行 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md) 失败，也会发生此错误。  例如，它可能未注册或缺少必要的 DLL。  
  
## 请参阅  
 [CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)
---
title: "&lt;customErrorReporting&gt; 元素（ClickOnce 部署） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<customErrorReporting> 元素 [ClickOnce 部署清单]"
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;customErrorReporting&gt; 元素（ClickOnce 部署）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定发生错误时所显示的 URI。  
  
## 语法  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## 备注  
 此元素是可选的。  如果此元素不存在，则 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 会显示一个错误对话框，其中显示异常堆栈。  如果 `customErrorReporting` 元素存在，则 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 将改为显示由 `uri` 参数指定的 URI。  目标 URI 将以参数形式包含外部异常类、内部异常类以及内部异常消息。  
  
 使用此元素可以为应用程序添加错误报告功能。  生成的 URI 包含有关错误类型的信息，因此您的网站可以对这些信息进行分析并据此显示内容（例如，显示相应的疑难解答屏幕）。  
  
## 示例  
 下面的代码段演示 `customErrorReporting` 元素以及它可能生成的 URI。  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## 请参阅  
 [ClickOnce 部署清单](../deployment/clickonce-deployment-manifest.md)
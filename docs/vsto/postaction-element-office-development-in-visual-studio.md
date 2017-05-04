---
title: "&lt;postAction&gt; 元素（Visual Studio 中的 Office 开发） | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<postAction> 元素"
  - "<postAction> 元素"
  - "postAction 元素"
ms.assetid: a047e2e2-9732-4140-b8bd-bc5bd1b84291
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# &lt;postAction&gt; 元素（Visual Studio 中的 Office 开发）
  `vstav3`  命名空间的 `postAction` 元素包含与部署后操作（在安装 Office 解决方案后运行）相关联的 `entrypoint` 元素和所有 `postActionData` 元素。  
  
## 语法  
  
```  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## 元素和属性  
 `postAction` 元素是可选的，它位于 `vstav3`  命名空间中。 每个部署后操作的应用程序清单中只定义了一个 `postAction` 元素。  
  
 `postAction` 元素没有属性。  
  
 `postAction` 具有下列元素。  
  
### entryPoint  
 可选。`vstav3`  命名空间中 `entryPoint` 元素的角色在 [&#60;entryPoints&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/entrypoints-element-office-development-in-visual-studio.md) 中定义。  
  
### postActionData  
 可选。`vstav3`  命名空间中 `postActionData` 元素的角色在 [&#60;postActionData&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/postactiondata-element-office-development-in-visual-studio.md) 中定义。  
  
## 部署后操作示例  
  
### 描述  
 下面的代码示例演示 Office 解决方案的应用程序清单中的 `postAction` 元素，该解决方案是使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction>  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  
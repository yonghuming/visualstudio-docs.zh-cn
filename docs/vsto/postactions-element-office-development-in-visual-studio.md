---
title: "&lt;postActions&gt; 元素（Visual Studio 中的 Office 开发）"
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
  - "应用程序清单 [Visual Studio 中的 Office 开发]，<postActions> 元素"
  - "postActions 元素"
  - "<postActions> 元素"
ms.assetid: 6e487549-fdd6-49bd-be7a-b91f1f964594
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# &lt;postActions&gt; 元素（Visual Studio 中的 Office 开发）
  `vstav3` 命名空间的 `postActions` 元素包含描述部署后操作（在安装 Office 解决方案后运行）的 `postAction` 所有元素。  
  
## 语法  
  
```  
<postActions>  
  <postAction>  
    <entryPoint>  
    </entryPoint>  
    <postActionData>  
    </postActionData>  
  </postAction>  
</postActions>  
```  
  
## 元素和属性  
 `postActions` 元素是可选的，它位于 `vstav3`  命名空间中。 在应用程序清单中定义的 `postActions` 元素只有一个。  
  
 `postActions` 元素没有属性。  
  
 `postActions` 具有以下元素。  
  
### postAction  
 可选。`vstav3`  命名空间中 `postAction` 元素的角色在 [&#60;postAction&#62; 元素（Visual Studio 中的 Office 开发）](../vsto/postaction-element-office-development-in-visual-studio.md) 中定义。  
  
## 部署后操作示例  
  
### 描述  
 下面的代码示例演示 Office 解决方案的应用程序清单中的 `postActions` 元素，该解决方案是使用 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 部署的。 此代码示例摘自 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md) 中提供的一个更大的示例。  
  
### 代码  
  
```  
<vstav3:postActions> <vstav3:postAction> <vstav3:entryPoint class="PostDeploymentAction.PostDeploymentActionSample"> <assemblyIdentity name="PostDeploymentAction" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:postActionData> </vstav3:postActionData> </vstav3:postAction> </vstav3:postActions>  
```  
  
## 请参阅  
 [Office 解决方案的应用程序清单](../vsto/application-manifests-for-office-solutions.md)   
 [Office 解决方案的部署清单](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 应用程序清单](../deployment/clickonce-application-manifest.md)  
  
  
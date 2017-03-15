---
title: "&lt;Schedules&gt; 元素（引导程序） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Schedules> 元素 [引导程序]"
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# &lt;Schedules&gt; 元素（引导程序）
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Schedules` 元素包含 `Schedule` 元素，后者定义 `Command` 元素定义的命令的特定运行时间。  
  
## 语法  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## 元素和特性  
 `Schedules` 元素是 `Product` 元素的子元素。  每个 `Product` 元素最多可能有一个 `Schedules` 元素。  `Schedules` 元素没有任何特性。  
  
## Schedule  
 `Schedule` 元素是 `Schedules` 元素的子元素。  `Schedules` 元素必须至少有一个 `Schedule` 元素。  
  
 `Schedule` 具有下列特性。  
  
|特性|说明|  
|--------|--------|  
|`Name`|必选。  安排项的名称。  此名称与 `Command` 元素的 `ScheduleName` 属性对应。  当 `Command` 引用指定的安排时，只能在该 `Schedule` 元素所指示的时间执行。  安排还可能与 `FailIf` 和 `BypassIf` 元素关联，这些元素对这些条件测试进行限制，使其按照指定的安排执行。  有关更多信息，请参见 [\<Commands\> 元素](../deployment/commands-element-bootstrapper.md)。|  
  
 给定的 `Schedule` 元素可能恰好具有下列子元素之一。  
  
## BuildList  
 `BuildList` 元素指示安装程序在引导应用程序启动之后立即执行命令。  
  
## BeforePackage  
 `BeforePackage` 元素指示安装程序在安装指定的包之前执行命令。  
  
## AfterPackage  
 `AfterPackage` 元素指示安装程序在安装指定的包之后执行命令。  
  
## 请参阅  
 [\<Product\> 元素](../deployment/product-element-bootstrapper.md)   
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)
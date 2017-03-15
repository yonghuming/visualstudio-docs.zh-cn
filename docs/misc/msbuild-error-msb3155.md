---
title: "MSBuild 错误 MSB3155 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.ProductNotFound"
helpviewer_keywords: 
  - "MSB3155"
ms.assetid: 59bf2293-ef13-4bb1-8f29-5d6966bbe313
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3155
**MSBuild 错误 MSB3155: 未能在“\<路径\>”中找到项“\<包\>”。**  
  
 当无法在引导程序缓存中找到具有指定 <xref:Microsoft.Build.Tasks.Deployment.Bootstrapper.Product.ProductCode%2A> 的包时，就会出现此警告。  
  
> [!NOTE]
>  Microsoft 数据访问组件 \(MDAC\) 已不再以引导程序包的形式包含在缓存中。  可以从 [Microsoft Windows Update](http://go.microsoft.com/fwlink/?LinkId=86676) 网站下载这些组件。  
  
### 更正此错误  
  
-   从要安装的程序包列表中移除该程序包，或者将其添加到缓存。  还要确保使用有效的 XML 标记正确地设置清单的格式。  
  
## 请参阅  
 [产品和包架构引用](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\> 元素](../deployment/packagefiles-element-bootstrapper.md)   
 [“系统必备”对话框](../ide/reference/prerequisites-dialog-box.md)   
 [创建引导程序包](../deployment/creating-bootstrapper-packages.md)
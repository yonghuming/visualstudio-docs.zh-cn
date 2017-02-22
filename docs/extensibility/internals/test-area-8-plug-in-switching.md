---
title: "测试区域 8: 插件切换 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "源代码管理 [Visual Studio SDK]，切换插件"
  - "源代码管理插件切换"
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 测试区域 8: 插件切换
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 集成开发 \(IDE\)环境具有更改 \(UI\)的用户界面当前源代码管理插件。  此测试环节。使用的插件为解决方案源代码管理中选择的进程的测试用例。  
  
## 访问菜单命令  
 下面 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 集成开发环境 \(ide\) 菜单路径用于测试用例。  
  
-   当前源代码管理插件: **工具** \- AMP\_GT **选项** \- AMP\_GT **源代码管理** \- AMP\_GT **插件选择**。  
  
-   更改源代码管理绑定: **文件** \- AMP\_GT **源代码管理** \- AMP\_GT **更改源代码管理**…  
  
## 常见的预期行为。  
 更改解决方案的源代码管理插件是可能的，而不退出 Visual Studio 或加载解决方案。  此外，在中，当该解决方案加载时，当前源代码管理插件自动更改为解决方案中使用的对象。  
  
## 测试用例  
 下面是插件切换的特定测试用例测试环节。  
  
### 用例 8a:自动更改  
  
#### 预期的行为  
 当用户加载在源代码管理的解决方案时，解决方案会自动加载，并相应的源代码管理插件中选择作为当前。  
  
|操作|测试步骤|验证的预期结果|  
|--------|----------|-------------|  
|自动源代码管理插件更改|1.  选择插件下测试作为当前 \(**工具** \- AMP\_GT **选项** \- AMP\_GT **源代码管理** \- AMP\_GT **插件选择**。\)<br />2.  创建新项目。<br />3.  将解决方案添加到源代码管理。<br />4.  选择另一个插件 \(例如， [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\)。<br />5.  卸载解决方案提示的 Accept。<br />6.  重新打开解决方案从磁盘。|打开解决方案。<br /><br /> 插件测试是当前源代码管理插件。|  
  
### 用例 8b:基于解决方案的更改  
  
#### 预期的行为  
 解决方案可以有其 changed 关联的源代码管理插件。  
  
|操作|测试步骤|验证的预期结果|  
|--------|----------|-------------|  
|插件的更改解决方案的|1.  选择插件下测试作为当前 \(**工具** \- AMP\_GT **选项** \- AMP\_GT **源代码管理** \- AMP\_GT **插件选择**\)。<br />2.  创建新项目和解决方案。<br />3.  将解决方案添加到源代码管理。<br />4.  断开从源代码管理的解决方案 \(使用 **更改源代码管理** 对话框\)。<br />5.  选择另一个插件 \(例如， [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\)。<br />6.  重新加载解决方案从磁盘，如果卸载。<br />7.  将解决方案添加到源代码管理。<br />8.  断开从源代码管理的解决方案 \(使用 **更改源代码管理** 对话框\)。<br />9. 选择插件下重新测试。<br />10. 重新加载解决方案从磁盘，如果卸载。<br />11. 将解决方案添加到原始位置 \(使用 **更改源代码管理** 对话框\)。|使用选定的插件，解决方案添加到源控件。|  
  
## 请参阅  
 [源代码管理插件的测试指南](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
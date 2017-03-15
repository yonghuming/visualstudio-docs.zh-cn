---
title: "如何︰ 更新 Visual Studio 扩展 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "更新包"
  - "更新扩展"
  - "新的包版本"
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何︰ 更新 Visual Studio 扩展
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以通过使用 Visual Studio 扩展中更新您的系统上 **扩展和更新** 若要安装的更新的版本。 如果您创建的扩展的更新的版本，您可以将其表示为更新的 VSIX 清单中的版本号递增。  
  
 安装更新时传入的扩展的 VSIX 清单具有相同 `ID` 作为安装的一个及更高版本 `Version` 数。 如果 `Version` 相同或更低时，不能安装的包。 如果 `ID` 值不匹配，尚未安装的包识别为单独的扩展。  
  
 为了帮助防止冲突，在开发过程中，我们建议卸载较早版本的扩展的进度，并同时卸载或禁用可能会有冲突的任何其他扩展。  
  
### 若要更新您的系统上的某个扩展  
  
1.  在“工具”菜单上，单击“扩展和更新”。  
  
2.  在左窗格中，单击 **更新**。  
  
3.  在中间窗格中，单击你想要安装的更新。  
  
     更新后的扩展的版本号显示在右窗格中，以及其他信息。  
  
4.  在右窗格的底部，单击 **更新**。  
  
### 若要发布扩展的更新  
  
1.  在 Visual Studio 中，打开你想要更新的扩展插件的解决方案。 进行更改。  
  
    > [!IMPORTANT]
    >  无符号的所有用户分机根本不会自动都更新。 你应始终登录您的扩展。  
  
2.  在 **解决方案资源管理器**, ，打开 source.extension.manifest。  
  
3.  在清单设计器中的数字将值增加 **版本** 字段。  
  
4.  保存解决方案并生成它。  
  
5.  （位于项目的 \\bin\\Debug\\ 文件夹） 的新.vsix 文件上载到 [Visual Studio 库](http://go.microsoft.com/fwlink/?LinkID=123847) Web 站点。  
  
     当扩展了早期版本的用户打开 **扩展和更新**, ，新版本将出现在 **更新** 列表中，前提是该工具设置为自动查找更新。  
  
     可以启用或禁用自动检查更新的底部 **更新** 窗格 \(**启用\/禁用自动检测可用的更新**\)，哪些更改 **检查是否有更新** 中设置 **工具 \/ 选项 \/ 环境 \/ 扩展和更新**。  
  
    > [!NOTE]
    >  从 Visual Studio 2015 Update 2 开始，您可以指定 \(在 **工具 \/ 选项 \/ 环境 \/ 扩展和更新**\) 您是否需要为每用户扩展、 所有用户扩展或这两个 （默认设置） 自动更新。  
  
## 请参阅  
 [VSIX 包的剖析](../extensibility/anatomy-of-a-vsix-package.md)   
 [查找和使用 Visual Studio 扩展](../ide/finding-and-using-visual-studio-extensions.md)
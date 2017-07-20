---
title: "管理应用程序资源 (.NET) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: 5cb2e044f5c55881adade6d3022fc453360a2e9c
ms.contentlocale: zh-cn
ms.lasthandoff: 05/30/2017

---
# 管理应用程序资源 (.NET)
<a id="managing-application-resources-net" class="xliff"></a>
资源文件是应用程序使用的不可编译的文件，例如图标文件或音频文件。 由于这些文件不是编译过程的一部分，因此你可以更改它们而无需重新编译二进制文件。 如果打算本地化你的应用程序，则应为本地化应用程序时需要进行更改的所有字符串和其他资源使用资源文件。  
  
 有关 .NET 桌面应用中的资源的详细信息，请参阅 [Resources in Desktop Apps](/dotnet/framework/resources/index)（桌面应用中的资源）。 有关 C++ 桌面应用中的资源的详细信息，请参阅 [Working with Resource Files](/cpp/windows/working-with-resource-files)。  
  
 Windows 应用商店应用使用桌面应用中的不同资源模型。 有关 Windows 应用商店应用中的资源的信息，请参阅 Windows 开发人员中心网站上的 [定义应用程序资源](https://msdn.microsoft.com/en-us/library/windows/apps/hh465228.aspx) 。  
  
## 使用资源
<a id="working-with-resources" class="xliff"></a>  
 在托管代码项目中，打开项目属性窗口（在“解决方案资源管理器”  中，右键单击项目节点并选择“属性” ，或在“快速启动”  窗口中键入 **project properties** ，或在“解决方案资源管理器”  窗口中键入 ALT + ENTER）。 选择“资源”  选项卡。 如果你的项目尚未包含 .resx 文件，你可以添加一个，添加和删除不同类型的资源，并修改现有资源。  
  
 若要了解如何使用 C++ 项目中的资源，请参阅 [How to: Create a Resource](/cpp/windows/how-to-create-a-resource)（如何：创建资源）。

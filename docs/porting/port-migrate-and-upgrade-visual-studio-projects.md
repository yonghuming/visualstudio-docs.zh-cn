---
title: "移植、迁移和升级 Visual Studio 项目 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: TerryGLee
ms.author: tglee
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
translationtype: Human Translation
ms.sourcegitcommit: ae6564f10ca561853444698665779bd1014d4afd
ms.openlocfilehash: 2915a9ceec638471ac29599992a7ccdff17cefb4

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>移植、迁移和升级 Visual Studio 项目
移动到较新版本的 Visual Studio 时，需要知道是否必须修改在早期版本中创建的任何解决方案、项目、文件以及其他资产，*之后*才能在最新版本中开始运行。

 许多使用广泛的资源在最新版本 Visual Studio 2017 RC 中的行为与其在最近的 Visual Studio 2015 中的行为相同。 它们在早期版本 Visual Studio 2013 和 Visual Studio 2012 中的行为也相同。

 例如，可在 Visual Studio 2017 RC 中打开在 Visual Studio 2015 或 Visual Studio 2013 中创建的项目，对其进行更改，然后在 Visual Studio 2017 RC 中重新打开；更改将保持不变，并且项目的行为方式与早期版本中的一样。 上述情况同样适用于在 Visual Studio 2012 中创建的许多资产。  

 如果将 Visual Studio 2015 与 Visual Studio 2013、Visual Studio 2012 或 Visual Studio 2010 SP1 一起使用，则可在任意一个版本中创建和修改项目和文件。 可以在各个版本之间传输项目和文件，前提是不添加其中某个版本不支持的功能。 （若要深入了解哪些功能特定于哪些版本，请参阅[发布说明](https://www.visualstudio.com/vs/release-notes/)。）



<!--HONumber=Feb17_HO4-->



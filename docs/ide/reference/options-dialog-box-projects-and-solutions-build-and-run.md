---
title: "“选项”对话框、项目和解决方案、生成和运行 | Microsoft Docs"
ms.custom: 
ms.date: 7/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: dc7a0c10390de67b56a83d2824224bed24125db0
ms.openlocfilehash: 974a032e57397592b7c09bffe28c55cb02c01a0a
ms.contentlocale: zh-cn
ms.lasthandoff: 07/17/2017

---

# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>选项对话框，项目和解决方案，生成和运行

在此对话框中，可以指定可同时生成的 Visual C++ 或 Visual C# 项目的最大数量、某些默认生成行为及一些生成日志设置。 要访问这些选项，请选择“工具 > 选项”，展开“项目和解决方案”，然后选择“生成和运行”。
  
**最大并行项目生成数**  
指定可以同时生成的 Visual C++ 和 Visual C# 项目的最大数量。 若要优化生成过程，最大并行项目生成数自动设置为你的计算机的 CPU 数量。 最大数量为 32。  

**在运行时仅生成启动项目和依赖项**  
当使用 F5 键，选择“调试 > 启动”菜单命令或“生成”菜单上的适用命令时，仅生成启动项目及其依赖项。 如果清楚明确的话，则会生成所有项目和依赖项。 

**运行期间，当项目过期时**  
*仅适用于 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 项目。*

当使用 F5 或“调试 > 启动”命令运行项目时，默认设置“提示生成”会显示一条消息（如果项目配置已过期）。 选择“始终生成”以在每次运行时均生成项目。 选择“从不生成”以禁止运行项目时的所有自动生成。

**运行期间，当出现生成或部署错误时**  
*仅适用于 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 项目。*

当使用 F5 或“调试 > 启动”命令运行项目时，默认设置“提示启动”会显示一条消息（如果项目应运行，即使生成失败）。 选择“启动旧版本”以自动启动上一个良好生成，这可能会导致正在运行的代码和源代码之间不匹配。 选择“不启动”以禁止显示消息。

**对于新解决方案，使用当前选定的项目作为启动项目**  
设置此选项时，新解决方案会使用当前选定的项目作为启动项目。  

**MSBuild 项目生成输出详细信息**  
确定出现在生成的“输出”窗口中的信息数。  

**MSBuild 项目生成日志文件详细信息**  
*仅适用于 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 项目。*

确定写入到生成日志文件中的信息数，该文件位于 \\...\\ProjectName\Debug\\ProjectName.log。  

## <a name="see-also"></a>另请参阅  
-[编译和生成](../../ide/compiling-and-building-in-visual-studio.md)
- [“选项”对话框、项目和解决方案](../../ide/projects-and-solutions-options-dialog-box.md)
- [“选项”对话框、项目和解决方案、Web 项目](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)

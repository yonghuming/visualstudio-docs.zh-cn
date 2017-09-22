---
title: "“选项”对话框 ->“项目和解决方案”->“VC++ 项目设置”| Microsoft Docs"
ms.custom: 
ms.date: 08/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
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
ms.translationtype: HT
ms.sourcegitcommit: 8a544bd1e1242bb6fabe00f7842ac33ed9d9d444
ms.openlocfilehash: 6980c103c58df6ef88837c8701be2e04ccb0eee2
ms.contentlocale: zh-cn
ms.lasthandoff: 08/14/2017

---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>“选项”对话框 ->“项目和解决方案”->“VC++ 项目设置”
使用此对话框，可以定义与记录、性能和支持文件类型相关的 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 生成和项目设置。  
  
### <a name="to-access-this-dialog-box"></a>访问此对话框  
  
1.  在 **“工具”** 菜单上，单击 **“选项”**。  
  
2.  依次选择“项目和解决方案”和“VC++ 项目设置”。  
  
 
## <a name="build-logging"></a>生成日志  
 **是**  
  启用生成相应的生成日志文件。 此选项可生成位于项目的中间文件目录中的 BuildLog.htm。 每个新的生成文件都会覆盖上一 BuildLog.htm 文件。  
  
 **否**  
  禁用生成相应的生成日志文件。  

## <a name="show-environment-in-log"></a>在日志中显示环境  
 **是**  
 在生成日志文件中列出环境变量。 此选项指定在 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 项目生成期间，将所有环境变量回显到生成日志文件中。  
  
 **否**  
 不在生成日志文件中显示环境变量。  

## <a name="build-timing"></a>生成计时  
 **是**  
  启用生成计时。 如果选中，输出窗口中会发布生成完成所需的时间。 有关详细信息，请参阅[输出窗口](../../ide/reference/output-window.md)。  
  
 **否**  
 禁用生成计时。  
   
## <a name="maximum-concurrent-c-compilations"></a>最大并发 C++ 编译数  
  指定用于并行 C++ 编译的 CPU 内核数目上限。  
  
## <a name="extensions-to-include"></a>要包括的扩展名  
  指定可导入项目的文件的文件扩展名。  

## <a name="extensions-to-hide"></a>要隐藏的扩展名  
  指定在“显示所有文件”启用时，不会在“解决方案资源管理器”中显示的文件的文件扩展名。  

 ## <a name="build-customization-search-path"></a>生成自定义搜索路径  
  指定包含 .rules 文件的目录列表，这些文件有助于定义项目的生成规则。  

# <a name="solution-explorer-mode"></a>解决方案资源管理器模式  
 **仅显示项目中的文件**  
  将“解决方案资源管理器”配置为仅显示项目中的文件。  
  
 **显示所有文件**  
  将“解决方案资源管理器”配置为显示项目中的文件和磁盘上项目文件夹中的文件。  


## <a name="enable-project-caching"></a>启用项目缓存
“是”选项使 Visual Studio 能缓存项目数据，以便下次打开该项目时，它能直接加载缓存的数据，而无需通过项目文件重新对其计算。 使用缓存数据可显著缩短项目加载时间。   

“否”选项表示请勿使用缓存的项目数据。 每次加载项目时分析项目文件。


  

  
#
## <a name="see-also"></a>另请参阅  
 [生成 C/C++ 程序](/cpp/build/building-c-cpp-programs)   
 [C/C++ 生成参考](/cpp/build/reference/c-cpp-building-reference)

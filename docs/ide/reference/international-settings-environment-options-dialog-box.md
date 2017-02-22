---
title: "“选项”对话框 -&gt;“环境”-&gt;“区域设置” | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.InternationalSettings"
  - "VS.ToolsOptionsPages.Environment.International_Settings"
  - "VS.Environment.International Settings"
  - "VS.ToolsOptionsPag.Environment.International_Settings"
helpviewer_keywords: 
  - "“区域设置”对话框"
  - "语言，环境设置"
  - "“选项”对话框，区域设置"
  - "语言，指定默认值"
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# “选项”对话框 -&gt;“环境”-&gt;“区域设置”
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

当你的计算机上安装有多个语言版本的集成开发环境 \(IDE\) 时，可通过国际设置页面更改默认语言。  可通过从**“工具”**菜单选择**“选项”**，然后从**“环境”**文件夹选择**“国际设置”**，访问此对话框。  如果此页未出现在列表中，请在**“选项”**对话框中选择**“显示所有设置”**。  
  
> [!NOTE]
>  对话框中的可用选项以及显示的菜单命令的名称和位置可能与“帮助”中的描述不同，具体取决于您的当前设置或版本。  若要更改设置，请在**“工具”**菜单上选择**“导入和导出设置”**。  有关详细信息，请参阅 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-cn/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
 **语言**  
 列出已安装产品语言版本的可用语言。  除非你的计算机上安装了多个语言版本，否则此选项不可用。  如果产品的多个语言或产品的混合语言安装可共享环境，则将语言选项更改为**和 Microsoft Windows 一样**。  
  
> [!CAUTION]
>  在安装了多个语言的系统中，Visual C\+\+ 生成工具（cl.exe、link.exe、nmake.exe、bscmake.exe 和相关文件）不受此设置的影响。  这些工具使用上次安装的语言版本，以前安装的语言版本的工具将被覆盖，因为 Visual C\+\+ 生成工具不使用附属 DLL 模型。  
  
## 请参阅  
 [安装 Visual Studio 的多个语言版本](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [“选项”对话框 \-\>“环境”](../../ide/reference/environment-options-dialog-box.md)
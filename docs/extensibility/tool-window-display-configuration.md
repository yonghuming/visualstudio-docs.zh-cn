---
title: "工具窗口中显示配置 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 9478ffb6ffc1fcd2204065ff4fb7cb113ab88ba4
ms.lasthandoff: 02/22/2017

---
# <a name="tool-window-display-configuration"></a>工具窗口中显示配置
可选的值中指定了 VSPackage 时注册一个工具窗口、 的默认位置、 大小、 停靠样式和可见性的其他信息。 工具窗口注册的详细信息，请参阅[注册表中的工具窗口](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>窗口显示信息  
 工具窗口的基本显示配置存储在最多六个可选的值︰  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|名称|类型|数据|说明|  
|----------|----------|----------|-----------------|  
|名称|REG_SZ|"此处显示短名称"|描述工具窗口中的短名称。 仅用于在注册表中的引用。|  
|Float|REG_SZ|"X1，Y1，X2，Y2"|四个以逗号分隔的值。 X1，Y1 是工具窗口的左上角的坐标。 X2，Y2 是右下角的坐标。 所有值都都以屏幕坐标表示。|  
|样式|REG_SZ|"MDI"<br /><br /> "浮动"<br /><br /> "链接"<br /><br /> "选项卡式"<br /><br /> "AlwaysFloat"|关键字指定初始显示工具窗口的状态。<br /><br /> "MDI"= 与 MDI 窗口停靠在一起。<br /><br /> "浮动"= 浮动。<br /><br /> "链接"= 链接在一起 （窗口中的项中指定） 的另一个窗口。<br /><br /> "选项卡式"= 与另一个工具窗口结合使用。<br /><br /> "AlwaysFloat"= 不固定。<br /><br /> 有关详细信息，请参阅下面的注释部分。|  
|窗口|REG_SZ|*\<GUID&1;&GT;*|窗口的可链接或选项卡式工具窗口中的 GUID。 GUID 可以属于您自己的窗口中的一个或一种在 windows [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE。|  
|方向|REG_SZ|"左"<br /><br /> "右"<br /><br /> "Top"<br /><br /> "底部"|请参阅下面的注释部分。|  
|DontForceCreate|REG_DWORD|0 或 1|此条目存在后，其值不为零，窗口中加载，但不是会立即显示。|  
  
### <a name="comments"></a>注释  
 方向条目定义其中工具窗口停靠在双击其标题栏时的位置。 位置是相对于窗口在窗口中的项中指定的。 如果样式条目设置为"链接"，则方向项可以是"Left"、"右"、"Top"或"底部"。 如果样式条目为"选项卡式"、 方向条目可以"保留"Right"，并指定选项卡的添加位置。 如果样式该项，则"浮动"，工具窗口中浮动第一次。 双击标题栏时，方向和窗口条目适用，并且窗口中使用"选项卡式"样式。 如果"AlwaysFloat"样式条目，则不停靠工具窗口。 如果"MDI"样式条目，则工具窗口链接到 MDI 区域中，并且将忽略窗口中的项。  
  
### <a name="example"></a>示例  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>工具窗口可见性  
 可选的可见性子项中的值确定工具窗口的可见性设置。 值的名称用于存储命令需要窗口的可见性的 Guid。 如果执行命令时，IDE 将保证工具窗口中创建并可见。  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|名称|类型|数据|说明|  
|----------|----------|----------|-----------------|  
|(默认)|REG_SZ|无|将保留为空。|  
|*\<GUID&1;&GT;*|REG_DWORD 或 REG_SZ|0 或的描述性字符串。|可选。 注册表项的名称必须是命令需要可见性的 GUID。 只包含一个信息性的字符串值。 通常情况下，值是`reg_dword`设置为 0。|  
  
### <a name="example"></a>示例  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>另请参阅  
 [VSPackage 要点](../misc/vspackage-essentials.md)

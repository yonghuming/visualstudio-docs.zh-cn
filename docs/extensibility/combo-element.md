---
title: "组合元素 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "组合元素 （VSCT XML 架构）"
  - "VSCT XML 架构元素、 组合"
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 组合元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定义在组合框中显示的命令。 有四种类型的组合框，如下所示︰ 下拉组合、 DynamicCombo、 IndexCombo 和 MRUCombo。  
  
## <a name="syntax"></a>语法  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|guid|必需。 GUID/ID 命令标识符的 GUID。|  
|id|必需。 ID 的 GUID/ID 命令标识符。|  
|defaultWidth|必需。 一个整数，指定组合框像素宽度。|  
|idCommandList|必需。 发送到活动的命令目标要检索的项将在组合框中显示的列表 ID。 ID 将为与控件相同的 GUID 作用域中。|  
|priority|可选。 一个数字值，指定的优先级。|  
|类型|可选。 一个枚举的值，指定按钮的类型。<br /><br /> 如果未授予，将使用按钮。<br /><br /> 下拉组合<br /> VSPackage 负责填写此组合框的内容。 用户能在此下拉列表的文本框中键入任何内容。<br /><br /> DynamicCombo<br /> VSPackage 负责填写此组合框的内容。 用户可以编辑此组合，并还在其中选择项。<br /><br /> IndexCombo<br /> 但它 DynamicCombo 相同引发项而不是其文本的索引。<br /><br /> MRUCombo<br /> 填充由集成的开发环境 (IDE) 代表 VSPackage。  用户可以编辑此组合框中。 IDE 会记住最多每个组合中各上次 16 个条目。<br /><br /> 当用户在组合框中，选择某个控件，或进入新的内容时，IDE 将通知合适的 VSPackage。|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|父级|可选。 父元素的按钮。|  
|CommandFlag|必需。 请参阅 [命令标志元素](../extensibility/command-flag-element.md)。 按钮 CommandFlag 有效值如下所示。<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> 的筛选键<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|字符串|必需。 请参阅 [字符串元素](../extensibility/strings-element.md)。 必须定义子 ButtonText 元素。|  
|批注|可选注释。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[命令元素](../extensibility/commands-element.md)|表示 VSPackage 工具栏上的命令的集合。|  
  
## <a name="example"></a>示例  
  
```  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>请参阅  
 [Visual Studio 命令表 (。Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
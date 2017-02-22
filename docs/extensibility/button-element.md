---
title: "Button 元素 | Microsoft Docs"
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
  - "按钮元素 （VSCT XML 架构）"
  - "VSCT XML 架构元素、 按钮"
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Button 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定义用户可以与交互元素。 按钮可以是不同类型的︰ 按钮、 MenuButton 和 SplitDropDown。  
  
## <a name="syntax"></a>语法  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|guid|必需。 GUID/ID 命令标识符的 GUID。|  
|id|必需。 ID 的 GUID/ID 命令标识符。|  
|priority|可选。 一个数字值，指定的优先级。|  
|类型|可选。 一个枚举的值，用于指定按钮的种类。<br /><br /> 如果未授予，将使用按钮。<br /><br /> Button<br /> 标准命令显示在工具栏上 （通常作为图标按钮），菜单和上下文菜单。<br /><br /> MenuButton<br /> 不执行命令，但生成另一个菜单的菜单项。<br /><br /> SplitDropDown<br /> 控件，如 Microsoft Word 中的标准工具栏上的撤消和重做按钮。|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[父元素](../extensibility/parent-element.md)|可选。 父元素的按钮。|  
|[Icon 元素](../extensibility/icon-element.md)|可选。 与按钮相关联的图标。|  
|[命令标志元素](../extensibility/command-flag-element.md)|必需。 按钮 CommandFlag 有效值如下所示。<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -图像<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|  
|[字符串元素](../extensibility/strings-element.md)|必需。 子 [ButtonText 元素](../extensibility/buttontext-element.md) 必须定义。|  
|批注|可选注释。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[按钮元素](../extensibility/buttons-element.md)|按钮元素进行分组。|  
  
## <a name="example"></a>示例  
 下面的示例在.vsct 文件中定义一个按钮。  
  
 [!CODE [MenuText#02](../CodeSnippet/VS_Snippets_VSSDK/menutext#02)]  
  
## <a name="see-also"></a>请参阅  
 [Visual Studio 命令表 (。Vsct) 文件](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
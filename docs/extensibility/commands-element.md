---
title: "Commands 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Commands"
helpviewer_keywords: 
  - "Commands 元素 (VSCT XML 架构)"
  - "VSCT XML 架构元素命令"
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Commands 元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

表示 VSPackage 工具栏上的命令的集合。 该集合中可以具有最多五个小节，如下所示: 菜单、 组、 按钮、 组合和位图。  
  
 每个小节子元素，例如，\< 菜单 \> 由 GUID 和数字标识符对唯一的命令 ID 标识。 GUID 标识"命令将设置"，并且用于进行分组在逻辑上相关的命令。 VSPackage 应定义其自己的命令集以避免与由其他 Vspackage 定义的命令 Id 发生冲突。  
  
## 语法  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|包|标识将提供的命令的 VSPackage 的 GUID。<br /><br /> 例如，打包 \="guidVsPackage1Pkg"。|  
  
### 子元素  
  
|元素|描述|  
|--------|--------|  
|[菜单元素](../extensibility/menus-element.md)|定义 VSPackage 实现的所有菜单。|  
|[Groups 元素](../extensibility/groups-element.md)|包含在 VSPackage 中定义的命令组的条目。|  
|[按钮元素](../extensibility/buttons-element.md)|按钮元素进行分组。|  
|[位图元素](../extensibility/bitmaps-element.md)|位图元素进行分组。|  
|[组合元素](../extensibility/combos-element.md)|组合元素进行分组。|  
  
### 父元素  
  
|元素|描述|  
|--------|--------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定义表示 VSPackage 提供到 IDE 的命令的所有元素。 可能的元素是菜单项、 菜单、 工具栏和组合框。|  
  
## 示例  
 下面的示例演示如何使用 [Commands Element](../extensibility/commands-element.md)。  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## 请参阅  
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)
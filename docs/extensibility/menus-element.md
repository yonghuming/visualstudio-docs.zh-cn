---
title: "菜单元素 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML 架构元素菜单"
  - "菜单元素 (VSCT XML 架构)"
ms.assetid: d825a99b-e05c-4dd9-8933-a180216d667a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 菜单元素
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定义所有菜单和工具栏 VSPackage 实现。  
  
## 语法  
  
```  
<Menus>  
  <Menu>... </Menu>  
  <Menu>... </Menu>  
</Menus>  
```  
  
## 特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### 特性  
  
|特性|描述|  
|--------|--------|  
|条件|可选。 请参阅 [条件属性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子元素  
  
|元素|说明|  
|--------|--------|  
|[Menus Element](../extensibility/menus-element.md)|定义所有菜单和工具栏 VSPackage 实现。|  
|[Menu 元素](../extensibility/menu-element.md)|表示单个菜单或工具栏。|  
  
### 父元素  
  
|元素|说明|  
|--------|--------|  
|[Commands 元素](../extensibility/commands-element.md)|表示在 VSPackage 中命令的集合。|  
  
## 示例  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## 请参阅  
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、 菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)
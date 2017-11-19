---
title: "命令元素 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61d7f67eda9bdd1d215586a75ed01c1089ccf7fc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="commands-element"></a>命令元素
表示 VSPackage 工具栏上的命令的集合。 集合可以有最多五个小节中，如下： 菜单、 组、 按钮、 组合和位图。  
  
 每个小节子元素，例如，\<菜单 >，由 GUID，数字标识符对是唯一的命令 ID 标识。 GUID 标识的"命令集"，并用于逻辑上相关的命令进行分组。 VSPackage 应定义其自己的命令集以避免与由其他 Vspackage 定义的命令 Id 的冲突。  
  
## <a name="syntax"></a>语法  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|包|一个 GUID，标识提供了命令的 VSPackage。<br /><br /> 例如，打包 ="guidVsPackage1Pkg"。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[Menus 元素](../extensibility/menus-element.md)|定义 VSPackage 实现的所有菜单。|  
|[Groups 元素](../extensibility/groups-element.md)|包含在 VSPackage 中定义的命令组的条目。|  
|[Buttons 元素](../extensibility/buttons-element.md)|按钮元素进行分组。|  
|[Bitmaps 元素](../extensibility/bitmaps-element.md)|位图元素进行分组。|  
|[Combos 元素](../extensibility/combos-element.md)|组合元素进行分组。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[CommandTable 元素](../extensibility/commandtable-element.md)|定义表示 VSPackage 提供给 IDE 的命令的所有元素。 可能的元素是菜单项、 菜单、 工具栏和组合框。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用[命令元素](../extensibility/commands-element.md)。  
  
```  
<Commands package="guidMyPackage">  
    <Menus>  
      <Menu Condition="'%(DEBUG)' != 'true'"   
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"   
        priority="0x0000" type="Menu">  
        <Annotation>  
          <Documentation>this is an annotation</Documentation>  
          <AppInfo>  
            <CustomData>  
              <CustomSubElement>Some data</CustomSubElement>  
            </CustomData>  
          </AppInfo>  
        </Annotation>  
        <CommandFlag>AlwaysCreate</CommandFlag>  
        <Strings>  
          <ButtonText>MainMenu</ButtonText>  
        </Strings>  
      </Menu>  
  </Menus>  
<Commands>  
```  
  
## <a name="see-also"></a>另请参阅  
 [Vspackage 如何添加用户界面元素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [命令、菜单和工具栏](../extensibility/internals/commands-menus-and-toolbars.md)
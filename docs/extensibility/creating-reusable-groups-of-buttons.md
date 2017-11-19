---
title: "创建可重用的按钮的组 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: "44"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4be8e84c6040f3b4d57082cd39920aec2196e9f7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="creating-reusable-groups-of-buttons"></a>创建可重用的按钮的组
命令组是一套始终可以一起出现，菜单或工具栏的命令。 可以将其分配给不同的父菜单的.vsct 文件的 CommandPlacements 部分中重新使用任何命令组。  
  
 命令组通常包含按钮，但它们还可以包含其他菜单或组合框。  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>若要创建一组可重用按钮  
  
1.  创建一个名为的 VSIX 项目`ReusableButtons`。 有关详细信息，请参阅[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
2.  在项目打开，添加名为的自定义命令项模板**ReusableCommand**。 在**解决方案资源管理器**，右键单击项目节点并选择**添加 / 新项**。 在**添加新项**对话框中，转到**Visual C# / 可扩展性**和选择**自定义命令**。 在**名称**在窗口底部字段中，命令文件名称更改为**ReusableCommand.cs**。  
  
3.  在.vsct 文件中，转到符号部分，并找到包含组和项目的命令的 GuidSymbol 元素。 它应命名 guidReusableCommandPackageCmdSet。  
  
4.  添加将添加到组，如以下示例所示的每个按钮 IDSymbol。  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     默认情况下，命令项模板创建一个名为组**MyGroup**和一个按钮，已提供，以及每个 IDSymbol 条目的名称。  
  
5.  在组部分中，创建具有给定符号部分中的相同的 GUID 和 ID 属性的组元素。 你也可以使用现有组，或使用提供的命令模板，如以下示例所示的条目。 此组将出现在**工具**菜单  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>若要创建一组以供重复使用的按钮  
  
1.  通过使用组作为父项的命令或菜单上，定义中或将组中的命令或菜单放使用 CommandPlacements 部分，可在组中将命令或菜单。  
  
     按钮部分中定义你组作为其父级，一个按钮，或使用由包模板提供的按钮，如下面的示例中所示。  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  如果一个按钮必须出现在多个组中，创建一个条目为其在 CommandPlacements 部分中，必须置于之后的命令部分。 设置 CommandPlacement 元素以匹配你想要放置的按钮的 GUID 和 ID 属性，然后设置的 GUID 和 ID 其父元素的目标组中，如下面的示例中所示。  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  优先级字段的值确定该命令在新的命令组中的位置。 在元素重写这些设置在项定义 CommandPlacement 设置优先级别。 在具有较高优先级值的命令之前，会显示具有较低的优先级值的命令。 允许使用重复的优先级值，但不能保证具有相同的优先级值的命令的相对位置，因为的顺序**devenv /setup**命令从注册表中创建的最后一个接口可能不一致。  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>菜单中放置一组可重用按钮  
  
1.  创建将项记入`CommandPlacements`部分。 设置的 GUID 和 ID`CommandPlacement`元素与你的组，并将设置父 GUID 和 ID 为这些目标位置。  
  
     CommandPlacements 部分应放置之后的命令部分：  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     命令组可以包含多个菜单上。 父 menu 可以是指你创建一个由提供[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]（为所述 ShellCmdDef.vsct 或 SharedCmdDef.vsct），或在另一个 VSPackage 中定义的另一个。 设置父级层数不受限制，只要父菜单最终连接到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]或到 VSPackage 显示的快捷菜单。  
  
     下面的示例将组置于上**解决方案资源管理器**工具栏上，其他按钮右侧。  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">  
          <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements>  
      <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"   
          priority="0x605">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />  
      </CommandPlacement>  
    </CommandPlacements>  
  
    ```
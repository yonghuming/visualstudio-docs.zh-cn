---
title: "绑定到菜单项的键盘快捷方式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 15
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
ms.openlocfilehash: e75976be74d7d0362102a2cbeb32a85d3e612c67
ms.lasthandoff: 02/22/2017

---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>绑定的键盘快捷方式菜单项
要绑定到自定义菜单命令的键盘快捷方式，只需向包.vsct 文件添加一个条目。 本主题说明如何映射到自定义按钮、 菜单项或工具栏命令的键盘快捷方式以及如何将应用在默认的编辑器的键盘映射或将其限制为自定义编辑器。  
  
 若要将键盘快捷方式分配给现有的 Visual Studio 菜单项，请参阅[标识并自定义键盘快捷键](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。  
  
## <a name="choosing-a-key-combination"></a>选择一个键组合  
 已在 Visual Studio 中使用多个键盘快捷方式。 不应将相同的快捷方式分配给多个命令，因为重复的绑定是难以检测到，也可能会导致不可预知的结果。 因此，它是验证的可用性的一种快捷方式之前将其分配一个好主意。  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>若要验证的可用性的键盘快捷方式  
  
1.  在**工具 / 选项 / 环境**窗口中，选择**键盘**。  
  
2.  请确保**新快捷键**设置为**全局**。  
  
3.  在**按快捷键**框中，键入你想要使用的键盘快捷方式。  
  
     如果已在 Visual Studio 中使用快捷方式**当前使用的快捷键**框将显示该快捷方式当前调用的命令。  
  
4.  直到您找到未映射，请尝试不同的密钥的组合。  
  
    > [!NOTE]
    >  使用 ALT 的键盘快捷方式可能会打开菜单，并不是直接执行命令。 因此，**当前使用的快捷键**框可能为空，当您键入的快捷方式，包括 ALT 时。 您可以验证快捷方式不会打开一个菜单，通过关闭**选项**对话框中，然后按这些键。  
  
 下面的过程假定你具有现有 VSPackage 与菜单命令。 如果您需要执行此操作的帮助，看一看[使用菜单命令创建扩展](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>若要为命令分配键盘快捷方式  
  
1.  打开您的软件包的.vsct 文件。  
  
2.  创建一个空`<KeyBindings>`部分之后`<Commands>`如果它尚不存在。  
  
    > [!WARNING]
    >  键绑定的详细信息，请参阅[Keybinding](../extensibility/keybinding-element.md)。  
  
     在`<KeyBindings>`部分中，创建`<KeyBinding>`条目。  
  
     设置`guid`和`id`属性对那些想要调用的命令。  
  
     设置`mod1`属性设为**控件**， **Alt**，或**Shift**。  
  
     键绑定部分应如下所示︰  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 如果您的键盘快捷方式需要两个以上的键，则设置`mod2`和`key2`属性。  
  
 在大多数情况下， **Shift**不应在由于已按导致大多数键入大写字母或符号的字母数字键使用不带第二个修饰符。  
  
 虚拟键代码让您可访问不含有字符与它们，例如，功能键相关联的特殊键和**退格符**键。 有关详细信息，请参阅[虚拟键代码](http://go.microsoft.com/fwlink/?LinkID=105932)。  
  
 若要使此命令可用在 Visual Studio 编辑器中，将设置`editor`属性设为`guidVSStd97`。  
  
 若要使该命令仅适用于自定义编辑器，将设置`editor`属性由生成的自定义编辑器的名称为[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]包模板创建 VSPackage 时包括自定义编辑器。 若要查找的名称值，请查看`<Symbols>`部分`<GuidSymbol>`节点其`name`以属性结尾"`editorfactory`。"这是自定义编辑器的名称。  
  
## <a name="example"></a>示例  
 此示例绑定到名为的命令的键盘快捷方式 CTRL + ALT + C`cmdidMyCommand`在名为包中`MyPackage`。  
  
```  
<CommandTable>  
. . .  
<Commands>  
. . .  
</Commands>  
<KeyBindings>  
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"   
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />  
</KeyBindings>  
. . .  
</CommandTable>  
```  
  
## <a name="example"></a>示例  
 此示例绑定到名为的命令的键盘快捷方式 CTL + B`cmdidBold`中一个名为项目`TestEditor`。 命令为仅在自定义编辑器中并不在其他编辑器中可用。  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>另请参阅  
 [扩展的菜单和命令](../extensibility/extending-menus-and-commands.md)

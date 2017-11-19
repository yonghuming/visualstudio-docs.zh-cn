---
title: "演练： 创建使用 JavaScript SDK |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a87ee7d1a48c313a29d00524d471b46ef572f4a3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>演练： 创建使用 JavaScript SDK
本演练介绍如何使用 JavaScript 创建一个简单的数学 SDK 作为 Visual Studio 扩展 (VSIX)。  本演练分为三个部分：  
  
-   [若要创建 SimpleMathVSIX 扩展 SDK 项目](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
-   [若要创建的示例应用程序使用 SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
 为 JavaScript 没有类库项目类型。 在本演练中，在 VSIX 项目中直接创建示例 arithmetic.js 文件。 在实践中，我们建议您首先生成和测试的 JavaScript 和 CSS 文件为 Windows 应用商店应用-例如，通过使用**空白应用程序**模板-将它们放在 VSIX 项目之前。  
  
## <a name="prerequisites"></a>先决条件  
 要按照本演练的步骤操作，必须安装 Visual Studio SDK。 有关详细信息，请参阅[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
##  <a name="createSimpleMathVSIX"></a>若要创建 SimpleMathVSIX 扩展 SDK 项目  
  
1.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
2.  在列表中的模板类别下**Visual C#**，选择**扩展性**，然后选择**VSIX 项目**模板。  
  
3.  在**名称**文本框中，指定`SimpleMathVSIX`选择**确定**按钮。  
  
4.  如果**Visual Studio 包向导**出现时，选择**下一步**按钮上**欢迎**页上，然后在**7 的第 1 页**，选择**完成**按钮。  
  
     尽管**清单设计器**打开时，我们将简化本演练通过直接修改清单的文件。  
  
5.  在**解决方案资源管理器**，打开 source.extension.vsixmanifest 文件中的快捷菜单，然后选择**查看代码**。 使用此代码替换文件中的现有内容。  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
      <Metadata>  
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />  
        <DisplayName>Simple Math</DisplayName>  
        <Description>Does basic arithmetic calculations.</Description>  
      </Metadata>  
      <Installation Scope="Global" AllUsers="true">  
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />  
      </Installation>  
      <Dependencies>  
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />  
      </Dependencies>  
      <Assets>  
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />  
      </Assets>  
    </PackageManifest>  
    ```  
  
6.  在**解决方案资源管理器**，打开 SimpleMathVSIX 项目的快捷菜单，然后选择**添加**，**新项**。  
  
7.  在**数据**类别中，选择**XML 文件**，命名该文件`SDKManifest.xml`，然后选择**添加**按钮。  
  
8.  在**解决方案资源管理器**，打开 SDKManifest.xml，为文件的快捷菜单，然后选择**打开**以显示中的文件**XML 编辑器**。  
  
9. 将以下代码添加到 SDKManifest.xml 文件中。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. 在**解决方案资源管理器**，在 SDKManifest.xml 文件的快捷菜单，选择**属性**。  
  
11. 在**属性**窗口中，设置**包括在 VSIX 中的**属性**True**。  
  
12. 在**解决方案资源管理器**，在 SimpleMathVSIX 项目的快捷菜单，选择**添加**，**新文件夹**，并将其命名文件夹`Redist`。  
  
13. 添加下面 Redist 要创建此文件夹结构的子文件夹：  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. 在 \js\ 文件夹的快捷菜单，选择**添加**，**新项**。  
  
15. 下**Visual C# 项**，选择**Web**类别，，然后选择**JavaScript 文件**项。 命名该文件`arithmetic.js`，然后选择**添加**按钮。  
  
16. 下面的代码插入 arithmetic.js:  
  
    ```  
    (function (global) {  
        "use strict";  
        global.Arithmetic = {  
            add: function (firstNumber, secondNumber) {  
                return firstNumber + secondNumber;  
            },  
  
            subtract: function (firstNumber, secondNumber) {  
                return firstNumber - secondNumber;  
            },  
  
            multiply: function (firstNumber, secondNumber) {  
                return firstNumber * secondNumber;  
            },  
  
            divide: function (firstNumber, secondNumber) {  
                return firstNumber / secondNumber;  
            }  
        };  
    })(this);  
  
    ```  
  
17. 在**解决方案资源管理器**，在 arithmetic.js 文件的快捷菜单，选择**属性**。 更改这些属性：  
  
    -   设置**包括在 VSIX 中的**属性**True**。  
  
    -   设置**复制到输出目录**属性**始终复制**。  
  
18. 在**解决方案资源管理器**，在 SimpleMathVSIX 项目的快捷菜单，选择**生成**。  
  
19. 生成该项目的快捷菜单上成功完成后，选择**在文件资源管理器中打开文件夹**。 导航到 \bin\debug\\，并运行`SimpleMathVSIX.vsix`来进行安装。  
  
20. 选择**安装**按钮，让安装完成。  
  
21. 重新启动 Visual Studio。  
  
##  <a name="createSampleApp"></a>若要创建的示例应用程序使用 SDK  
  
1.  在菜单栏上，依次选择“文件” 、“新建” 、“项目” 。  
  
2.  在列表中的模板类别下**JavaScript**，选择**Windows 应用商店**，然后选择**空白应用程序**模板。  
  
3.  在**名称**框中，指定`ArithmeticUI`。 选择“确定”  按钮。  
  
4.  在**解决方案资源管理器**，打开 ArithmeticUI 项目的快捷菜单，然后选择**添加**，**引用**。  
  
5.  下**Windows**，选择**扩展**，请注意，**简单数学**显示。  
  
6.  选择**简单数学**复选框，然后选择**确定**按钮。  
  
7.  在**解决方案资源管理器**下**引用**，请注意，**简单数学**显示引用。 将其展开，并请注意，没有包括 arithmetic.js 的 \js\ 文件夹。 你可以打开 arithmetic.js 若要确认已安装你的源代码。  
  
8.  使用下面的代码替换 default.htm 的内容。  
  
    ```  
    <!DOCTYPE html>  
    <html>  
    <head>  
        <meta charset="utf-8" />  
        <title>ArithmeticUI</title>  
  
        <!-- WinJS references -->  
        <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />  
        <script src="//Microsoft.WinJS.1.0/js/base.js"></script>  
        <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>  
  
        <!-- ArithmeticUI references -->  
        <link href="/css/default.css" rel="stylesheet" />  
        <script src="/js/default.js"></script>  
        <script src="/SimpleMath/js/arithmetic.js"></script>  
    </head>  
    <body>  
        <form>  
        <div id="calculator" class="ms-grid">  
            <input name="firstNumber" id="firstNumber" type="number" step="any">  
            <div id="operators">  
                <button class="operator" type="button">+</button>  
                <button class="operator" type="button">-</button>  
                <button class="operator" type="button">*</button>  
                <button class="operator" type="button">/</button>  
            </div>  
            <input id="secondNumber" type="number">  
            <button class="calculate" type="button">=</button>  
            <input id="result" type="number" name="result" disabled="" readonly="">  
        </div>  
        </form>  
    </body>  
    </html>  
    ```  
  
9. 使用下一个代码替换 \js\default.js 的内容。  
  
    ```  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var operation = null;  
  
        function calculateResult() {  
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),  
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),  
                result = 0;  
  
            if (isNaN(firstNumber) || isNaN(secondNumber)) {  
                result = 0;  
            }  
            else {  
                switch (operation) {  
                    case "+":  
                        result = Arithmetic.add(firstNumber, secondNumber);  
                        break;  
                    case "-":  
                        result = Arithmetic.subtract(firstNumber, secondNumber);  
                        break;  
                    case "*":  
                        result = Arithmetic.multiply(firstNumber, secondNumber);  
                        break;  
                    case "/":  
                        result = Arithmetic.divide(firstNumber, secondNumber);  
                        break;  
                    default:  
                }  
            }  
            document.querySelector("#result").value = result.toString();  
        }  
  
        app.onactivated = function (args) {  
            document.querySelector("#calculator").addEventListener("click", function (event) {  
                if (event.target.tagName.toLowerCase() === "button") {  
                    switch (event.target.className) {  
                        case "operator":  
                            operation = event.target.innerText;  
                            break;  
                        case "calculate":  
                            calculateResult();  
                            break;  
                        default:  
                            break;  
                    }  
                }  
            });  
        };  
  
        app.start();  
    })();  
    ```  
  
10. 用此代码替换 \css\default.css 的内容：  
  
    ```  
    form {  
        display: -ms-grid;  
        -ms-grid-rows: 1fr auto 1fr;  
        -ms-grid-columns: 1fr auto 1fr;  
        height: 100%;  
        width: 100%;  
    }  
  
    button, input[type=number] {  
        margin-right: 5px;  
        -ms-grid-row-align: center;  
    }  
  
    #calculator {  
        -ms-grid-column: 2;  
        -ms-grid-row: 2;  
        display: -ms-grid;  
        -ms-grid-rows: 1fr;  
        -ms-grid-columns: auto min-content auto auto auto;  
    }  
  
    .ms-grid input {  
        width: 5em;  
    }  
  
    #firstNumber {  
        -ms-grid-column: 1;  
        -ms-grid-row-align: center;  
    }  
  
    #operators {  
        -ms-grid-column: 2;  
        -ms-grid-row-align: center;  
    }  
  
        #operators button.operator {  
            margin-bottom: 5px;  
            height: 40px;  
        }  
  
    #secondNumber {  
        -ms-grid-column: 3;  
    }  
  
    button.calculate {  
        -ms-grid-column: 4;  
        -ms-grid-row-align: center;  
        height: 40px;  
    }  
  
    #result {  
        -ms-grid-column: 5;  
    }  
  
    ```  
  
11. 选择 F5 键以生成并运行应用程序。  
  
12. 在应用 UI 中，输入任何两个数字，选择某一操作，，然后选择 **=** 按钮。 将显示正确的结果。  
  
## <a name="see-also"></a>另请参阅  
 [获取软件开发工具包](../extensibility/creating-a-software-development-kit.md)
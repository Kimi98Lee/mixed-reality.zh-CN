---
title: MR 学习 ASA 模块 Azure HoloLens 2 上的空间定位点
description: 请完成本课程来了解如何在混合现实应用程序中实现 Azure 人脸识别。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 混合现实, unity, 教程, hololens
ms.openlocfilehash: c120d22f955d366042bbcb9ac73eaa4f13dc20e9
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415270"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>开始使用 Azure HoloLens 2 上的空间定位点

欢迎使用 HoloLens 2 教程的第二个模块。 开始之前，请确保所有的[先决条件](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens)都已完成。 如果您尚未完成第一种[的基本模块](mrlearning-base.md)尚，建议您首先完成该模块。 如果要从新的 Unity 项目开始，按照中的新项目创建步骤[的基本模块](mrlearning-base.md)。 

## <a name="objectives"></a>目标

* 了解使用 Azure HoloLens 2 的空间定位点进行开发基础的知识

* 创建、 上传和下载空间的定位点

  

## <a name="instructions"></a>说明

### <a name="downloading-and-importing-assets"></a>下载和导入资产
开始时之前, 下载并导入以下资产：

[Azure 空间定位点](https://github.com/azure/azure-spatial-anchors-samples/releases)

[MR 基本模块资产包](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[ASA 模块资产包](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[混合现实工具包](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> 注意：有关如何导入 Azure 空间的定位点、 MR 基本模块资产包的具体说明的步骤 6 和步骤 3 到 4 有关具体说明混合现实工具包 (MRKT) 的特定说明，请参阅步骤 5。

1. 在项目中创建新的场景。 右键单击场景文件夹中，单击"创建，"然后场景。 命名新的场景 ASALearningmodule。

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. 双击 ASALearningmodule 若要查看某些预定义的项目显示以及新的场景。 
3. 配置用于混合的现实开发场景。 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> 注意：显示弹出窗口，指出，"您必须选择一个文件的混合现实工具包。" 单击确定转到步骤 4。

4. 当为 MRTK 选择一个文件，选择，DefaultMixedRealityToolkitConfigurationProfile。

   > 注意：如果必须自己配置的配置文件，请随意使用该副本。

![module2chapter1step4im](images/module2chapter1step4im.PNG)

现在场景配置为使用混合现实。 请确保保存您的场景 (执行此操作与任一控件 / 命令 + S 或单击文件，然后单击保存)。 

5. 导入[Azure 空间的定位点](https://github.com/azure/azure-spatial-anchors-samples/releases)。 若要使用空间的定位点，必须导入此资产。 单击上面的链接并右键单击 AzureSpatialAnchors.unitypackage。 在目标另存为上单击，并将其保存到您的计算机。 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   保存后，请转回 Unity 中，单击资产，转到导入包。 然后单击自定义包...将打开你的计算机文件。 当它们执行操作，查找 Azure 空间的定位点包的保存位置并选择它。 然后单击打开。

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   弹出一个窗口，providingg 工具和设置，并询问您要导入的列表。 选择***所有***的可用的选项，然后单击导入。

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > 注意：请耐心等待，它将需要几分钟来导入。 

   6. 导入[MR 基本模块资产包](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)下一步。 更像步骤 5 中，单击上面的链接。 然后右键单击 BasemoduleAssetsV1 1.unitypackag，并单击目标另存为，并将其保存到您的计算机。

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > 提示：将所有这些资产保存在同一文件夹，以便可以更轻松地查找和有权访问。 它会保留所有内容和组织更好。

   就像步骤 5 中，返回到 Unity、 单击资源，并悬停在导入包。 单击自定义包...你的计算机文件将会再次出现。 请转到你在其中存储的基本模块资产包。 然后选择它。 单击“打开”。

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > 注意：可能需要更高版本在此模块中的多个资产。 按照这些步骤导入所述从该点上的任何资产。 
                                                                                                                                                                                                                    
7. 导入 ASA 模块确认作为导入之前的包使用相同的方法。

### <a name="configuring-your-scene"></a>配置您的场景

在本部分中，我们会将预设和脚本添加到场景中，从而创建一系列演示应用程序中本地定位点和 Azure 空间的定位点的行为方式的基础知识的按钮。

7. 在项目选项卡下的资产文件夹中，单击 ASAmoduleAssets。 选择后，你将看到两个预设：ButtonParent 和 ParentAnchor。

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. 将这两个预设拖到场景。 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. 双击父定位点，以将其选中。 您可能需要调整视图以查看整个场景。 根据需要调整您的场景。

    自行熟悉 ParentAnchor 预设。 目前，游戏对象命名，ParentAnchor，是出于演示目的的彩色多维数据集。 最终，我们，ll 隐藏该多维数据集并将它们作为子级 ParentAnchor 放置我们的内容。 此预设可包括 AzureSpatialAnchorsDemoWrapper.cs 脚本 （包含在 ASA SDK），以及作为 ParentAnchor 对象到此模块的一部分包含的 ASAmoduleScript.cs 脚本。 

10. 配置按钮。 下 ParentAnchor 预设，请注意，多个标记的按钮。 从 MRTK PressableButton 预设，则创建这些按钮。 了解有关如何创建从 Pressable 按钮的详细信息[的基本模块](mrlearning-base-ch2.md)。 每个按钮，将添加在用户按下或选择根据下面的列表按钮时，将触发的事件。 

- 对于名为 StartAzureSession，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。 将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 StartAzureSession() 方法。

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- 对于按钮名称，StopAzureSession，创建新的事件下按下按钮事件触发器，以及在单击事件触发器。 将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 StopAzureSession() 方法。

- 对于名为 CreateAnchor，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。 将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 CreateAzureAnchor() 方法。

- 按钮命名为，开始查找的定位点，创建一个新按钮按下的事件"事件触发器，以及在单击事件触发器。 将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 FindAzureAnchor() 方法。

- 对于名为 DeleteAzureAnchor，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。 将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 DeleteAzureAnchor() 方法。

- 对于名为，删除本地定位点，按钮创建新事件下按下按钮事件触发器，以及在单击事件触发器。 将 ParentAnchor 对象拖到空的字段，并从 ParentAnchor 对象 ASAmoduleScript 组件分配 RemoveLocalAnchor() 方法。

### <a name="build-and-demonstrate-base-application"></a>生成并演示基本应用程序

现在，您的场景配置来演示 Azure 空间的定位点的基础知识，我们将生成并演示 Azure 空间的定位点的基本行为。 

1. 如果在前面的部分关闭了“生成设置”窗口，请转到“文件”>“生成设置”，再次打开生成设置窗口。
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. 请确保你想要尝试的场景是在生成列表中的场景中通过单击添加打开场景按钮。

3. 按“生成”按钮开始生成过程。
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. 为应用程序创建一个新文件夹并为其命名。 在下图中，创建具有名称应用的文件夹以包含应用程序。 单击选择文件夹若要开始新创建的文件夹中生成。 在 Unity 中完成生成后，你可以关闭生成设置"窗口。 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > 注意：如果生成失败，尝试再次生成或重启 Unity 并再次生成。 如果看到错误，如“错误：CS0246 = 找不到"XX"键入或命名空间名称 (是否缺少 using 指令或程序集引用？)。 可能需要安装[Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. 生成完成后，打开包含新生成的应用程序文件的新创建的文件夹。 双击 the"MixedRealityBase.sln 解决方案或相应的名称。 如果你的项目的替代名称用于在 Visual Studio 中打开解决方案文件。

  > 注意：请务必打开新创建的文件夹 （即，应用程序文件夹，如果从前面的步骤遵循命名约定，因为外部不会与生成文件夹中的.sln 文件混淆，该文件夹的类似名称的.sln 文件。 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > 注意：如果 Visual Studio 要求安装新组件，请花点时间以确保安装所有必备组件中的具体["安装工具"页](install-the-tools.md) 

6. 使用 USB 电缆将 HoloLens 2 插入电脑。 虽然这些课程说明假设将部署使用 HoloLens 2 设备进行测试，但是您还可选择将部署到[HoloLens 2 模拟器](using-the-hololens-emulator.md)或选择创建[的旁加载应用包](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. 在生成到设备之前，请确保设备处于开发者模式。 如果这是你第一次部署到 HoloLens 2，Visual Studio 可能会要求你将 HoloLens 2 与 pin 配对。 请按照[这些说明](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio)如果你需要启用开发人员模式或与 Visual Studio 配对。

8. 通过选择发布配置和"RM"体系结构为构建到 HoloLens 2 配置 Visual Studio。
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. 最后一步是向你的设备通过选择生成调试 > 启动但不调试。 选择但不调试的启动将导致应用程序以使其不显示在 Visual Studio 中的成功生成 ithout 调试信息时在设备上立即启动。 这也意味着可以在 HoloLens 2 上运行应用程序时断开 USB 电缆，而无需停止应用程序。 您还可能选择生成 > 部署解决方案，而无需自动启动该应用程序部署到你的设备。
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10.按照的说明。 当在设备上运行应用程序时，请按照屏幕上的说明。 按场景按钮对应于下面的步骤。
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. 启动空间的定位点会话。
    
    2. 将多维数据集移到另一个位置。
    
    3. 保存该多维数据集的位置的 Azure 空间定位点。
    
    4. 停止 Azure 空间的定位点会话。
    
    5. 删除多维数据集以允许用户移动该多维数据集上的本地定位点。
    6. 将移动到其他位置的多维数据集。
    
    7. 启动 Azure 空间的定位点会话。
    
    8. 查找 Azure 空间 aachors。 
    
    e 您应返回到原始位置，将其放在创建定位点时）。
    9. 删除 Azure 空间的定位点。
    
    10. 停止 Azure 的会话。

### <a name="anchoring-an-experience"></a>锚定的体验

在前面部分中，您学习了 Azure 空间的定位点的基础知识。 我们使用多维数据集来表示和可视化父级游戏对象使用附加的定位点。 在本部分中，您将学习如何通过将其放置 ParentAnchor 对象的子级作为定位整个体验。 对于此示例中，我们使用农历模块程序集演示应用程序创建期间[第 6 课中的基本模块](mrlearning-base-ch6.md)。

1. 搜索农历模块程序集完整预设，并将其拖动到你的层次结构作为子 AnchorParent gameobject 中如下图所示。

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. 模块程序集位置体验，以便在多维数据集中所显示下图中所示。 在应用程序中，用户可能会重新定位整个体验通过移动该多维数据集。 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > 注意：有多种以重新定位体验，包括要切换一个边框环绕体验，请使用 （如多维数据集在此步骤中使用），重新放置对象的位置和旋转 gizmos，请使用一个按钮使用的用户体验流和的详细信息。

## <a name="congratulations"></a>祝贺
在本课程中，您学习了 Azure 空间的定位点的基础知识。 此 esson 提供了几个按钮，您可以了解启动和停止 Azure 的会话，并创建、 上载和下载单个设备上的 azure 定位点所需的各种步骤。 在下一课中，我们将了解如何将 Azure 的定位标记 Id 保存到检索，在 HoloLens 2，即使重新启动应用程序。 在系列中，您还将了解如何实现空间对齐方式，并了解有关共享会话 （即将发布的共享模块一部分） 的多用户信息的多个设备之间传输锚点 Id

[下一课：ASA Lesson 2](mrlearning-asa-ch2.md)

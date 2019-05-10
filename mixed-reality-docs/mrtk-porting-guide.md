---
title: 让您的应用程序准备好使用 HoloLens 2
description: 面向开发人员在 HoloLens 上已有一个应用 （第 1 代） 和/或较旧 MRTK，并查找移植到 MRTK 版本 2 和 HoloLens 2。
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
keywords: Windows Mixed Reality 测试，MRTK、 MRTK 版本 2、 HoloLens 2
ms.openlocfilehash: 369470326d815ee711e96264939dd2e0487879b6
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873915"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a><span data-ttu-id="2dee3-104">让您现有的应用程序准备好使用 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2dee3-104">Getting your existing app ready for HoloLens 2</span></span>

<span data-ttu-id="2dee3-105">本指南专门用于帮助开发人员的 HoloLens 具有现有的 Unity 应用程序 （第 1 代） 端口他们新的 HoloLens 2 设备的应用程序。</span><span class="sxs-lookup"><span data-stu-id="2dee3-105">This guide is specifically tailored to help developers who have an existing Unity app for HoloLens (1st gen) to port their application for the new HoloLens 2 device.</span></span> <span data-ttu-id="2dee3-106">有四个关键步骤移植 HoloLens （第 1 代） 到 HoloLens 2 Unity 应用程序。</span><span class="sxs-lookup"><span data-stu-id="2dee3-106">There are four key steps to porting a HoloLens (1st gen) Unity app to HoloLens 2.</span></span> <span data-ttu-id="2dee3-107">以下各节将详细介绍每个阶段的信息。</span><span class="sxs-lookup"><span data-stu-id="2dee3-107">The sections below will detail information for each stage.</span></span> 

| <span data-ttu-id="2dee3-108">步骤 1</span><span class="sxs-lookup"><span data-stu-id="2dee3-108">Step 1</span></span> | <span data-ttu-id="2dee3-109">步骤 2</span><span class="sxs-lookup"><span data-stu-id="2dee3-109">Step 2</span></span> | <span data-ttu-id="2dee3-110">步骤 3</span><span class="sxs-lookup"><span data-stu-id="2dee3-110">Step 3</span></span> | <span data-ttu-id="2dee3-111">步骤 4</span><span class="sxs-lookup"><span data-stu-id="2dee3-111">Step 4</span></span> |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio 徽标](images/visualstudio_logo.png) | ![Unity 徽标](images/unity_logo.png)| ![Unity 图标](images/hololens2_icon.jpg) | ![MRTK 徽标](images/MRTKIcon.jpg) |
| <span data-ttu-id="2dee3-116">下载最新的工具</span><span class="sxs-lookup"><span data-stu-id="2dee3-116">Download latest tools</span></span> | <span data-ttu-id="2dee3-117">更新 Unity 项目</span><span class="sxs-lookup"><span data-stu-id="2dee3-117">Update Unity Project</span></span> | <span data-ttu-id="2dee3-118">针对 ARM 编译</span><span class="sxs-lookup"><span data-stu-id="2dee3-118">Compile for ARM</span></span> | <span data-ttu-id="2dee3-119">将迁移到 MRTK v2</span><span class="sxs-lookup"><span data-stu-id="2dee3-119">Migrate to MRTK v2</span></span>

<span data-ttu-id="2dee3-120">它是**强烈建议**，才能开始迁移过程，开发人员利用源代码管理，以保存自己的应用程序的原始状态的快照。</span><span class="sxs-lookup"><span data-stu-id="2dee3-120">It is **highly recommended** that, before beginning the porting process, developers utilize source control to save a snapshot of the original state of their app.</span></span> <span data-ttu-id="2dee3-121">此外，建议向*保存*在过程中的不同位置的检查点状态。</span><span class="sxs-lookup"><span data-stu-id="2dee3-121">Additionally, it is recommended to *save* checkpoint states at various points during the process.</span></span> <span data-ttu-id="2dee3-122">它可以是非常有益的原始应用程序以在端口过程中用于通过并行比较的另一个 Unity 实例。</span><span class="sxs-lookup"><span data-stu-id="2dee3-122">It can also be very helpful to have another Unity instance of the original app to allow for side-by-side comparison during the port process.</span></span> 

> [!NOTE]
> <span data-ttu-id="2dee3-123">移植之前，请确保已安装用于 Windows Mixed Reality 开发最新工具。</span><span class="sxs-lookup"><span data-stu-id="2dee3-123">Before porting, ensure you have the latest tools installed for Windows Mixed Reality development.</span></span> <span data-ttu-id="2dee3-124">对于大多数现有的 HoloLens 开发人员，这将主要涉及更新到最新的 Visual Studio 2017 并安装相应的 Windows SDK。</span><span class="sxs-lookup"><span data-stu-id="2dee3-124">For most existing HoloLens developers, this will primarily involve updating to the latest Visual Studio 2017 and installing the appropriate Windows SDK.</span></span> <span data-ttu-id="2dee3-125">深入了解以下内容将进一步深入到不同的 Unity 版本和混合现实工具包版本 2。</span><span class="sxs-lookup"><span data-stu-id="2dee3-125">The content below will dive further into different Unity versions and the Mixed Reality Toolkit version 2.</span></span>
>
> <span data-ttu-id="2dee3-126">有关详细信息，请参阅[安装的工具](install-the-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="2dee3-126">For more information, please see [Install the tools](install-the-tools.md).</span></span>

## <a name="migrate-project-to-latest-version-of-unity"></a><span data-ttu-id="2dee3-127">将项目迁移到最新版本的 Unity</span><span class="sxs-lookup"><span data-stu-id="2dee3-127">Migrate project to latest version of Unity</span></span>

<span data-ttu-id="2dee3-128">如果使用 MRTK v2，Unity 2018 LTS 将不进行任何重大更改或 MRTK Unity 中的最佳的长期支持路径。</span><span class="sxs-lookup"><span data-stu-id="2dee3-128">If using the MRTK v2, then Unity 2018 LTS will be the best long-term support path with no breaking changes in Unity or in MRTK.</span></span>  <span data-ttu-id="2dee3-129">建议的 Unity 生成，每个上述"安装工具"是 Unity 2018.3，将成为 Unity 2018 的 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="2dee3-129">The recommended Unity build, per the above "install the tools" is Unity 2018.3, which will become the LTS release for Unity 2018.</span></span>  <span data-ttu-id="2dee3-130">此外，MRTK v2 将始终保证对 Unity 2018 LTS 的支持，但不是一定能保证每次迭代 Unity 支持 2019.x。</span><span class="sxs-lookup"><span data-stu-id="2dee3-130">Further, the MRTK v2 will always guarantee support for Unity 2018 LTS but not necessarily guarantee support for every iteration of Unity 2019.x.</span></span> 

<span data-ttu-id="2dee3-131">若要帮助阐明 Unity 之间其他差异 2018.3.x 或 Unity 2019.1.x，下面的轮廓的权衡这两个版本之间的基数能够编译中 Unity 2019 ARM64 二者的主要区别。</span><span class="sxs-lookup"><span data-stu-id="2dee3-131">To help clarify additional differences between Unity 2018.3.x or Unity 2019.1.x, below outlines the trade-offs between these two versions, with the primary difference of significance being the ability to compile for ARM64 in Unity 2019.</span></span> 

<span data-ttu-id="2dee3-132">开发人员应评估任何[插件依赖项](https://docs.unity3d.com/Manual/Plugins.html)，当前在其项目和是否可以针对 ARM64 生成这些 Dll 中存在。</span><span class="sxs-lookup"><span data-stu-id="2dee3-132">Developers should assess any [plugin dependencies](https://docs.unity3d.com/Manual/Plugins.html) that currently exist in their project and whether or not these DLLs can be built for ARM64.</span></span> <span data-ttu-id="2dee3-133">如果不能为 ARM64 生成硬依赖项插件，其中一个将需要利用 Unity 2018 LTS。</span><span class="sxs-lookup"><span data-stu-id="2dee3-133">If a hard dependency plugin cannot be built for ARM64, then one will have to utilize Unity 2018 LTS.</span></span>


| <span data-ttu-id="2dee3-134">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="2dee3-134">Unity 2018.3.x</span></span> | <span data-ttu-id="2dee3-135">Unity 2019.1 +</span><span class="sxs-lookup"><span data-stu-id="2dee3-135">Unity 2019.1+</span></span> |
|----------|-------------------|
| <span data-ttu-id="2dee3-136">ARM32 生成支持</span><span class="sxs-lookup"><span data-stu-id="2dee3-136">ARM32 build support</span></span> | <span data-ttu-id="2dee3-137">ARM32 和 ARM64 生成支持</span><span class="sxs-lookup"><span data-stu-id="2dee3-137">ARM32 and ARM64 build support</span></span> |
| <span data-ttu-id="2dee3-138">稳定 LTS 生成版本</span><span class="sxs-lookup"><span data-stu-id="2dee3-138">Stable LTS build release</span></span> | <span data-ttu-id="2dee3-139">Beta 稳定性</span><span class="sxs-lookup"><span data-stu-id="2dee3-139">Beta stability</span></span> |
| <span data-ttu-id="2dee3-140">[脚本编写的.NET 后端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)*不推荐使用*</span><span class="sxs-lookup"><span data-stu-id="2dee3-140">[.NET Scripting back-end](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *deprecated*</span></span> | <span data-ttu-id="2dee3-141">[脚本编写的.NET 后端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)*删除*</span><span class="sxs-lookup"><span data-stu-id="2dee3-141">[.NET Scripting back-end](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *removed*</span></span> |
| <span data-ttu-id="2dee3-142">UNET 网络*不推荐使用*</span><span class="sxs-lookup"><span data-stu-id="2dee3-142">UNET Networking *deprecated*</span></span> | <span data-ttu-id="2dee3-143">UNET 网络*删除*</span><span class="sxs-lookup"><span data-stu-id="2dee3-143">UNET Networking *removed*</span></span> |

## <a name="update-sceneproject-settings-in-unity"></a><span data-ttu-id="2dee3-144">更新 Unity 中的场景/项目设置</span><span class="sxs-lookup"><span data-stu-id="2dee3-144">Update scene/project settings in Unity</span></span>

<span data-ttu-id="2dee3-145">更新了对 Unity 之后 2018.3.x 或 Unity 2019 + 中，建议更新在 Unity 中的设备上获得最佳结果的特定设置。</span><span class="sxs-lookup"><span data-stu-id="2dee3-145">After updating to Unity 2018.3.x or Unity 2019+, it is recommended to update particular settings in Unity for optimal results on device.</span></span> <span data-ttu-id="2dee3-146">这些设置下的详细信息中所述**[推荐设置为 Unity](Recommended-settings-for-Unity.md)**。</span><span class="sxs-lookup"><span data-stu-id="2dee3-146">These settings are outlined in detail under **[Recommended settings for Unity](Recommended-settings-for-Unity.md)**.</span></span>

<span data-ttu-id="2dee3-147">应重新进行循环访问的[.NET 脚本的后端](https://docs.unity3d.com/Manual/windowsstore-dotnet.html)在 Unity 2018 中弃用并*删除*中 Unity 2019，因此，开发人员应考虑其项目切换到[IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)。</span><span class="sxs-lookup"><span data-stu-id="2dee3-147">It should be re-iterated that the [.NET Scripting back-end](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) is being deprecated in Unity 2018 and *removed* in Unity 2019 and thus, developers should strongly consider switching their project over to [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html).</span></span> 

> [!NOTE]
> <span data-ttu-id="2dee3-148">IL2CPP 脚本编写后端可以到 Visual Studio 从 Unity 导致生成时间较长，因此开发人员应设置为其开发人员计算机[优化 IL2CPP 生成时间](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)。</span><span class="sxs-lookup"><span data-stu-id="2dee3-148">IL2CPP scripting back-end can cause longer build times from Unity to Visual Studio and thus developers should setup their developer machine for [optimizing IL2CPP build times](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).</span></span>

<span data-ttu-id="2dee3-149">之后在迁移到更新的 Unity 版本后寻址任何重大更改，开发人员应生成和测试在 HoloLens 上的其当前应用程序 （第 1 代）。</span><span class="sxs-lookup"><span data-stu-id="2dee3-149">After addressing any breaking changes after moving to the updated Unity version, developers should build and test their current apps on HoloLens (1st gen).</span></span> <span data-ttu-id="2dee3-150">此外，这是很好的点来创建和保存源代码管理的提交。</span><span class="sxs-lookup"><span data-stu-id="2dee3-150">Further, this is a good point to create and save a commit for source control.</span></span> 

## <a name="compile-dependenciesplugins-for-arm-processor"></a><span data-ttu-id="2dee3-151">编译为 ARM 处理器的依赖项/插件</span><span class="sxs-lookup"><span data-stu-id="2dee3-151">Compile dependencies/plugins for ARM processor</span></span>

<span data-ttu-id="2dee3-152">HoloLens （第 1 代） 在 x86 上执行应用程序时新 HoloLens 2 设备利用 ARM 处理器的处理器。</span><span class="sxs-lookup"><span data-stu-id="2dee3-152">HoloLens (1st gen) executed applications on an x86 processor while the new HoloLens 2 device utilizes an ARM processor.</span></span> <span data-ttu-id="2dee3-153">因此，现有的应用程序需要通过移植以支持 ARM。</span><span class="sxs-lookup"><span data-stu-id="2dee3-153">Thus, existing applications need to be ported over to support ARM.</span></span> <span data-ttu-id="2dee3-154">如前文所述，Unity 2018 支持 Unity 2019 + 支持 ARM64 应用的编译时 ARM32 应用的编译。</span><span class="sxs-lookup"><span data-stu-id="2dee3-154">As noted earlier, Unity 2018 supports compiling for ARM32 apps while Unity 2019+ supports compiling for ARM64 apps.</span></span> <span data-ttu-id="2dee3-155">用于 ARM64 的应用程序开发是通常首选，因为性能存在重大差异。</span><span class="sxs-lookup"><span data-stu-id="2dee3-155">Developing for ARM64 applications is generally preferred as there is a material difference in performance.</span></span> <span data-ttu-id="2dee3-156">但是，这需要所有[插件依赖项](https://docs.unity3d.com/Manual/Plugins.html)还生成用于 ARM64。</span><span class="sxs-lookup"><span data-stu-id="2dee3-156">However, this requires all [plugin dependencies](https://docs.unity3d.com/Manual/Plugins.html) to also be built for ARM64.</span></span> 

<span data-ttu-id="2dee3-157">当前查看应用程序中的所有 DLL 依赖项。</span><span class="sxs-lookup"><span data-stu-id="2dee3-157">Review all DLL dependencies in your application currently.</span></span> <span data-ttu-id="2dee3-158">如果不再需要依赖项，则最好从项目中删除它。</span><span class="sxs-lookup"><span data-stu-id="2dee3-158">If a dependency is no longer needed, it is advisable to remove it from your project.</span></span> <span data-ttu-id="2dee3-159">为所需的剩余插件，向你的 Unity 项目中引入各自 ARM32 或 ARM64 二进制文件。</span><span class="sxs-lookup"><span data-stu-id="2dee3-159">For remaining plugins that are required, ingest the respective ARM32 or ARM64 binaries into your Unity project.</span></span> 

<span data-ttu-id="2dee3-160">之后引入相关的 Dll 中的 Unity 生成的 Visual Studio 解决方案，然后编译 Visual Studio 来测试可以针对 ARM 处理器生成你的应用程序中的 ARM AppX。</span><span class="sxs-lookup"><span data-stu-id="2dee3-160">After ingesting the relevant DLLs, build a Visual Studio solution from Unity and then compile an AppX for ARM in Visual Studio to test that your application can be built for ARM processors.</span></span> <span data-ttu-id="2dee3-161">它建议将保存在源代码管理解决方案中的提交此另一个点。</span><span class="sxs-lookup"><span data-stu-id="2dee3-161">This another point where it is advised to save a commit in your source control solution.</span></span> 

## <a name="update-to-mrtk-version-2"></a><span data-ttu-id="2dee3-162">更新到 MRTK 版本 2</span><span class="sxs-lookup"><span data-stu-id="2dee3-162">Update to MRTK version 2</span></span>

<span data-ttu-id="2dee3-163">MRTK 版本 2 是基于 Unity 支持这两个 HoloLens 的新工具包 （第 1 代） 和 HoloLens 2 和其中的所有新的 HoloLens 2 功能已添加，如将交互，并眼睛跟踪。</span><span class="sxs-lookup"><span data-stu-id="2dee3-163">MRTK version 2 is the new toolkit on top of Unity supporting both HoloLens (1st gen) and HoloLens 2, and where all of the new HoloLens 2 capabilities have been added, such as hand interactions and eye tracking.</span></span>

### <a name="prepare-for-the-migration"></a><span data-ttu-id="2dee3-164">为迁移准备</span><span class="sxs-lookup"><span data-stu-id="2dee3-164">Prepare for the migration</span></span>

<span data-ttu-id="2dee3-165">之前引入的新[\*.unitypackage 文件 MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)，建议清点**MRTK v1 与集成，1） 任何自定义生成代码**和**2） 任何自定义生成代码为输入的交互或 UX 组件**。</span><span class="sxs-lookup"><span data-stu-id="2dee3-165">Before ingesting the new [\*.unitypackage files for MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), it is recommended to take an inventory of **1) any custom-built code that integrates with MRTK v1** and **2) any custom-built code for input interactions or UX components**.</span></span> <span data-ttu-id="2dee3-166">最常见和流行，以致 Mixed Reality 开发人员引入新 MRTK v2 冲突将涉及输入和交互。</span><span class="sxs-lookup"><span data-stu-id="2dee3-166">The most common and prevalent conflict for a Mixed Reality developer ingesting the new MRTK v2 will involve input and interactions.</span></span> <span data-ttu-id="2dee3-167">因此，建议在开始阅读和理解[MRTK v2 输入的模型](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)。</span><span class="sxs-lookup"><span data-stu-id="2dee3-167">Thus, it is advised to begin reading and understanding the [MRTK v2 input model](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html).</span></span>

<span data-ttu-id="2dee3-168">最后，新 MRTK v2 已从脚本和场景中管理器对象模型转换到的配置和服务提供程序体系结构。</span><span class="sxs-lookup"><span data-stu-id="2dee3-168">Finally, the new MRTK v2 has transitioned from a model of scripts and in-scene manager objects to a configuration and services provider architecture.</span></span> <span data-ttu-id="2dee3-169">这将导致更简洁的场景层次结构和体系结构模型，但对于了解新的配置文件需要一个学习曲线。</span><span class="sxs-lookup"><span data-stu-id="2dee3-169">This results in a cleaner scene hierarchy and architecture model but requires a learning curve for understanding the new configuration profiles.</span></span> <span data-ttu-id="2dee3-170">因此，请阅读[混合现实工具包配置指南](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)以开始熟悉重要的设置和配置文件，以适应你的应用程序的需求。</span><span class="sxs-lookup"><span data-stu-id="2dee3-170">Thus, please read the [Mixed Reality Toolkit Configuration Guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) to start becoming familiar with the important settings and profiles to adjust to the needs of your application.</span></span> 

### <a name="perform-the-migration"></a><span data-ttu-id="2dee3-171">执行迁移</span><span class="sxs-lookup"><span data-stu-id="2dee3-171">Perform the migration</span></span>

<span data-ttu-id="2dee3-172">导入后 MRTK v2，Unity 项目将可能有许多与编译器相关的错误。</span><span class="sxs-lookup"><span data-stu-id="2dee3-172">After importing MRTK v2, your Unity project will likely have many compiler related errors.</span></span> <span data-ttu-id="2dee3-173">这通常是由于新命名空间的结构和新组件名称。</span><span class="sxs-lookup"><span data-stu-id="2dee3-173">These are most commonly due to the new namespace structure and new component names.</span></span> <span data-ttu-id="2dee3-174">继续通过修改你对新的命名空间和组件的脚本来纠正这些错误。</span><span class="sxs-lookup"><span data-stu-id="2dee3-174">Proceed to resolve these errors by modifying your scripts to the new namespaces and components.</span></span> 

<span data-ttu-id="2dee3-175">HTK/MRTK 和 MRTK 版本 2 之间的特定 API 差异的详细信息，请参阅迁移指南上[MRTK 版本 2 wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)。</span><span class="sxs-lookup"><span data-stu-id="2dee3-175">For more information on specific API differences between HTK/MRTK and MRTK version 2, see the porting guide on the [MRTK Version 2 wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).</span></span>

### <a name="best-practices"></a><span data-ttu-id="2dee3-176">最佳做法</span><span class="sxs-lookup"><span data-stu-id="2dee3-176">Best practices</span></span>

- <span data-ttu-id="2dee3-177">更喜欢使用 MRTK 标准着色器</span><span class="sxs-lookup"><span data-stu-id="2dee3-177">Prefer use of the MRTK Standard shader</span></span>
- <span data-ttu-id="2dee3-178">上一个重大工作一次更改类型 (例如：到 IMixedRealityFocusHandler IFocusable)</span><span class="sxs-lookup"><span data-stu-id="2dee3-178">Work on one breaking change type at a time (ex: IFocusable to IMixedRealityFocusHandler)</span></span>
- <span data-ttu-id="2dee3-179">每次更改后测试并使用源代码管理</span><span class="sxs-lookup"><span data-stu-id="2dee3-179">Test after every change and utilize source control</span></span>
- <span data-ttu-id="2dee3-180">使用默认的 MRTK UX （按钮、 平板电脑等） 在可能的情况</span><span class="sxs-lookup"><span data-stu-id="2dee3-180">Use default MRTK UX (buttons, slates, etc) when possible</span></span>
- <span data-ttu-id="2dee3-181">尝试避免直接修改 MRTK 文件，请改为创建包装 MRTK 组件</span><span class="sxs-lookup"><span data-stu-id="2dee3-181">Try to refrain from modifying MRTK files directly, instead create wrappers around MRTK components</span></span>
    - <span data-ttu-id="2dee3-182">这将防止将来 MRTK ingestions 和更新</span><span class="sxs-lookup"><span data-stu-id="2dee3-182">This will protect against future MRTK ingestions and updates</span></span>
- <span data-ttu-id="2dee3-183">查看和探索 MRTK 中提供的示例场景 (尤其是*HandInteractionExamples.scene*)</span><span class="sxs-lookup"><span data-stu-id="2dee3-183">Review & explore sample scenes provided in MRTK (especially *HandInteractionExamples.scene*)</span></span>
- <span data-ttu-id="2dee3-184">而是重新生成基于画布的 UI 与四边形、 碰撞体和 TextMeshPro 文本</span><span class="sxs-lookup"><span data-stu-id="2dee3-184">Rebuild canvas-based UI with quads, colliders and TextMeshPro text instead</span></span>

### <a name="testing-your-application"></a><span data-ttu-id="2dee3-185">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="2dee3-185">Testing your application</span></span>

<span data-ttu-id="2dee3-186">现在，MRTK 版本 2 中提供了 HoloLens 2 组件和功能在[RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1)，可以模拟直接在 Unity 中，手动交互，并针对用于手动交互和的眼跟踪的新 Api 进行开发。</span><span class="sxs-lookup"><span data-stu-id="2dee3-186">Now that HoloLens 2 components and capabilities are available in MRTK version 2, as of [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1), you can simulate the hand interactions directly in Unity, and develop against the new APIs for hand interactions and eye tracking.</span></span>  <span data-ttu-id="2dee3-187">HoloLens 2 设备需要创建更完美的体验，但至少一个可以开始学习工具和文档中。</span><span class="sxs-lookup"><span data-stu-id="2dee3-187">The HoloLens 2 device is required to create a great experience, but at least one could start learning in the tools and documentation.</span></span> <span data-ttu-id="2dee3-188">此外，MRTK v2 支持在 HoloLens 上开发 （第 1 代） 和传统输入因此，模型如通过敲击选择仍在 HoloLens 上测试 （第 1 代） 设备。</span><span class="sxs-lookup"><span data-stu-id="2dee3-188">Further, MRTK v2 supports development on HoloLens (1st gen) and thus, traditional input models such as select via air-tap can still be tested on HoloLens (1st gen) devices.</span></span> 

## <a name="updating-interaction-model-for-hololens-2"></a><span data-ttu-id="2dee3-189">HoloLens 2 更新交互模型</span><span class="sxs-lookup"><span data-stu-id="2dee3-189">Updating interaction model for HoloLens 2</span></span>

<span data-ttu-id="2dee3-190">在应用程序移植并准备好 HoloLens 2 后，你现可考虑更新您的交互模型和全息图设计/的位置。</span><span class="sxs-lookup"><span data-stu-id="2dee3-190">Once you have your app ported and prepped for HoloLens 2, you are ready to consider updating your interaction model and hologram designs/placement.</span></span>
<span data-ttu-id="2dee3-191">来自 HoloLens （第 1 代），应用可能具有的视线移动并提交交互模型，与全息相对较远而无法放入视图的字段。</span><span class="sxs-lookup"><span data-stu-id="2dee3-191">Coming from HoloLens (1st gen), your app likely has a gaze and commit interaction model, with holograms relatively far away to fit into the field of view.</span></span>

<span data-ttu-id="2dee3-192">若要更新您的应用程序设计为最适合 HoloLens 2 的步骤：</span><span class="sxs-lookup"><span data-stu-id="2dee3-192">Steps to update your app design to be best for HoloLens 2:</span></span>
1.  <span data-ttu-id="2dee3-193">MRTK 组件：每个预工作，如果添加 MRTK v2，有各种组件/利用的脚本已进行了设计和优化 HoloLens 2。</span><span class="sxs-lookup"><span data-stu-id="2dee3-193">MRTK components: Per the pre-work, if you added MRTK v2, there are various components/scripts to leverage that have been designed and optimized for HoloLens 2.</span></span>

2.  <span data-ttu-id="2dee3-194">交互模型：请考虑更新您的交互模型。</span><span class="sxs-lookup"><span data-stu-id="2dee3-194">Interaction model: Consider updating your interaction model.</span></span>  <span data-ttu-id="2dee3-195">大多数情况下，我们建议从注视切换并提交到手中。</span><span class="sxs-lookup"><span data-stu-id="2dee3-195">For most scenarios, we recommend switching from gaze and commit to hands.</span></span>  <span data-ttu-id="2dee3-196">使用你通常要超出手臂达到的全息，切换到手将导致最交互指针大气并获取手势。</span><span class="sxs-lookup"><span data-stu-id="2dee3-196">With your holograms typically being out of arms reach, switching to hands will result in far interaction pointing rays and grab gestures.</span></span>
<span data-ttu-id="2dee3-197">注意： 在无需手动交互模型是必需的如任务工作线程持有工具，并且没有这种情况下的特定设计指南的情况下。</span><span class="sxs-lookup"><span data-stu-id="2dee3-197">Note: there are scenarios where a hands-free interaction model is required, such as a task worker holding tools, and there is specific design guidance for such cases.</span></span> 

3.  <span data-ttu-id="2dee3-198">全息图放置：后切换到手交互模型，请考虑更接近移动某些全息与用手，使用附近交互随取即行手势全息直接交互。</span><span class="sxs-lookup"><span data-stu-id="2dee3-198">Hologram placement: After switching to a hands interaction model, consider moving some holograms closer to directly interact with the holograms with your hands, using near interaction grab gestures.</span></span>  <span data-ttu-id="2dee3-199">全息建议更接近直接获取，或进行交互的类型是较小的目标菜单、 控件、 按钮和较小全息适合 HoloLens 2 视图的字段时捕获并检查全息图。</span><span class="sxs-lookup"><span data-stu-id="2dee3-199">The types of holograms recommended to move closer to directly grab or interact are small target menus, controls, buttons, and smaller holograms that fit within the HoloLens 2 field of view when grabbing and inspecting the hologram.</span></span>
<br>
<span data-ttu-id="2dee3-200">每个应用程序和方案都不同，并且我们将继续进行优化和发布帖子设计指南的反馈基础并继续了解的情况。</span><span class="sxs-lookup"><span data-stu-id="2dee3-200">Every app and scenario is different, and we’ll continue to refine and post design guidance based on feedback and continued learnings.</span></span>


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a><span data-ttu-id="2dee3-201">从应用程序从 x86 移动到 ARM 的更多知识</span><span class="sxs-lookup"><span data-stu-id="2dee3-201">Additional learnings from moving apps from x86 to ARM</span></span>

- <span data-ttu-id="2dee3-202">可以生成一个 ARM appx 捆绑包，也可以直接向设备部署并运行它，直接 Unity 应用非常简单。</span><span class="sxs-lookup"><span data-stu-id="2dee3-202">Straight Unity apps are simple as you can build an ARM appx bundle or deploy directly to the device and it runs.</span></span>
<span data-ttu-id="2dee3-203">Unity 应用程序使用本机插件时，面临的挑战。</span><span class="sxs-lookup"><span data-stu-id="2dee3-203">The challenge comes when the Unity app uses native plugins.</span></span>  <span data-ttu-id="2dee3-204">所有本机插件需要升级到 VS2017 和重新生成对于 ARM，以及 Unity 2019，ARM64。</span><span class="sxs-lookup"><span data-stu-id="2dee3-204">All of the native plugins need to be upgraded to VS2017 and rebuilt for ARM, and with Unity 2019, ARM64.</span></span>

- <span data-ttu-id="2dee3-205">一个应用，用于 Unity，AudioKinetic Wwise 插件，所使用的版本没有 UWP ARM 插件。</span><span class="sxs-lookup"><span data-stu-id="2dee3-205">One app, used the AudioKinetic Wwise plugin for Unity, and the version used didn’t have a UWP ARM plugin.</span></span> <span data-ttu-id="2dee3-206">花费几天时间才能重新使用应用程序用于 ARM 的声音。</span><span class="sxs-lookup"><span data-stu-id="2dee3-206">It took several days to re-work the sound in the application to work on ARM.</span></span>

- <span data-ttu-id="2dee3-207">在其他情况下，UWP/ARM 插件可能不存在的应用程序所需的插件、 端口和 HoloLens 2 上运行的能力造成了阻碍。</span><span class="sxs-lookup"><span data-stu-id="2dee3-207">In other cases, a UWP/ARM plugin may not exist for app-required plugins, blocking the ability to port and run on HoloLens 2.</span></span>  <span data-ttu-id="2dee3-208">可能需要插件提供商合作，以取消阻止，支持 ARM。</span><span class="sxs-lookup"><span data-stu-id="2dee3-208">Engagement with the plugin provider may be needed to unblock and support ARM.</span></span>

- <span data-ttu-id="2dee3-209">在着色器 minfloat （和变量，例如 min16float、 minint、 等） 的行为可能有所不同 HoloLen 2 比在 HoloLens 上 （第 1 代）。</span><span class="sxs-lookup"><span data-stu-id="2dee3-209">The minfloat (and variants such as min16float, minint, etc…) in shaders may behave differently on HoloLen 2 than on HoloLens (1st gen).</span></span> <span data-ttu-id="2dee3-210">具体而言，这些保证"至少指定将使用比特数"。</span><span class="sxs-lookup"><span data-stu-id="2dee3-210">Specifically, these guarantee that “at least the specified number of bits will be used”.</span></span> <span data-ttu-id="2dee3-211">Intel/Nvidia Gpu 上这些很大程度上就被视为 32 位。</span><span class="sxs-lookup"><span data-stu-id="2dee3-211">On Intel/Nvidia GPUs, these are largely just treated as 32 bits.</span></span> <span data-ttu-id="2dee3-212">在 ARM，实际上遵循指定的位数。</span><span class="sxs-lookup"><span data-stu-id="2dee3-212">On ARM, the number of bits specified is actually respected.</span></span> <span data-ttu-id="2dee3-213">这意味着，在实践中，这些数字可能具有较少精度/范围 HoloLens 2 上与在 HoloLens 上 （第 1 代）。</span><span class="sxs-lookup"><span data-stu-id="2dee3-213">That means that in practice, these numbers may have less precision/range on HoloLens 2 than they did on HoloLens (1st gen).</span></span>

- <span data-ttu-id="2dee3-214">_Asm 说明不会显示用于 ARM，这意味着使用 _asm 说明的任何代码必须重写。</span><span class="sxs-lookup"><span data-stu-id="2dee3-214">The _asm instructions don’t appear to work on ARM, meaning any code using _asm instructions will have to be rewritten.</span></span>

- <span data-ttu-id="2dee3-215">ARM 不支持 SIMD 指令集。</span><span class="sxs-lookup"><span data-stu-id="2dee3-215">The SIMD instruction set is not supported on ARM.</span></span> <span data-ttu-id="2dee3-216">这意味着各种标头，例如 xmmintrin.h、 emmintrin.h、 tmmintrin.h 和 immintrin.h 不是在 ARM 上可用。</span><span class="sxs-lookup"><span data-stu-id="2dee3-216">This means various headers, such as xmmintrin.h, emmintrin.h, tmmintrin.h, and immintrin.h are not available on ARM.</span></span>

- <span data-ttu-id="2dee3-217">着色器编译器在 ARM 运行时期间的第一个绘图调用后的着色器已加载或着色器的内容依赖于已更改，不是在着色器加载时间。</span><span class="sxs-lookup"><span data-stu-id="2dee3-217">The shader compiler on ARM runs during the first draw call after the shader has been loaded or something the shader relies on has changed, not at shader load time.</span></span> <span data-ttu-id="2dee3-218">对帧速率的影响可以是非常明显，具体取决于多少着色器需要进行编译。</span><span class="sxs-lookup"><span data-stu-id="2dee3-218">The impact on framerate can be very noticeable, depending on how many shaders need to be compiled.</span></span> <span data-ttu-id="2dee3-219">这有不同的含义的着色器应如何处理/打包/更新以不同的方式上 HoloLens 2 vs HoloLens （第 1 代）。</span><span class="sxs-lookup"><span data-stu-id="2dee3-219">This has various implications for how shaders should be handled/packaged/updated differently on HoloLens 2 vs HoloLens (1st gen).</span></span>

## <a name="see-also"></a><span data-ttu-id="2dee3-220">请参阅</span><span class="sxs-lookup"><span data-stu-id="2dee3-220">See also</span></span>
* [<span data-ttu-id="2dee3-221">开始使用 MRTK 版本 2</span><span class="sxs-lookup"><span data-stu-id="2dee3-221">Getting started with MRTK version 2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="2dee3-222">MRTK 版本 2 操作方法</span><span class="sxs-lookup"><span data-stu-id="2dee3-222">MRTK Version 2 HowTo</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [<span data-ttu-id="2dee3-223">安装工具</span><span class="sxs-lookup"><span data-stu-id="2dee3-223">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="2dee3-224">建议用于 Unity 的设置</span><span class="sxs-lookup"><span data-stu-id="2dee3-224">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="2dee3-225">混合现实的了解性能</span><span class="sxs-lookup"><span data-stu-id="2dee3-225">Understanding performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)

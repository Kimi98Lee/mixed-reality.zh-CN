---
title: 双手和动作控制器
description: 双手和动作控制器交互的概述
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: 混合现实，手、 运动控制器、 交互，设计
ms.openlocfilehash: 583d284ee98b8ccbc0a9c2c8670551d0a7397074
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873997"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="cb71c-104">双手和动作控制器</span><span class="sxs-lookup"><span data-stu-id="cb71c-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="cb71c-105">方案</span><span class="sxs-lookup"><span data-stu-id="cb71c-105">Scenarios</span></span>
<span data-ttu-id="cb71c-106">如果选择读取后采用此交互模型[设计准则](interaction-fundamentals.md)，这意味着您在开发应用程序要求用户使用两只手进行与 holographic 世界交互。</span><span class="sxs-lookup"><span data-stu-id="cb71c-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="cb71c-107">你的应用程序要实现删除之间虚拟和物理边界的目标。</span><span class="sxs-lookup"><span data-stu-id="cb71c-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="cb71c-108">某些特定方案可能是：</span><span class="sxs-lookup"><span data-stu-id="cb71c-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="cb71c-109">提供信息工作人员 2D 虚拟屏幕和 Ui 用于显示和控制内容</span><span class="sxs-lookup"><span data-stu-id="cb71c-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="cb71c-110">提供第一个行辅助角色教程和工厂的程序集行中的指南</span><span class="sxs-lookup"><span data-stu-id="cb71c-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="cb71c-111">开发用于协助和培训医疗专业人员的专业工具</span><span class="sxs-lookup"><span data-stu-id="cb71c-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="cb71c-112">使用 3D 虚拟对象来修饰现实世界，或若要创建第二个世界</span><span class="sxs-lookup"><span data-stu-id="cb71c-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="cb71c-113">创建位置基于服务和作为背景中使用实际的游戏</span><span class="sxs-lookup"><span data-stu-id="cb71c-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="cb71c-114">双手和动作控制器模式</span><span class="sxs-lookup"><span data-stu-id="cb71c-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-near-hand-interactiondirect-manipulationmd"></a>[<span data-ttu-id="cb71c-115">直接操作 （附近手动交互）</span><span class="sxs-lookup"><span data-stu-id="cb71c-115">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
<span data-ttu-id="cb71c-116">这是利用的手，用户了支持的触摸和直接操作全息模态。</span><span class="sxs-lookup"><span data-stu-id="cb71c-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="cb71c-117">通过 leaveraging 日常生活体验和提供适当的可视化提示，用户就能够使用相同的方法来操作实际对象与虚拟的交互。</span><span class="sxs-lookup"><span data-stu-id="cb71c-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world obejcts to interact with virtual ones.</span></span>   

### <a name="point-and-commit-far-hand-interactionpoint-and-commitmd"></a>[<span data-ttu-id="cb71c-118">点和提交 （Far 手动交互）</span><span class="sxs-lookup"><span data-stu-id="cb71c-118">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
<span data-ttu-id="cb71c-119">此模式为用户提供超级全息距离与之交互的能力。</span><span class="sxs-lookup"><span data-stu-id="cb71c-119">This modality provides users super power to interact with holograms in a distance.</span></span> <span data-ttu-id="cb71c-120">它使用户能够充分利用的周围的设置。</span><span class="sxs-lookup"><span data-stu-id="cb71c-120">It enables users to make the best use of setting of surrounding.</span></span> <span data-ttu-id="cb71c-121">用户可以在任意位置全息和仍可以从任何距离访问它们。</span><span class="sxs-lookup"><span data-stu-id="cb71c-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="cb71c-122">心理模型和用于控制和操作 2D 和 3D 全息手势是高度与同步的直接操作。</span><span class="sxs-lookup"><span data-stu-id="cb71c-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="cb71c-123">运动控制器</span><span class="sxs-lookup"><span data-stu-id="cb71c-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="cb71c-124">运动控制器是通过使用一个或两个指针时为单位的距离大范围内提供精确交互来扩展用户的物理功能的工具。</span><span class="sxs-lookup"><span data-stu-id="cb71c-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="cb71c-125">这些硬件附件提供了许多常用的交互，并提供 surefooted、 触觉反馈的各种操作的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="cb71c-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="cb71c-126">目前，motion 控制器是仅适用于 WMR 方案。</span><span class="sxs-lookup"><span data-stu-id="cb71c-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="cb71c-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="cb71c-127">See also</span></span>
* [<span data-ttu-id="cb71c-128">视线移动和提交</span><span class="sxs-lookup"><span data-stu-id="cb71c-128">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="cb71c-129">直接操作 （附近手动交互）</span><span class="sxs-lookup"><span data-stu-id="cb71c-129">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
* [<span data-ttu-id="cb71c-130">点和提交 （Far 手动交互）</span><span class="sxs-lookup"><span data-stu-id="cb71c-130">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
* [<span data-ttu-id="cb71c-131">Hands-free</span><span class="sxs-lookup"><span data-stu-id="cb71c-131">Hands-free</span></span>](hands-free.md)
* [<span data-ttu-id="cb71c-132">设定凝视目标</span><span class="sxs-lookup"><span data-stu-id="cb71c-132">Gaze targeting</span></span>](gaze-targeting.md)
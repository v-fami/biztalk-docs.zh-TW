---
title: 執行 Orchestrations3 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, running
- Receive shape [Orchestration Designer], starting orchestrations
- Start Orchestration shape [Orchestration Designer], starting orchestrations
- Call Orchestration shape [Orchestration Designer], starting orchestrations
- Receive shape [Orchestration Designer], activating orchestrations
ms.assetid: 5bfe61c9-80e0-4a0a-b6b1-ab48037e665e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 550fc1e03f3583215a817028917000c9a9c3074a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269046"
---
# <a name="running-orchestrations"></a><span data-ttu-id="77097-102">執行協調流程</span><span class="sxs-lookup"><span data-stu-id="77097-102">Running Orchestrations</span></span>
<span data-ttu-id="77097-103">協調流程執行個體都是設計成觸發藉由從另一個協調流程的明確呼叫 — 使用**呼叫協調流程**圖形或**啟動協調流程**圖形 — 或透過接收啟動訊息。</span><span class="sxs-lookup"><span data-stu-id="77097-103">Orchestration instances are designed to be triggered either by an explicit call from another orchestration—using a **Call Orchestration** shape or **Start Orchestration** shape—or by receipt of an activation message.</span></span> <span data-ttu-id="77097-104">啟動訊息結構描述中指定**訊息**屬性。</span><span class="sxs-lookup"><span data-stu-id="77097-104">The activation message schema is specified in the **Message** property.</span></span> <span data-ttu-id="77097-105">您應該同理，設計您的協調流程，而且其中一個設定**Activate**屬性**接收**true，或請確定呼叫的協調流程存在且已正確設定成執行圖形新的協調流程。</span><span class="sxs-lookup"><span data-stu-id="77097-105">You should design your orchestration accordingly, and either set the **Activate** property on a **Receive** shape to true, or make sure that a calling orchestration exists and is configured properly to run the new orchestration.</span></span>  
  
 <span data-ttu-id="77097-106">執行任何執行個體之前，您必須先繫結和部署 BizTalk 組件，然後登錄和啟動協調流程引擎以開始處理。</span><span class="sxs-lookup"><span data-stu-id="77097-106">Before any instances can run, you must first bind and deploy the BizTalk assembly, and then enlist and start the orchestration engine to begin processing.</span></span> <span data-ttu-id="77097-107">如需詳細資訊，請參閱[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)和[部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="77097-107">For more information, see [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md) and [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md).</span></span> <span data-ttu-id="77097-108">當協調流程由另一個協調流程叫用，或訊息呈現給符合啟動接收中準則的引擎時，引擎會建立新的協調流程執行個體並執行該執行個體。</span><span class="sxs-lookup"><span data-stu-id="77097-108">When an orchestration is invoked from another orchestration, or a message is presented to the engine that matches the criteria in an activation receive, the engine creates a new instance of the orchestration and runs that instance.</span></span> <span data-ttu-id="77097-109">可以同時執行許多不同的執行個體。</span><span class="sxs-lookup"><span data-stu-id="77097-109">It can run many different instances concurrently.</span></span>  
  
## <a name="calling-and-starting-orchestrations"></a><span data-ttu-id="77097-110">呼叫和啟動協調流程</span><span class="sxs-lookup"><span data-stu-id="77097-110">Calling and starting orchestrations</span></span>  
 <span data-ttu-id="77097-111">**呼叫協調流程**圖形和**啟動協調流程**圖形可以用來啟動另一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="77097-111">The **Call Orchestration** shape and **Start Orchestration** shape can be used to activate another orchestration.</span></span> <span data-ttu-id="77097-112">在這兩種情況下，呼叫者可傳送參數與其他協調流程交換資訊。</span><span class="sxs-lookup"><span data-stu-id="77097-112">In both cases, the caller can pass in parameters to exchange information with the other orchestration.</span></span> <span data-ttu-id="77097-113">如需詳細資訊，請參閱[如何將參數加入至協調流程](../core/how-to-add-parameters-to-orchestrations.md)。</span><span class="sxs-lookup"><span data-stu-id="77097-113">For more information, see [How to Add Parameters to Orchestrations](../core/how-to-add-parameters-to-orchestrations.md).</span></span>  
  
## <a name="using-activation-receives-with-filter-expression"></a><span data-ttu-id="77097-114">搭配篩選條件運算式使用啟動接收</span><span class="sxs-lookup"><span data-stu-id="77097-114">Using activation receives with filter expression</span></span>  
 <span data-ttu-id="77097-115">**接收**圖形也可以使用以要求啟用的其他條件的篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="77097-115">The **Receive** shape might also use a filter expression to require further criteria for activation.</span></span> <span data-ttu-id="77097-116">如果訊息是正確的型別，而且某些屬性或訊息屬性符合所有條件的篩選運算式，**接收**圖形會接受訊息，且協調流程會啟動。</span><span class="sxs-lookup"><span data-stu-id="77097-116">If the message is of the correct type and some property or properties of the message meet all of the criteria in the filter expression, the **Receive** shape accepts the message and the orchestration is activated.</span></span> <span data-ttu-id="77097-117">這類 「 接收 」 圖形指*啟動接收*。</span><span class="sxs-lookup"><span data-stu-id="77097-117">Such a Receive shape is referred to as an *activation receive*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77097-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77097-118">See Also</span></span>  
 <span data-ttu-id="77097-119">[如何設定呼叫協調流程圖形](../core/how-to-configure-the-call-orchestration-shape.md) </span><span class="sxs-lookup"><span data-stu-id="77097-119">[How to Configure the Call Orchestration Shape](../core/how-to-configure-the-call-orchestration-shape.md) </span></span>  
 <span data-ttu-id="77097-120">[如何設定啟動協調流程圖形](../core/how-to-configure-the-start-orchestration-shape.md) </span><span class="sxs-lookup"><span data-stu-id="77097-120">[How to Configure the Start Orchestration Shape](../core/how-to-configure-the-start-orchestration-shape.md) </span></span>  
 <span data-ttu-id="77097-121">[如何設定 「 接收 」 圖形](../core/how-to-configure-the-receive-shape.md) </span><span class="sxs-lookup"><span data-stu-id="77097-121">[How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md) </span></span>  
 [<span data-ttu-id="77097-122">建置和執行協調流程</span><span class="sxs-lookup"><span data-stu-id="77097-122">Building and Running Orchestrations</span></span>](../core/building-and-running-orchestrations.md)
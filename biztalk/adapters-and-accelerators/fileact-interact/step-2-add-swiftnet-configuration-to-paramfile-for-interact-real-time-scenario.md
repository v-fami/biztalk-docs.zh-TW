---
title: 步驟 2： 將 SWIFTNet 設定新增至 Paramfile 針對 InterAct 即時案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a900a6e-3e08-430a-8766-4a7192adba5e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d36758716fb368760e9a93909f70bf4d92c5f840
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992447"
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-interact-real-time-scenario"></a><span data-ttu-id="7f8d7-102">步驟 2： 將 SWIFTNet 設定新增至 Paramfile 針對 InterAct 即時案例</span><span class="sxs-lookup"><span data-stu-id="7f8d7-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="7f8d7-103">若要啟用這些值初始化的接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息夥伴。</span><span class="sxs-lookup"><span data-stu-id="7f8d7-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span> <span data-ttu-id="7f8d7-104">在開始此程序之前，您必須完成中的指示[步驟 1： 互動即時案例設定 SWIFT 配接器](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="7f8d7-104">Before you begin the procedure, you must complete the instructions in [Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md).</span></span>  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="7f8d7-105">若要將 SWIFTNet 設定新增至 paramfile</span><span class="sxs-lookup"><span data-stu-id="7f8d7-105">To add SWIFTNet configuration to the paramfile</span></span>  
  
1. <span data-ttu-id="7f8d7-106">在文字編輯器中，例如 [記事本] 開啟 paramfile。</span><span class="sxs-lookup"><span data-stu-id="7f8d7-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
    <span data-ttu-id="7f8d7-107">Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span><span class="sxs-lookup"><span data-stu-id="7f8d7-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span></span>  
  
2. <span data-ttu-id="7f8d7-108">在 paramfile，請反白顯示的變更指定伺服器訊息的夥伴名稱：</span><span class="sxs-lookup"><span data-stu-id="7f8d7-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
  
    <span data-ttu-id="7f8d7-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="7f8d7-109">username:snlowner</span></span>  
  
    <span data-ttu-id="7f8d7-110">subsystem_name:InteractStub</span><span class="sxs-lookup"><span data-stu-id="7f8d7-110">subsystem_name:InteractStub</span></span>  
  
    <span data-ttu-id="7f8d7-111">\#subsystem_group:InteractRT</span><span class="sxs-lookup"><span data-stu-id="7f8d7-111">\#subsystem_group:InteractRT</span></span>  
  
    <span data-ttu-id="7f8d7-112">\#subsystem_dependency:Support Swarm</span><span class="sxs-lookup"><span data-stu-id="7f8d7-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
    <span data-ttu-id="7f8d7-113">subsystem_nature： 重要</span><span class="sxs-lookup"><span data-stu-id="7f8d7-113">subsystem_nature:critical</span></span>  
  
    <span data-ttu-id="7f8d7-114">subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="7f8d7-114">subsystem_start:</span></span>  
  
    <span data-ttu-id="7f8d7-115">**繁衍"snlreceiver-SagMessagePartner \<Interact RT 的伺服器 MessagePartnerName \> -AdapterMode 互動 」**</span><span class="sxs-lookup"><span data-stu-id="7f8d7-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for Interact RT \> -AdapterMode Interact"**</span></span>  
  
    <span data-ttu-id="7f8d7-116">\* 結束</span><span class="sxs-lookup"><span data-stu-id="7f8d7-116">\*END</span></span>  
  
    <span data-ttu-id="7f8d7-117">subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="7f8d7-117">subsystem_stop:</span></span>  
  
    <span data-ttu-id="7f8d7-118">\* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="7f8d7-118">\*KILL9:snlreceiver</span></span>  
  
    <span data-ttu-id="7f8d7-119">\* 結束</span><span class="sxs-lookup"><span data-stu-id="7f8d7-119">\*END</span></span>  
  
    <span data-ttu-id="7f8d7-120">subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="7f8d7-120">subsystem_status:</span></span>  
  
    <span data-ttu-id="7f8d7-121">\* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="7f8d7-121">\*NB:1:snlreceiver</span></span>  
  
    <span data-ttu-id="7f8d7-122">\* 結束</span><span class="sxs-lookup"><span data-stu-id="7f8d7-122">\*END</span></span>  
  
    <span data-ttu-id="7f8d7-123">start_event:SNL001:subsystem InteractStub 已啟動</span><span class="sxs-lookup"><span data-stu-id="7f8d7-123">start_event:SNL001:subsystem InteractStub is up</span></span>  
  
    <span data-ttu-id="7f8d7-124">stop_event:SNL002:subsystem InteractStub 已關閉</span><span class="sxs-lookup"><span data-stu-id="7f8d7-124">stop_event:SNL002:subsystem InteractStub is down</span></span>  
  
    <span data-ttu-id="7f8d7-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="7f8d7-125">\#subsystem_name:User</span></span>  
  
    <span data-ttu-id="7f8d7-126">\## subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="7f8d7-126">\##subsystem_group:user</span></span>  
  
    <span data-ttu-id="7f8d7-127">\## subsystem_dependency:</span><span class="sxs-lookup"><span data-stu-id="7f8d7-127">\##subsystem_dependency:</span></span>  
  
    <span data-ttu-id="7f8d7-128">\#subsystem_nature： 重要</span><span class="sxs-lookup"><span data-stu-id="7f8d7-128">\#subsystem_nature:critical</span></span>  
  
    <span data-ttu-id="7f8d7-129">\#subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="7f8d7-129">\#subsystem_start:</span></span>  
  
    <span data-ttu-id="7f8d7-130">\#\* 結束</span><span class="sxs-lookup"><span data-stu-id="7f8d7-130">\#\*END</span></span>  
  
    <span data-ttu-id="7f8d7-131">\#subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="7f8d7-131">\#subsystem_stop:</span></span>  
  
    <span data-ttu-id="7f8d7-132">\#\* 結束</span><span class="sxs-lookup"><span data-stu-id="7f8d7-132">\#\*END</span></span>  
  
    <span data-ttu-id="7f8d7-133">\#subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="7f8d7-133">\#subsystem_status:</span></span>  
  
    # <a name="end"></a><span data-ttu-id="7f8d7-134">\* 結束</span><span class="sxs-lookup"><span data-stu-id="7f8d7-134">\*END</span></span>  
  
    # <a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="7f8d7-135">start_event:SNL001:subsystem 使用者已啟動</span><span class="sxs-lookup"><span data-stu-id="7f8d7-135">start_event:SNL001:subsystem User is up</span></span>  
  
    # <a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="7f8d7-136">stop_event:SNL002:subsystem 使用者已關閉</span><span class="sxs-lookup"><span data-stu-id="7f8d7-136">stop_event:SNL002:subsystem User is down</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f8d7-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f8d7-137">See Also</span></span>  
 <span data-ttu-id="7f8d7-138">[InterAct 即時案例](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="7f8d7-138">[InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="7f8d7-139">[步驟 1： 設定 SWIFT 配接器針對 InterAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="7f8d7-139">[Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="7f8d7-140">[步驟 3： 建立傳送和接收的連接埠 InterAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="7f8d7-140">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="7f8d7-141">步驟 4：測試 InterAct 即時端對端案例</span><span class="sxs-lookup"><span data-stu-id="7f8d7-141">Step 4: Test the InterAct Real-Time End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md)
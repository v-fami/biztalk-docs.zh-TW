---
title: 步驟 2： 針對 InterAct 儲存和轉寄案例將 SWIFTNet 設定新增至 Paramfile |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a18a43c-1dd9-4113-bf32-8bc7bf9338b0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9495d6a53e9048dc5dee839f1dc859c62b4e9187
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014495"
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="8a842-102">步驟 2： 針對 InterAct 儲存和轉寄案例將 SWIFTNet 設定新增至 Paramfile</span><span class="sxs-lookup"><span data-stu-id="8a842-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="8a842-103">若要啟用這些值初始化的接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息夥伴。</span><span class="sxs-lookup"><span data-stu-id="8a842-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span>  
  
 <span data-ttu-id="8a842-104">在開始此步驟之前，必須先完成[步驟 1： 設定 SWIFT 配接器針對 InterAct 儲存和轉寄案例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="8a842-104">Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="8a842-105">若要將 SWIFTNet 設定新增至 paramfile</span><span class="sxs-lookup"><span data-stu-id="8a842-105">To add SWIFTNet configuration to the paramfile</span></span>  
  
1. <span data-ttu-id="8a842-106">在文字編輯器中，例如 [記事本] 開啟 paramfile。</span><span class="sxs-lookup"><span data-stu-id="8a842-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="8a842-107">Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile。</span><span class="sxs-lookup"><span data-stu-id="8a842-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile.</span></span>  
  
2. <span data-ttu-id="8a842-108">在 paramfile，請反白顯示的變更指定伺服器訊息的夥伴名稱：</span><span class="sxs-lookup"><span data-stu-id="8a842-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
  
    <span data-ttu-id="8a842-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="8a842-109">username:snlowner</span></span>  
  
    <span data-ttu-id="8a842-110">subsystem_name:InteractStub</span><span class="sxs-lookup"><span data-stu-id="8a842-110">subsystem_name:InteractStub</span></span>  
  
    <span data-ttu-id="8a842-111">\#subsystem_group:Interactsnf</span><span class="sxs-lookup"><span data-stu-id="8a842-111">\#subsystem_group:Interactsnf</span></span>  
  
    <span data-ttu-id="8a842-112">\#subsystem_dependency:Support Swarm</span><span class="sxs-lookup"><span data-stu-id="8a842-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
    <span data-ttu-id="8a842-113">subsystem_nature： 重要</span><span class="sxs-lookup"><span data-stu-id="8a842-113">subsystem_nature:critical</span></span>  
  
    <span data-ttu-id="8a842-114">subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="8a842-114">subsystem_start:</span></span>  
  
    <span data-ttu-id="8a842-115">**繁衍"snlreceiver-SagMessagePartner \<Interact SnF 的伺服器 MessagePartnerName\> -AdapterMode 互動 」**</span><span class="sxs-lookup"><span data-stu-id="8a842-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for Interact SnF\> -AdapterMode Interact"**</span></span>  
  
    <span data-ttu-id="8a842-116">\* 結束</span><span class="sxs-lookup"><span data-stu-id="8a842-116">\*END</span></span>  
  
    <span data-ttu-id="8a842-117">subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="8a842-117">subsystem_stop:</span></span>  
  
    <span data-ttu-id="8a842-118">\* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="8a842-118">\*KILL9:snlreceiver</span></span>  
  
    <span data-ttu-id="8a842-119">\* 結束</span><span class="sxs-lookup"><span data-stu-id="8a842-119">\*END</span></span>  
  
    <span data-ttu-id="8a842-120">subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="8a842-120">subsystem_status:</span></span>  
  
    <span data-ttu-id="8a842-121">\* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="8a842-121">\*NB:1:snlreceiver</span></span>  
  
    <span data-ttu-id="8a842-122">\* 結束</span><span class="sxs-lookup"><span data-stu-id="8a842-122">\*END</span></span>  
  
    <span data-ttu-id="8a842-123">start_event:SNL001:subsystem InteractStubSnF 已啟動</span><span class="sxs-lookup"><span data-stu-id="8a842-123">start_event:SNL001:subsystem InteractStubSnF is up</span></span>  
  
    <span data-ttu-id="8a842-124">stop_event:SNL002:subsystem InteractStubSnF 已關閉</span><span class="sxs-lookup"><span data-stu-id="8a842-124">stop_event:SNL002:subsystem InteractStubSnF is down</span></span>  
  
    <span data-ttu-id="8a842-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="8a842-125">\#subsystem_name:User</span></span>  
  
    <span data-ttu-id="8a842-126">\## subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="8a842-126">\##subsystem_group:user</span></span>  
  
    <span data-ttu-id="8a842-127">\## subsystem_dependency:</span><span class="sxs-lookup"><span data-stu-id="8a842-127">\##subsystem_dependency:</span></span>  
  
    <span data-ttu-id="8a842-128">\#subsystem_nature： 重要</span><span class="sxs-lookup"><span data-stu-id="8a842-128">\#subsystem_nature:critical</span></span>  
  
    <span data-ttu-id="8a842-129">\#subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="8a842-129">\#subsystem_start:</span></span>  
  
    <span data-ttu-id="8a842-130">\#\* 結束</span><span class="sxs-lookup"><span data-stu-id="8a842-130">\#\*END</span></span>  
  
    <span data-ttu-id="8a842-131">\#subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="8a842-131">\#subsystem_stop:</span></span>  
  
    <span data-ttu-id="8a842-132">\#\* 結束</span><span class="sxs-lookup"><span data-stu-id="8a842-132">\#\*END</span></span>  
  
    <span data-ttu-id="8a842-133">\#subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="8a842-133">\#subsystem_status:</span></span>  
  
    <span data-ttu-id="8a842-134">\#\* 結束</span><span class="sxs-lookup"><span data-stu-id="8a842-134">\#\*END</span></span>  
  
    # <a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="8a842-135">start_event:SNL001:subsystem 使用者已啟動</span><span class="sxs-lookup"><span data-stu-id="8a842-135">start_event:SNL001:subsystem User is up</span></span>  
  
    # <a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="8a842-136">stop_event:SNL002:subsystem 使用者已關閉</span><span class="sxs-lookup"><span data-stu-id="8a842-136">stop_event:SNL002:subsystem User is down</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a842-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a842-137">See Also</span></span>  
 <span data-ttu-id="8a842-138">[InterAct 儲存和轉寄 （推送） 案例](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8a842-138">[InterAct Store and Forward (Push) Scenario](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span></span>  
 <span data-ttu-id="8a842-139">[步驟 1： 針對 InterAct 儲存和轉寄案例設定 SWIFT 配接器](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8a842-139">[Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="8a842-140">[步驟 3： 建立傳送埠和接收埠以進行 InterAct 儲存和轉寄案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8a842-140">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="8a842-141">步驟 4：測試 InterAct 儲存和轉寄端對端案例</span><span class="sxs-lookup"><span data-stu-id="8a842-141">Step 4: Test the InterAct Store and Forward End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)
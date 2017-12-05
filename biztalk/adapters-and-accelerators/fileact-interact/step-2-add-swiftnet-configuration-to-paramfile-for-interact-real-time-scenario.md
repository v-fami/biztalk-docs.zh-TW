---
title: "步驟 2： 將 SWIFTNet 組態新增至為 Paramfile 互動即時案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a900a6e-3e08-430a-8766-4a7192adba5e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e33203279e045b28d2098ca78c55403c7070b64
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-interact-real-time-scenario"></a><span data-ttu-id="ce809-102">步驟 2： 將 SWIFTNet 組態新增至為 Paramfile 互動即時案例</span><span class="sxs-lookup"><span data-stu-id="ce809-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="ce809-103">若要啟用以這些值來初始化接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息協力廠商。</span><span class="sxs-lookup"><span data-stu-id="ce809-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span> <span data-ttu-id="ce809-104">在開始此程序之前，您必須完成的指示[步驟 1： 設定 SWIFT 配接器的互動即時實例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="ce809-104">Before you begin the procedure, you must complete the instructions in [Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md).</span></span>  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="ce809-105">若要將 SWIFTNet 組態新增至 paramfile</span><span class="sxs-lookup"><span data-stu-id="ce809-105">To add SWIFTNet configuration to the paramfile</span></span>  
  
1.  <span data-ttu-id="ce809-106">在文字編輯器中，例如 [記事本] 開啟 paramfile。</span><span class="sxs-lookup"><span data-stu-id="ce809-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
     <span data-ttu-id="ce809-107">Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span><span class="sxs-lookup"><span data-stu-id="ce809-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span></span>  
  
2.  <span data-ttu-id="ce809-108">在 paramfile，請指定伺服器訊息夥伴名稱的反白顯示的變更：</span><span class="sxs-lookup"><span data-stu-id="ce809-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
  
     <span data-ttu-id="ce809-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="ce809-109">username:snlowner</span></span>  
  
     <span data-ttu-id="ce809-110">subsystem_name:InteractStub</span><span class="sxs-lookup"><span data-stu-id="ce809-110">subsystem_name:InteractStub</span></span>  
  
     <span data-ttu-id="ce809-111">\#subsystem_group:InteractRT</span><span class="sxs-lookup"><span data-stu-id="ce809-111">\#subsystem_group:InteractRT</span></span>  
  
     <span data-ttu-id="ce809-112">\#subsystem_dependency:Support 群集</span><span class="sxs-lookup"><span data-stu-id="ce809-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
     <span data-ttu-id="ce809-113">subsystem_nature： 重大</span><span class="sxs-lookup"><span data-stu-id="ce809-113">subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="ce809-114">subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="ce809-114">subsystem_start:</span></span>  
  
     <span data-ttu-id="ce809-115">**繁衍"snlreceiver-SagMessagePartner\<互動 RT 的伺服器 MessagePartnerName \> -AdapterMode 互動 」**</span><span class="sxs-lookup"><span data-stu-id="ce809-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for Interact RT \> -AdapterMode Interact"**</span></span>  
  
     <span data-ttu-id="ce809-116">* 結束</span><span class="sxs-lookup"><span data-stu-id="ce809-116">*END</span></span>  
  
     <span data-ttu-id="ce809-117">subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="ce809-117">subsystem_stop:</span></span>  
  
     <span data-ttu-id="ce809-118">* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="ce809-118">*KILL9:snlreceiver</span></span>  
  
     <span data-ttu-id="ce809-119">* 結束</span><span class="sxs-lookup"><span data-stu-id="ce809-119">*END</span></span>  
  
     <span data-ttu-id="ce809-120">subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="ce809-120">subsystem_status:</span></span>  
  
     <span data-ttu-id="ce809-121">* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="ce809-121">*NB:1:snlreceiver</span></span>  
  
     <span data-ttu-id="ce809-122">* 結束</span><span class="sxs-lookup"><span data-stu-id="ce809-122">*END</span></span>  
  
     <span data-ttu-id="ce809-123">start_event:SNL001:subsystem InteractStub 已啟動</span><span class="sxs-lookup"><span data-stu-id="ce809-123">start_event:SNL001:subsystem InteractStub is up</span></span>  
  
     <span data-ttu-id="ce809-124">stop_event:SNL002:subsystem InteractStub 已關閉</span><span class="sxs-lookup"><span data-stu-id="ce809-124">stop_event:SNL002:subsystem InteractStub is down</span></span>  
  
     <span data-ttu-id="ce809-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="ce809-125">\#subsystem_name:User</span></span>  
  
     <span data-ttu-id="ce809-126">\## subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="ce809-126">\##subsystem_group:user</span></span>  
  
     <span data-ttu-id="ce809-127">\## subsystem_dependency:</span><span class="sxs-lookup"><span data-stu-id="ce809-127">\##subsystem_dependency:</span></span>  
  
     <span data-ttu-id="ce809-128">\#subsystem_nature： 重大</span><span class="sxs-lookup"><span data-stu-id="ce809-128">\#subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="ce809-129">\#subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="ce809-129">\#subsystem_start:</span></span>  
  
     <span data-ttu-id="ce809-130">\#* 結束</span><span class="sxs-lookup"><span data-stu-id="ce809-130">\#*END</span></span>  
  
     <span data-ttu-id="ce809-131">\#subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="ce809-131">\#subsystem_stop:</span></span>  
  
     <span data-ttu-id="ce809-132">\#* 結束</span><span class="sxs-lookup"><span data-stu-id="ce809-132">\#*END</span></span>  
  
     <span data-ttu-id="ce809-133">\#subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="ce809-133">\#subsystem_status:</span></span>  
  
     #<a name="end"></a><span data-ttu-id="ce809-134">* 結束</span><span class="sxs-lookup"><span data-stu-id="ce809-134">*END</span></span>  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="ce809-135">start_event:SNL001:subsystem 使用者已啟動</span><span class="sxs-lookup"><span data-stu-id="ce809-135">start_event:SNL001:subsystem User is up</span></span>  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="ce809-136">stop_event:SNL002:subsystem 使用者已關閉</span><span class="sxs-lookup"><span data-stu-id="ce809-136">stop_event:SNL002:subsystem User is down</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce809-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce809-137">See Also</span></span>  
 <span data-ttu-id="ce809-138">[互動即時案例](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ce809-138">[InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="ce809-139">[步驟 1： 設定的 SWIFT 配接器互動即時案例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ce809-139">[Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="ce809-140">[步驟 3： 建立傳送和接收埠互動即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ce809-140">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="ce809-141">步驟 4：測試 InterAct 即時端對端案例</span><span class="sxs-lookup"><span data-stu-id="ce809-141">Step 4: Test the InterAct Real-Time End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md)
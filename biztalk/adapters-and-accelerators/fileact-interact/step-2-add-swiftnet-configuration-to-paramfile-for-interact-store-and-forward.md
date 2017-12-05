---
title: "步驟 2： 將 SWIFTNet 組態新增至 Paramfile 互動存放區和情況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a18a43c-1dd9-4113-bf32-8bc7bf9338b0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05524abd4cd57b8d804ab5995072905392fd3645
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="bb841-102">步驟 2： 將 SWIFTNet 組態新增至 Paramfile 互動存放區和轉寄的案例</span><span class="sxs-lookup"><span data-stu-id="bb841-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="bb841-103">若要啟用以這些值來初始化接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息協力廠商。</span><span class="sxs-lookup"><span data-stu-id="bb841-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span>  
  
 <span data-ttu-id="bb841-104">在開始此步驟之前，必須先完成[步驟 1： 設定 SWIFT 配接器，為互動存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="bb841-104">Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="bb841-105">若要將 SWIFTNet 組態新增至 paramfile</span><span class="sxs-lookup"><span data-stu-id="bb841-105">To add SWIFTNet configuration to the paramfile</span></span>  
  
1.  <span data-ttu-id="bb841-106">在文字編輯器中，例如 [記事本] 開啟 paramfile。</span><span class="sxs-lookup"><span data-stu-id="bb841-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb841-107">Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile。</span><span class="sxs-lookup"><span data-stu-id="bb841-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile.</span></span>  
  
2.  <span data-ttu-id="bb841-108">在 paramfile，請指定伺服器訊息夥伴名稱的反白顯示的變更：</span><span class="sxs-lookup"><span data-stu-id="bb841-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
  
     <span data-ttu-id="bb841-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="bb841-109">username:snlowner</span></span>  
  
     <span data-ttu-id="bb841-110">subsystem_name:InteractStub</span><span class="sxs-lookup"><span data-stu-id="bb841-110">subsystem_name:InteractStub</span></span>  
  
     <span data-ttu-id="bb841-111">\#subsystem_group:Interactsnf</span><span class="sxs-lookup"><span data-stu-id="bb841-111">\#subsystem_group:Interactsnf</span></span>  
  
     <span data-ttu-id="bb841-112">\#subsystem_dependency:Support 群集</span><span class="sxs-lookup"><span data-stu-id="bb841-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
     <span data-ttu-id="bb841-113">subsystem_nature： 重大</span><span class="sxs-lookup"><span data-stu-id="bb841-113">subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="bb841-114">subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="bb841-114">subsystem_start:</span></span>  
  
     <span data-ttu-id="bb841-115">**繁衍"snlreceiver-SagMessagePartner\<互動 SnF 的伺服器 MessagePartnerName\> -AdapterMode 互動 」**</span><span class="sxs-lookup"><span data-stu-id="bb841-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for Interact SnF\> -AdapterMode Interact"**</span></span>  
  
     <span data-ttu-id="bb841-116">* 結束</span><span class="sxs-lookup"><span data-stu-id="bb841-116">*END</span></span>  
  
     <span data-ttu-id="bb841-117">subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="bb841-117">subsystem_stop:</span></span>  
  
     <span data-ttu-id="bb841-118">* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="bb841-118">*KILL9:snlreceiver</span></span>  
  
     <span data-ttu-id="bb841-119">* 結束</span><span class="sxs-lookup"><span data-stu-id="bb841-119">*END</span></span>  
  
     <span data-ttu-id="bb841-120">subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="bb841-120">subsystem_status:</span></span>  
  
     <span data-ttu-id="bb841-121">* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="bb841-121">*NB:1:snlreceiver</span></span>  
  
     <span data-ttu-id="bb841-122">* 結束</span><span class="sxs-lookup"><span data-stu-id="bb841-122">*END</span></span>  
  
     <span data-ttu-id="bb841-123">start_event:SNL001:subsystem InteractStubSnF 已啟動</span><span class="sxs-lookup"><span data-stu-id="bb841-123">start_event:SNL001:subsystem InteractStubSnF is up</span></span>  
  
     <span data-ttu-id="bb841-124">stop_event:SNL002:subsystem InteractStubSnF 已關閉</span><span class="sxs-lookup"><span data-stu-id="bb841-124">stop_event:SNL002:subsystem InteractStubSnF is down</span></span>  
  
     <span data-ttu-id="bb841-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="bb841-125">\#subsystem_name:User</span></span>  
  
     <span data-ttu-id="bb841-126">\## subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="bb841-126">\##subsystem_group:user</span></span>  
  
     <span data-ttu-id="bb841-127">\## subsystem_dependency:</span><span class="sxs-lookup"><span data-stu-id="bb841-127">\##subsystem_dependency:</span></span>  
  
     <span data-ttu-id="bb841-128">\#subsystem_nature： 重大</span><span class="sxs-lookup"><span data-stu-id="bb841-128">\#subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="bb841-129">\#subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="bb841-129">\#subsystem_start:</span></span>  
  
     <span data-ttu-id="bb841-130">\#* 結束</span><span class="sxs-lookup"><span data-stu-id="bb841-130">\#*END</span></span>  
  
     <span data-ttu-id="bb841-131">\#subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="bb841-131">\#subsystem_stop:</span></span>  
  
     <span data-ttu-id="bb841-132">\#* 結束</span><span class="sxs-lookup"><span data-stu-id="bb841-132">\#*END</span></span>  
  
     <span data-ttu-id="bb841-133">\#subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="bb841-133">\#subsystem_status:</span></span>  
  
     <span data-ttu-id="bb841-134">\#* 結束</span><span class="sxs-lookup"><span data-stu-id="bb841-134">\#*END</span></span>  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="bb841-135">start_event:SNL001:subsystem 使用者已啟動</span><span class="sxs-lookup"><span data-stu-id="bb841-135">start_event:SNL001:subsystem User is up</span></span>  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="bb841-136">stop_event:SNL002:subsystem 使用者已關閉</span><span class="sxs-lookup"><span data-stu-id="bb841-136">stop_event:SNL002:subsystem User is down</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb841-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="bb841-137">See Also</span></span>  
 <span data-ttu-id="bb841-138">[儲存和轉送 (Push) 的案例進行互動](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="bb841-138">[InterAct Store and Forward (Push) Scenario](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span></span>  
 <span data-ttu-id="bb841-139">[步驟 1： 設定 SWIFT 配接器互動存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="bb841-139">[Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="bb841-140">[步驟 3： 建立傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="bb841-140">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="bb841-141">步驟 4：測試 InterAct 儲存和轉寄端對端案例</span><span class="sxs-lookup"><span data-stu-id="bb841-141">Step 4: Test the InterAct Store and Forward End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)
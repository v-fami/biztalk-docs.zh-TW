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
ms.openlocfilehash: 78aa75762e40bfcdd033a057610cb34f38825dd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="23755-102">步驟 2： 將 SWIFTNet 組態新增至 Paramfile 互動存放區和轉寄的案例</span><span class="sxs-lookup"><span data-stu-id="23755-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="23755-103">若要啟用以這些值來初始化接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息協力廠商。</span><span class="sxs-lookup"><span data-stu-id="23755-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span>  
  
 <span data-ttu-id="23755-104">在開始此步驟之前，必須先完成[步驟 1： 設定 SWIFT 配接器，為互動存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="23755-104">Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="23755-105">若要將 SWIFTNet 組態新增至 paramfile</span><span class="sxs-lookup"><span data-stu-id="23755-105">To add SWIFTNet configuration to the paramfile</span></span>  
  
1.  <span data-ttu-id="23755-106">在文字編輯器中，例如 [記事本] 開啟 paramfile。</span><span class="sxs-lookup"><span data-stu-id="23755-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="23755-107">Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile。</span><span class="sxs-lookup"><span data-stu-id="23755-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile.</span></span>  
  
2.  <span data-ttu-id="23755-108">在 paramfile，請指定伺服器訊息夥伴名稱的反白顯示的變更：</span><span class="sxs-lookup"><span data-stu-id="23755-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
  
     <span data-ttu-id="23755-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="23755-109">username:snlowner</span></span>  
  
     <span data-ttu-id="23755-110">subsystem_name:InteractStub</span><span class="sxs-lookup"><span data-stu-id="23755-110">subsystem_name:InteractStub</span></span>  
  
     <span data-ttu-id="23755-111">\#subsystem_group:Interactsnf</span><span class="sxs-lookup"><span data-stu-id="23755-111">\#subsystem_group:Interactsnf</span></span>  
  
     <span data-ttu-id="23755-112">\#subsystem_dependency:Support 群集</span><span class="sxs-lookup"><span data-stu-id="23755-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
     <span data-ttu-id="23755-113">subsystem_nature： 重大</span><span class="sxs-lookup"><span data-stu-id="23755-113">subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="23755-114">subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="23755-114">subsystem_start:</span></span>  
  
     <span data-ttu-id="23755-115">**繁衍"snlreceiver-SagMessagePartner\<互動 SnF 的伺服器 MessagePartnerName >-AdapterMode 互動 」**</span><span class="sxs-lookup"><span data-stu-id="23755-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for Interact SnF> -AdapterMode Interact"**</span></span>  
  
     <span data-ttu-id="23755-116">* 結束</span><span class="sxs-lookup"><span data-stu-id="23755-116">*END</span></span>  
  
     <span data-ttu-id="23755-117">subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="23755-117">subsystem_stop:</span></span>  
  
     <span data-ttu-id="23755-118">* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="23755-118">*KILL9:snlreceiver</span></span>  
  
     <span data-ttu-id="23755-119">* 結束</span><span class="sxs-lookup"><span data-stu-id="23755-119">*END</span></span>  
  
     <span data-ttu-id="23755-120">subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="23755-120">subsystem_status:</span></span>  
  
     <span data-ttu-id="23755-121">* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="23755-121">*NB:1:snlreceiver</span></span>  
  
     <span data-ttu-id="23755-122">* 結束</span><span class="sxs-lookup"><span data-stu-id="23755-122">*END</span></span>  
  
     <span data-ttu-id="23755-123">start_event:SNL001:subsystem InteractStubSnF 已啟動</span><span class="sxs-lookup"><span data-stu-id="23755-123">start_event:SNL001:subsystem InteractStubSnF is up</span></span>  
  
     <span data-ttu-id="23755-124">stop_event:SNL002:subsystem InteractStubSnF 已關閉</span><span class="sxs-lookup"><span data-stu-id="23755-124">stop_event:SNL002:subsystem InteractStubSnF is down</span></span>  
  
     <span data-ttu-id="23755-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="23755-125">\#subsystem_name:User</span></span>  
  
     <span data-ttu-id="23755-126">\## subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="23755-126">\##subsystem_group:user</span></span>  
  
     <span data-ttu-id="23755-127">\## subsystem_dependency:</span><span class="sxs-lookup"><span data-stu-id="23755-127">\##subsystem_dependency:</span></span>  
  
     <span data-ttu-id="23755-128">\#subsystem_nature： 重大</span><span class="sxs-lookup"><span data-stu-id="23755-128">\#subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="23755-129">\#subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="23755-129">\#subsystem_start:</span></span>  
  
     <span data-ttu-id="23755-130">\#* 結束</span><span class="sxs-lookup"><span data-stu-id="23755-130">\#*END</span></span>  
  
     <span data-ttu-id="23755-131">\#subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="23755-131">\#subsystem_stop:</span></span>  
  
     <span data-ttu-id="23755-132">\#* 結束</span><span class="sxs-lookup"><span data-stu-id="23755-132">\#*END</span></span>  
  
     <span data-ttu-id="23755-133">\#subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="23755-133">\#subsystem_status:</span></span>  
  
     <span data-ttu-id="23755-134">\#* 結束</span><span class="sxs-lookup"><span data-stu-id="23755-134">\#*END</span></span>  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="23755-135">start_event:SNL001:subsystem 使用者已啟動</span><span class="sxs-lookup"><span data-stu-id="23755-135">start_event:SNL001:subsystem User is up</span></span>  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="23755-136">stop_event:SNL002:subsystem 使用者已關閉</span><span class="sxs-lookup"><span data-stu-id="23755-136">stop_event:SNL002:subsystem User is down</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23755-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23755-137">See Also</span></span>  
 <span data-ttu-id="23755-138">[儲存和轉送 (Push) 的案例進行互動](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="23755-138">[InterAct Store and Forward (Push) Scenario](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span></span>  
 <span data-ttu-id="23755-139">[步驟 1： 設定 SWIFT 配接器互動存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="23755-139">[Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="23755-140">[步驟 3： 建立傳送埠和接收埠以進行互動的存放區和轉寄的案例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="23755-140">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="23755-141">步驟 4： 測試互動存放區和轉寄的端對端案例</span><span class="sxs-lookup"><span data-stu-id="23755-141">Step 4: Test the InterAct Store and Forward End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)
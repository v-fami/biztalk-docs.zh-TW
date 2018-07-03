---
title: 步驟 2： 針對 FileAct 即時案例將 SWIFTNet 設定新增至 Paramfile |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4feec3f-4755-477e-b3d6-1dd6d075255e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f40da4b503a5b29e161b376fc25f535c338f5f42
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010559"
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-fileact-real-time-scenario"></a><span data-ttu-id="ee5cc-102">步驟 2： 針對 FileAct 即時案例將 SWIFTNet 設定新增至 Paramfile</span><span class="sxs-lookup"><span data-stu-id="ee5cc-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="ee5cc-103">若要啟用這些值初始化的接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息夥伴。</span><span class="sxs-lookup"><span data-stu-id="ee5cc-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span>  
  
 <span data-ttu-id="ee5cc-104">在開始此步驟之前，必須先完成[步驟 1： 針對 FileAct 即時案例設定 SWIFT 配接器](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="ee5cc-104">Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md).</span></span>  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="ee5cc-105">若要將 SWIFTNet 設定新增至 paramfile</span><span class="sxs-lookup"><span data-stu-id="ee5cc-105">To add SWIFTNet configuration to the paramfile</span></span>  
  
1. <span data-ttu-id="ee5cc-106">在文字編輯器中，例如 [記事本] 開啟 paramfile。</span><span class="sxs-lookup"><span data-stu-id="ee5cc-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="ee5cc-107">Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span><span class="sxs-lookup"><span data-stu-id="ee5cc-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span></span>  
  
2. <span data-ttu-id="ee5cc-108">在 paramfile，請反白顯示的變更指定伺服器訊息的夥伴名稱：</span><span class="sxs-lookup"><span data-stu-id="ee5cc-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
  
    <span data-ttu-id="ee5cc-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="ee5cc-109">username:snlowner</span></span>  
  
    <span data-ttu-id="ee5cc-110">subsystem_name:FileactStub</span><span class="sxs-lookup"><span data-stu-id="ee5cc-110">subsystem_name:FileactStub</span></span>  
  
    <span data-ttu-id="ee5cc-111">\#subsystem_group:fileact</span><span class="sxs-lookup"><span data-stu-id="ee5cc-111">\#subsystem_group:fileact</span></span>  
  
    <span data-ttu-id="ee5cc-112">\#subsystem_dependency:Support Swarm</span><span class="sxs-lookup"><span data-stu-id="ee5cc-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
    <span data-ttu-id="ee5cc-113">subsystem_nature： 重要</span><span class="sxs-lookup"><span data-stu-id="ee5cc-113">subsystem_nature:critical</span></span>  
  
    <span data-ttu-id="ee5cc-114">subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="ee5cc-114">subsystem_start:</span></span>  
  
    <span data-ttu-id="ee5cc-115">**繁衍"snlreceiver-SagMessagePartner \<fileact RT 的伺服器 MessagePartnerName \> -AdapterMode fileact"**</span><span class="sxs-lookup"><span data-stu-id="ee5cc-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for fileact RT \> -AdapterMode fileact"**</span></span>  
  
    <span data-ttu-id="ee5cc-116">\* 結束</span><span class="sxs-lookup"><span data-stu-id="ee5cc-116">\*END</span></span>  
  
    <span data-ttu-id="ee5cc-117">subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="ee5cc-117">subsystem_stop:</span></span>  
  
    <span data-ttu-id="ee5cc-118">\* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="ee5cc-118">\*KILL9:snlreceiver</span></span>  
  
    <span data-ttu-id="ee5cc-119">\* 結束</span><span class="sxs-lookup"><span data-stu-id="ee5cc-119">\*END</span></span>  
  
    <span data-ttu-id="ee5cc-120">subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="ee5cc-120">subsystem_status:</span></span>  
  
    <span data-ttu-id="ee5cc-121">\* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="ee5cc-121">\*NB:1:snlreceiver</span></span>  
  
    <span data-ttu-id="ee5cc-122">\* 結束</span><span class="sxs-lookup"><span data-stu-id="ee5cc-122">\*END</span></span>  
  
    <span data-ttu-id="ee5cc-123">start_event:SNL001:subsystem FileactStub 已啟動</span><span class="sxs-lookup"><span data-stu-id="ee5cc-123">start_event:SNL001:subsystem FileactStub is up</span></span>  
  
    <span data-ttu-id="ee5cc-124">stop_event:SNL002:subsystem FileactStub 已關閉</span><span class="sxs-lookup"><span data-stu-id="ee5cc-124">stop_event:SNL002:subsystem FileactStub is down</span></span>  
  
    <span data-ttu-id="ee5cc-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="ee5cc-125">\#subsystem_name:User</span></span>  
  
    <span data-ttu-id="ee5cc-126">\## subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="ee5cc-126">\##subsystem_group:user</span></span>  
  
    <span data-ttu-id="ee5cc-127">\## subsystem_dependency:</span><span class="sxs-lookup"><span data-stu-id="ee5cc-127">\##subsystem_dependency:</span></span>  
  
    <span data-ttu-id="ee5cc-128">\#subsystem_nature： 重要</span><span class="sxs-lookup"><span data-stu-id="ee5cc-128">\#subsystem_nature:critical</span></span>  
  
    <span data-ttu-id="ee5cc-129">\#subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="ee5cc-129">\#subsystem_start:</span></span>  
  
    <span data-ttu-id="ee5cc-130">\#\* 結束</span><span class="sxs-lookup"><span data-stu-id="ee5cc-130">\#\*END</span></span>  
  
    <span data-ttu-id="ee5cc-131">\#subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="ee5cc-131">\#subsystem_stop:</span></span>  
  
    <span data-ttu-id="ee5cc-132">\#\* 結束</span><span class="sxs-lookup"><span data-stu-id="ee5cc-132">\#\*END</span></span>  
  
    <span data-ttu-id="ee5cc-133">\#subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="ee5cc-133">\#subsystem_status:</span></span>  
  
    # <a name="end"></a><span data-ttu-id="ee5cc-134">\* 結束</span><span class="sxs-lookup"><span data-stu-id="ee5cc-134">\*END</span></span>  
  
    # <a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="ee5cc-135">start_event:SNL001:subsystem 使用者已啟動</span><span class="sxs-lookup"><span data-stu-id="ee5cc-135">start_event:SNL001:subsystem User is up</span></span>  
  
    # <a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="ee5cc-136">stop_event:SNL002:subsystem 使用者已關閉</span><span class="sxs-lookup"><span data-stu-id="ee5cc-136">stop_event:SNL002:subsystem User is down</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee5cc-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee5cc-137">See Also</span></span>  
 <span data-ttu-id="ee5cc-138">[FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ee5cc-138">[FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="ee5cc-139">[步驟 1： 針對 FileAct 即時案例設定 SWIFT 配接器](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ee5cc-139">[Step 1: Configure the SWIFT Adapter for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="ee5cc-140">[步驟 3： 建立傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ee5cc-140">[Step 3: Create the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="ee5cc-141">步驟 4：測試 FileAct 即時端對端案例</span><span class="sxs-lookup"><span data-stu-id="ee5cc-141">Step 4: Test FileAct Real-Time End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)
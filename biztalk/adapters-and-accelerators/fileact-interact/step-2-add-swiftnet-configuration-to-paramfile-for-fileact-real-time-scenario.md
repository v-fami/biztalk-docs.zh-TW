---
title: 步驟 2： 將 SWIFTNet 組態新增至 Paramfile FileAct 即時案例 |Microsoft 文件
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
ms.openlocfilehash: adad4d98be93e17bef4ab5eeb9e49271ffc94b74
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963764"
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-fileact-real-time-scenario"></a><span data-ttu-id="611d0-102">步驟 2： 將 SWIFTNet 組態新增至 Paramfile FileAct 即時案例</span><span class="sxs-lookup"><span data-stu-id="611d0-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="611d0-103">若要啟用以這些值來初始化接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息協力廠商。</span><span class="sxs-lookup"><span data-stu-id="611d0-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span>  
  
 <span data-ttu-id="611d0-104">在開始此步驟之前，必須先完成[步驟 1： 設定 SWIFT 配接器 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="611d0-104">Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md).</span></span>  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="611d0-105">若要將 SWIFTNet 組態新增至 paramfile</span><span class="sxs-lookup"><span data-stu-id="611d0-105">To add SWIFTNet configuration to the paramfile</span></span>  
  
1.  <span data-ttu-id="611d0-106">在文字編輯器中，例如 [記事本] 開啟 paramfile。</span><span class="sxs-lookup"><span data-stu-id="611d0-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="611d0-107">Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span><span class="sxs-lookup"><span data-stu-id="611d0-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span></span>  
  
2.  <span data-ttu-id="611d0-108">在 paramfile，請指定伺服器訊息夥伴名稱的反白顯示的變更：</span><span class="sxs-lookup"><span data-stu-id="611d0-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
  
     <span data-ttu-id="611d0-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="611d0-109">username:snlowner</span></span>  
  
     <span data-ttu-id="611d0-110">subsystem_name:FileactStub</span><span class="sxs-lookup"><span data-stu-id="611d0-110">subsystem_name:FileactStub</span></span>  
  
     <span data-ttu-id="611d0-111">\#subsystem_group:fileact</span><span class="sxs-lookup"><span data-stu-id="611d0-111">\#subsystem_group:fileact</span></span>  
  
     <span data-ttu-id="611d0-112">\#subsystem_dependency:Support 群集</span><span class="sxs-lookup"><span data-stu-id="611d0-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
     <span data-ttu-id="611d0-113">subsystem_nature： 重大</span><span class="sxs-lookup"><span data-stu-id="611d0-113">subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="611d0-114">subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="611d0-114">subsystem_start:</span></span>  
  
     <span data-ttu-id="611d0-115">**繁衍"snlreceiver-SagMessagePartner \<fileact RT 的伺服器 MessagePartnerName \> -AdapterMode fileact"**</span><span class="sxs-lookup"><span data-stu-id="611d0-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for fileact RT \> -AdapterMode fileact"**</span></span>  
  
     <span data-ttu-id="611d0-116">\* 結束</span><span class="sxs-lookup"><span data-stu-id="611d0-116">\*END</span></span>  
  
     <span data-ttu-id="611d0-117">subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="611d0-117">subsystem_stop:</span></span>  
  
     <span data-ttu-id="611d0-118">\* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="611d0-118">\*KILL9:snlreceiver</span></span>  
  
     <span data-ttu-id="611d0-119">\* 結束</span><span class="sxs-lookup"><span data-stu-id="611d0-119">\*END</span></span>  
  
     <span data-ttu-id="611d0-120">subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="611d0-120">subsystem_status:</span></span>  
  
     <span data-ttu-id="611d0-121">\* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="611d0-121">\*NB:1:snlreceiver</span></span>  
  
     <span data-ttu-id="611d0-122">\* 結束</span><span class="sxs-lookup"><span data-stu-id="611d0-122">\*END</span></span>  
  
     <span data-ttu-id="611d0-123">start_event:SNL001:subsystem FileactStub 已啟動</span><span class="sxs-lookup"><span data-stu-id="611d0-123">start_event:SNL001:subsystem FileactStub is up</span></span>  
  
     <span data-ttu-id="611d0-124">stop_event:SNL002:subsystem FileactStub 已關閉</span><span class="sxs-lookup"><span data-stu-id="611d0-124">stop_event:SNL002:subsystem FileactStub is down</span></span>  
  
     <span data-ttu-id="611d0-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="611d0-125">\#subsystem_name:User</span></span>  
  
     <span data-ttu-id="611d0-126">\## subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="611d0-126">\##subsystem_group:user</span></span>  
  
     <span data-ttu-id="611d0-127">\## subsystem_dependency:</span><span class="sxs-lookup"><span data-stu-id="611d0-127">\##subsystem_dependency:</span></span>  
  
     <span data-ttu-id="611d0-128">\#subsystem_nature： 重大</span><span class="sxs-lookup"><span data-stu-id="611d0-128">\#subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="611d0-129">\#subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="611d0-129">\#subsystem_start:</span></span>  
  
     <span data-ttu-id="611d0-130">\#\* 結束</span><span class="sxs-lookup"><span data-stu-id="611d0-130">\#\*END</span></span>  
  
     <span data-ttu-id="611d0-131">\#subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="611d0-131">\#subsystem_stop:</span></span>  
  
     <span data-ttu-id="611d0-132">\#\* 結束</span><span class="sxs-lookup"><span data-stu-id="611d0-132">\#\*END</span></span>  
  
     <span data-ttu-id="611d0-133">\#subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="611d0-133">\#subsystem_status:</span></span>  
  
     #<a name="end"></a><span data-ttu-id="611d0-134">\* 結束</span><span class="sxs-lookup"><span data-stu-id="611d0-134">\*END</span></span>  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="611d0-135">start_event:SNL001:subsystem 使用者已啟動</span><span class="sxs-lookup"><span data-stu-id="611d0-135">start_event:SNL001:subsystem User is up</span></span>  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="611d0-136">stop_event:SNL002:subsystem 使用者已關閉</span><span class="sxs-lookup"><span data-stu-id="611d0-136">stop_event:SNL002:subsystem User is down</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="611d0-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="611d0-137">See Also</span></span>  
 <span data-ttu-id="611d0-138">[FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="611d0-138">[FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="611d0-139">[步驟 1： 設定 FileAct 即時案例 SWIFT 配接器](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="611d0-139">[Step 1: Configure the SWIFT Adapter for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="611d0-140">[步驟 3： 建立傳送埠和接收埠以進行 FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="611d0-140">[Step 3: Create the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="611d0-141">步驟 4：測試 FileAct 即時端對端案例</span><span class="sxs-lookup"><span data-stu-id="611d0-141">Step 4: Test FileAct Real-Time End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)
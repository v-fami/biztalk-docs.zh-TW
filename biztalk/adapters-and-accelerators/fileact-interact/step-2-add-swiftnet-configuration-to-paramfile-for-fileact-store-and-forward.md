---
title: "步驟 2： 將 SWIFTNet 組態新增至為 FileAct 存放與轉寄實例 Paramfile |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088ab41f-8325-4330-b6f2-0164aa1911b1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 394e570ad9bd1c0e7532923dac9c2cc702f2f567
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="b8388-102">步驟 2： 加入為 FileAct 存放與轉寄實例 Paramfile SWIFTNet 組態</span><span class="sxs-lookup"><span data-stu-id="b8388-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="b8388-103">若要啟用以這些值來初始化接收者 SWIFTNet paramfile 中必須指定 SAG 中建立的伺服器訊息協力廠商。</span><span class="sxs-lookup"><span data-stu-id="b8388-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span>  
  
<span data-ttu-id="b8388-104">完成[步驟 1： 設定 SWIFT 配接器，為 FileAct 存放與轉寄實例](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md)開始此步驟之前。</span><span class="sxs-lookup"><span data-stu-id="b8388-104">Complete [Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md) before you begin this step.</span></span>
  
## <a name="add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="b8388-105">將 SWIFTNet 組態新增至 paramfile</span><span class="sxs-lookup"><span data-stu-id="b8388-105">Add SWIFTNet configuration to the paramfile</span></span>  
  
1.  <span data-ttu-id="b8388-106">在文字編輯器中，例如 [記事本] 開啟 paramfile。</span><span class="sxs-lookup"><span data-stu-id="b8388-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
2.  <span data-ttu-id="b8388-107">Paramfile 通常是位於： C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span><span class="sxs-lookup"><span data-stu-id="b8388-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span></span>  
  
3.  <span data-ttu-id="b8388-108">在 paramfile，請指定伺服器訊息夥伴名稱的反白顯示的變更：</span><span class="sxs-lookup"><span data-stu-id="b8388-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
    
     <span data-ttu-id="b8388-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="b8388-109">username:snlowner</span></span>  
  
     <span data-ttu-id="b8388-110">subsystem_name:FileactStub</span><span class="sxs-lookup"><span data-stu-id="b8388-110">subsystem_name:FileactStub</span></span>  
  
     <span data-ttu-id="b8388-111">\#subsystem_group:fileactsnf</span><span class="sxs-lookup"><span data-stu-id="b8388-111">\#subsystem_group:fileactsnf</span></span>  
  
     <span data-ttu-id="b8388-112">\#subsystem_dependency:Support 群集</span><span class="sxs-lookup"><span data-stu-id="b8388-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
     <span data-ttu-id="b8388-113">subsystem_nature： 重大</span><span class="sxs-lookup"><span data-stu-id="b8388-113">subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="b8388-114">subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="b8388-114">subsystem_start:</span></span>  
  
     <span data-ttu-id="b8388-115">**繁衍"snlreceiver-SagMessagePartner \<fileact SnF 的伺服器 MessagePartnerName\> -AdapterMode fileact"**</span><span class="sxs-lookup"><span data-stu-id="b8388-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for fileact SnF\> -AdapterMode fileact"**</span></span>  
  
     <span data-ttu-id="b8388-116">* 結束</span><span class="sxs-lookup"><span data-stu-id="b8388-116">*END</span></span>  
  
     <span data-ttu-id="b8388-117">subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="b8388-117">subsystem_stop:</span></span>  
  
     <span data-ttu-id="b8388-118">* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="b8388-118">*KILL9:snlreceiver</span></span>  
  
     <span data-ttu-id="b8388-119">* 結束</span><span class="sxs-lookup"><span data-stu-id="b8388-119">*END</span></span>  
  
     <span data-ttu-id="b8388-120">subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="b8388-120">subsystem_status:</span></span>  
  
     <span data-ttu-id="b8388-121">* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="b8388-121">*NB:1:snlreceiver</span></span>  
  
     <span data-ttu-id="b8388-122">* 結束</span><span class="sxs-lookup"><span data-stu-id="b8388-122">*END</span></span>  
  
     <span data-ttu-id="b8388-123">start_event:SNL001:subsystem FileactStubSnF 已啟動</span><span class="sxs-lookup"><span data-stu-id="b8388-123">start_event:SNL001:subsystem FileactStubSnF is up</span></span>  
  
     <span data-ttu-id="b8388-124">stop_event:SNL002:subsystem FileactStubSnF 已關閉</span><span class="sxs-lookup"><span data-stu-id="b8388-124">stop_event:SNL002:subsystem FileactStubSnF is down</span></span>  
  
     <span data-ttu-id="b8388-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="b8388-125">\#subsystem_name:User</span></span>  
  
     <span data-ttu-id="b8388-126">\## subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="b8388-126">\##subsystem_group:user</span></span>  
  
     <span data-ttu-id="b8388-127">\## subsystem_dependency:</span><span class="sxs-lookup"><span data-stu-id="b8388-127">\##subsystem_dependency:</span></span>  
  
     <span data-ttu-id="b8388-128">\#subsystem_nature： 重大</span><span class="sxs-lookup"><span data-stu-id="b8388-128">\#subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="b8388-129">\#subsystem_start:</span><span class="sxs-lookup"><span data-stu-id="b8388-129">\#subsystem_start:</span></span>  
  
     <span data-ttu-id="b8388-130">\#* 結束</span><span class="sxs-lookup"><span data-stu-id="b8388-130">\#*END</span></span>  
  
     <span data-ttu-id="b8388-131">\#subsystem_stop:</span><span class="sxs-lookup"><span data-stu-id="b8388-131">\#subsystem_stop:</span></span>  
  
     <span data-ttu-id="b8388-132">\#* 結束</span><span class="sxs-lookup"><span data-stu-id="b8388-132">\#*END</span></span>  
  
     <span data-ttu-id="b8388-133">\#subsystem_status:</span><span class="sxs-lookup"><span data-stu-id="b8388-133">\#subsystem_status:</span></span>  
  
     <span data-ttu-id="b8388-134">\#* 結束</span><span class="sxs-lookup"><span data-stu-id="b8388-134">\#*END</span></span>  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="b8388-135">start_event:SNL001:subsystem 使用者已啟動</span><span class="sxs-lookup"><span data-stu-id="b8388-135">start_event:SNL001:subsystem User is up</span></span>  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="b8388-136">stop_event:SNL002:subsystem 使用者已關閉</span><span class="sxs-lookup"><span data-stu-id="b8388-136">stop_event:SNL002:subsystem User is down</span></span>  
    
  
## <a name="complete-steps"></a><span data-ttu-id="b8388-137">完成步驟</span><span class="sxs-lookup"><span data-stu-id="b8388-137">Complete steps</span></span>
 <span data-ttu-id="b8388-138">[FileAct 存放與轉寄的案例](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="b8388-138">[FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="b8388-139">[步驟 1： 設定為 FileAct 存放與轉寄實例 SWIFT 的配接器](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="b8388-139">[Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="b8388-140">[步驟 3： 建立傳送埠和接收埠為 FileAct 存放與轉寄的實例](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="b8388-140">[Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span></span>  
 [<span data-ttu-id="b8388-141">步驟 4：測試 FileAct 儲存和轉寄端對端案例</span><span class="sxs-lookup"><span data-stu-id="b8388-141">Step 4: Test FileAct Store and Forward End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)
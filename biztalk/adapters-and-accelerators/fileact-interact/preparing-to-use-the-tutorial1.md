---
title: 準備使用 Tutorial1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4a792b2-8351-4ae8-9d7c-75420c00af03
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efedfeb184b8b0105b8622b6b3f068faffd6a906
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225206"
---
# <a name="preparing-to-use-the-tutorial"></a><span data-ttu-id="2bd24-102">準備使用本教學課程</span><span class="sxs-lookup"><span data-stu-id="2bd24-102">Preparing to Use the Tutorial</span></span>
<span data-ttu-id="2bd24-103">您必須執行下列使用 A4SWIFT 配接器的端對端教學課程之前。</span><span class="sxs-lookup"><span data-stu-id="2bd24-103">You must do the following before using the A4SWIFT adapter end-to-end tutorial.</span></span>  
  
1.  <span data-ttu-id="2bd24-104">此教學課程中，您將需要下列 SWIFT 成品：</span><span class="sxs-lookup"><span data-stu-id="2bd24-104">You will need the following SWIFT artifacts for this tutorial:</span></span>  
  
    -   <span data-ttu-id="2bd24-105">SWIFT 聯盟閘道 (SAG) 6.1</span><span class="sxs-lookup"><span data-stu-id="2bd24-105">SWIFT Alliance Gateway (SAG) 6.1</span></span>  
  
    -   <span data-ttu-id="2bd24-106">遠端存取 (RA) 6.1</span><span class="sxs-lookup"><span data-stu-id="2bd24-106">Remote Access (RA) 6.1</span></span>  
  
    -   <span data-ttu-id="2bd24-107">SWIFT WebStation 6.0</span><span class="sxs-lookup"><span data-stu-id="2bd24-107">SWIFT WebStation 6.0</span></span>  
  
    -   <span data-ttu-id="2bd24-108">SWIFTNet 連結 (SNL) 6.1</span><span class="sxs-lookup"><span data-stu-id="2bd24-108">SWIFTNet Link (SNL) 6.1</span></span>  
  
2.  <span data-ttu-id="2bd24-109">您必須設定 SAG: SAG，在建立 MessagePartners、 結束點和路由規則，並測試安裝介面卡的電腦上的 SAG 連線。</span><span class="sxs-lookup"><span data-stu-id="2bd24-109">You must configure SAG: create the MessagePartners, End Points, and Routing Rules in SAG, and test SAG connectivity on the computer where you install the adapters.</span></span> <span data-ttu-id="2bd24-110">如需資訊，請參閱 SAG 文件。</span><span class="sxs-lookup"><span data-stu-id="2bd24-110">For information, see the SAG documentation.</span></span>  
  
3.  <span data-ttu-id="2bd24-111">請遵循列於主題 「 如何以建立新主機 」 在 Microsoft BizTalk Server 說明中的指示 ([http://go.microsoft.com/fwlink/?LinkId = 100422](http://go.microsoft.com/fwlink/?LinkId=100422)) 若要建立一個 InterAct 配接器的內含式主控件名稱為*interacthost*，而另一個內含式主控件 FileAct 配接器，名為*fileacthost*。</span><span class="sxs-lookup"><span data-stu-id="2bd24-111">Follow the instructions listed in the topic “How to Create a New Host” in Microsoft BizTalk Server Help ([http://go.microsoft.com/fwlink/?LinkId=100422](http://go.microsoft.com/fwlink/?LinkId=100422)) to create one in-process Host for the InterAct adapter, named *interacthost*, and one in-process Host for the FileAct adapter, named *fileacthost*.</span></span> <span data-ttu-id="2bd24-112">建立配接器處理常式時，您將使用這些主機。</span><span class="sxs-lookup"><span data-stu-id="2bd24-112">You will use these hosts while creating handlers for the adapters.</span></span>  
  
4.  <span data-ttu-id="2bd24-113">教學課程中建立下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="2bd24-113">Create the following folders for the tutorial:</span></span>  
  
    -   <span data-ttu-id="2bd24-114">c:\SWIFTAdapterTutorial\Fileact\ClientLocation</span><span class="sxs-lookup"><span data-stu-id="2bd24-114">c:\SWIFTAdapterTutorial\Fileact\ClientLocation</span></span>  
  
    -   <span data-ttu-id="2bd24-115">c:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime</span><span class="sxs-lookup"><span data-stu-id="2bd24-115">c:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime</span></span>  
  
    -   <span data-ttu-id="2bd24-116">c:\SWIFTAdapterTutorial\Fileact\ResponseClient</span><span class="sxs-lookup"><span data-stu-id="2bd24-116">c:\SWIFTAdapterTutorial\Fileact\ResponseClient</span></span>  
  
    -   <span data-ttu-id="2bd24-117">c:\SWIFTAdapterTutorial\Fileact\ResponseServer</span><span class="sxs-lookup"><span data-stu-id="2bd24-117">c:\SWIFTAdapterTutorial\Fileact\ResponseServer</span></span>  
  
    -   <span data-ttu-id="2bd24-118">c:\SWIFTAdapterTutorial\Fileact\ServerLocation</span><span class="sxs-lookup"><span data-stu-id="2bd24-118">c:\SWIFTAdapterTutorial\Fileact\ServerLocation</span></span>  
  
    -   <span data-ttu-id="2bd24-119">c:\SWIFTAdapterTutorial\Fileact\StatusEvents</span><span class="sxs-lookup"><span data-stu-id="2bd24-119">c:\SWIFTAdapterTutorial\Fileact\StatusEvents</span></span>  
  
    -   <span data-ttu-id="2bd24-120">c:\SWIFTAdapterTutorial\Fileact\PullRequest</span><span class="sxs-lookup"><span data-stu-id="2bd24-120">c:\SWIFTAdapterTutorial\Fileact\PullRequest</span></span>  
  
    -   <span data-ttu-id="2bd24-121">c:\SWIFTAdapterTutorial\Fileact\PullResponse</span><span class="sxs-lookup"><span data-stu-id="2bd24-121">c:\SWIFTAdapterTutorial\Fileact\PullResponse</span></span>  
  
    -   <span data-ttu-id="2bd24-122">c:\SWIFTAdapterTutorial\Interact\HandleRequest</span><span class="sxs-lookup"><span data-stu-id="2bd24-122">c:\SWIFTAdapterTutorial\Interact\HandleRequest</span></span>  
  
    -   <span data-ttu-id="2bd24-123">c:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime</span><span class="sxs-lookup"><span data-stu-id="2bd24-123">c:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime</span></span>  
  
    -   <span data-ttu-id="2bd24-124">c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF</span><span class="sxs-lookup"><span data-stu-id="2bd24-124">c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF</span></span>  
  
    -   <span data-ttu-id="2bd24-125">c:\SWIFTAdapterTutorial\Interact\Response</span><span class="sxs-lookup"><span data-stu-id="2bd24-125">c:\SWIFTAdapterTutorial\Interact\Response</span></span>  
  
    -   <span data-ttu-id="2bd24-126">c:\SWIFTAdapterTutorial\Interact\PullRequest</span><span class="sxs-lookup"><span data-stu-id="2bd24-126">c:\SWIFTAdapterTutorial\Interact\PullRequest</span></span>  
  
    -   <span data-ttu-id="2bd24-127">c:\SWIFTAdapterTutorial\Interact\Pullresponse</span><span class="sxs-lookup"><span data-stu-id="2bd24-127">c:\SWIFTAdapterTutorial\Interact\Pullresponse</span></span>  
  
5.  <span data-ttu-id="2bd24-128">您必須擁有 SWIFT ITB 的連接或測試配接器的實際環境。</span><span class="sxs-lookup"><span data-stu-id="2bd24-128">You must have a connection to SWIFT ITB or live environment to test the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd24-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bd24-129">See Also</span></span>  
 <span data-ttu-id="2bd24-130">[BizTalk FileAct 和互動配接器的端對端教學課程](../../adapters-and-accelerators/fileact-interact/biztalk-fileact-and-interact-adapters-end-to-end-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="2bd24-130">[BizTalk FileAct and InterAct Adapters End-to-End Tutorial](../../adapters-and-accelerators/fileact-interact/biztalk-fileact-and-interact-adapters-end-to-end-tutorial.md) </span></span>  
 <span data-ttu-id="2bd24-131">[互動即時案例](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2bd24-131">[InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="2bd24-132">[儲存和轉送 (Push) 的案例進行互動](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2bd24-132">[InterAct Store and Forward (Push) Scenario](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span></span>  
 <span data-ttu-id="2bd24-133">[FileAct 即時案例](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2bd24-133">[FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="2bd24-134">FileAct 存放與轉寄的案例</span><span class="sxs-lookup"><span data-stu-id="2bd24-134">FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)
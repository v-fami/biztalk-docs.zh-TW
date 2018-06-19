---
title: 步驟 3： 測試批次中的批次出案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c487d39d-b2be-41d4-963e-d0ee9ba169fb
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d84c34eb3019f83ecd28f30425a93708affcecb2
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "25960796"
---
# <a name="step-3-test-the-batch-inbatch-out-scenario"></a><span data-ttu-id="db748-102">步驟 3： 測試中的批次/批次出案例</span><span class="sxs-lookup"><span data-stu-id="db748-102">Step 3: Test the Batch In/Batch Out Scenario</span></span>
<span data-ttu-id="db748-103">在此步驟中，您將測試批次中 / 批次出教學課程藉由卸除批次中的測試執行個體 / 批次訊息的資料夾。</span><span class="sxs-lookup"><span data-stu-id="db748-103">In this step, you test the Batch In/Batch Out tutorial by dropping a test instance of the batch in/batch out message into a folder.</span></span> <span data-ttu-id="db748-104">您設定的傳送埠會將訊息傳送、 接收埠會接收該和接收管線會處理它並拖放到目的資料夾。</span><span class="sxs-lookup"><span data-stu-id="db748-104">The send port that you set up will send the message, the receive port will receive it, and the receive pipeline will process it and drop it into the destination folder.</span></span>  
  
### <a name="to-test-the-batch-inbatch-out-scenario"></a><span data-ttu-id="db748-105">若要測試批次中 / 批次出案例</span><span class="sxs-lookup"><span data-stu-id="db748-105">To test the Batch In/Batch Out scenario</span></span>  
  
1.  <span data-ttu-id="db748-106">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至 **\<*磁碟機*\>: \Batching Tutorial\Instances**資料夾。</span><span class="sxs-lookup"><span data-stu-id="db748-106">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\Batching Tutorial\Instances** folder.</span></span>  
  
2.  <span data-ttu-id="db748-107">以滑鼠右鍵按一下**BatchInBatchOut.txt**，然後按一下 **複製**。</span><span class="sxs-lookup"><span data-stu-id="db748-107">Right click **BatchInBatchOut.txt**, and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="db748-108">瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_BTAHL7PickUp**資料夾。</span><span class="sxs-lookup"><span data-stu-id="db748-108">Browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7PickUp** folder.</span></span>  
  
4.  <span data-ttu-id="db748-109">以滑鼠右鍵按一下資料夾，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="db748-109">Right-click the folder, and then click **Paste**.</span></span>  
  
### <a name="to-verify-the-results-of-the-batch-inbatch-out-tutorial"></a><span data-ttu-id="db748-110">若要確認批次的結果中 / 批次出教學課程</span><span class="sxs-lookup"><span data-stu-id="db748-110">To verify the results of the Batch In/Batch Out Tutorial</span></span>  
  
-   <span data-ttu-id="db748-111">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_BTAHL7Drop**資料夾。</span><span class="sxs-lookup"><span data-stu-id="db748-111">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop** folder.</span></span> <span data-ttu-id="db748-112">短時間，您應該看到的批次訊息和通知處理的執行個體，出現在資料夾中。</span><span class="sxs-lookup"><span data-stu-id="db748-112">After a short period, you should see the processed instance of the batch message, and an acknowledgment, appear in the folder.</span></span> <span data-ttu-id="db748-113">如果它們沒有出現，請檢查[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="db748-113">If they do not appear, check the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer for an error message.</span></span> <span data-ttu-id="db748-114">每個檔案應該有不同的名稱形式\< *Guid*\>.txt。</span><span class="sxs-lookup"><span data-stu-id="db748-114">Each file should have a different name in the form \<*Guid*\>.txt.</span></span>  
  
     <span data-ttu-id="db748-115">第一個訊息應該是兩則訊息所組成的批次。</span><span class="sxs-lookup"><span data-stu-id="db748-115">The first message should be the batch consisting of two messages.</span></span> <span data-ttu-id="db748-116">BizTalk Accelerator for HL7 (BTAHL7) 具有循序包含這兩則訊息，在.txt 檔案中。</span><span class="sxs-lookup"><span data-stu-id="db748-116">BizTalk Accelerator for HL7 (BTAHL7) has included these two messages sequentially in the .txt file.</span></span> <span data-ttu-id="db748-117">這個批次不包含 FHS/FTS 和 BHS/BTS 標記。</span><span class="sxs-lookup"><span data-stu-id="db748-117">This batch does not contain FHS/FTS and BHS/BTS tags.</span></span> <span data-ttu-id="db748-118">在批次必須包含可能是所有 FHS/FTS 與 BHS/BTS 標記，或此批次訊息、 沒有 FHS/FTS 及無 BHS/BTS 標記等。</span><span class="sxs-lookup"><span data-stu-id="db748-118">A batch must contain either all FHS/FTS and BHS/BTS tags, or like this batch message, no FHS/FTS and no BHS/BTS tags.</span></span>  
  
    |<span data-ttu-id="db748-119">MSH.9</span><span class="sxs-lookup"><span data-stu-id="db748-119">MSH.9</span></span>|<span data-ttu-id="db748-120">MSH.10</span><span class="sxs-lookup"><span data-stu-id="db748-120">MSH.10</span></span>|<span data-ttu-id="db748-121">MSH.3</span><span class="sxs-lookup"><span data-stu-id="db748-121">MSH.3</span></span>|<span data-ttu-id="db748-122">MSH.5</span><span class="sxs-lookup"><span data-stu-id="db748-122">MSH.5</span></span>|  
    |-----------|------------|-----------|-----------|  
    |<span data-ttu-id="db748-123">ADT^A03</span><span class="sxs-lookup"><span data-stu-id="db748-123">ADT^A03</span></span>|<span data-ttu-id="db748-124">000001</span><span class="sxs-lookup"><span data-stu-id="db748-124">000001</span></span>|<span data-ttu-id="db748-125">Tutorial_BatchSource</span><span class="sxs-lookup"><span data-stu-id="db748-125">Tutorial_BatchSource</span></span>|<span data-ttu-id="db748-126">MESA_IS</span><span class="sxs-lookup"><span data-stu-id="db748-126">MESA_IS</span></span>|  
    |<span data-ttu-id="db748-127">ADT^A03</span><span class="sxs-lookup"><span data-stu-id="db748-127">ADT^A03</span></span>|<span data-ttu-id="db748-128">000002</span><span class="sxs-lookup"><span data-stu-id="db748-128">000002</span></span>|<span data-ttu-id="db748-129">Tutorial_BatchSource</span><span class="sxs-lookup"><span data-stu-id="db748-129">Tutorial_BatchSource</span></span>|<span data-ttu-id="db748-130">MESA_IS</span><span class="sxs-lookup"><span data-stu-id="db748-130">MESA_IS</span></span>|  
  
     <span data-ttu-id="db748-131">第二個訊息應傳送批次訊息，但是有下列欄位來回應單一應用程式通知：</span><span class="sxs-lookup"><span data-stu-id="db748-131">The second message should be a single application acknowledgment sent in response to the batch message, with the following fields:</span></span>  
  
    |<span data-ttu-id="db748-132">MSH.9</span><span class="sxs-lookup"><span data-stu-id="db748-132">MSH.9</span></span>|<span data-ttu-id="db748-133">MSH.3</span><span class="sxs-lookup"><span data-stu-id="db748-133">MSH.3</span></span>|<span data-ttu-id="db748-134">MSH.5</span><span class="sxs-lookup"><span data-stu-id="db748-134">MSH.5</span></span>|<span data-ttu-id="db748-135">MSA.1</span><span class="sxs-lookup"><span data-stu-id="db748-135">MSA.1</span></span>|<span data-ttu-id="db748-136">MSA.2</span><span class="sxs-lookup"><span data-stu-id="db748-136">MSA.2</span></span>|  
    |-----------|-----------|-----------|-----------|-----------|  
    |<span data-ttu-id="db748-137">ACK^A03^ACK</span><span class="sxs-lookup"><span data-stu-id="db748-137">ACK^A03^ACK</span></span>|<span data-ttu-id="db748-138">MESA_IS</span><span class="sxs-lookup"><span data-stu-id="db748-138">MESA_IS</span></span>|<span data-ttu-id="db748-139">Tutorial_BatchSource</span><span class="sxs-lookup"><span data-stu-id="db748-139">Tutorial_BatchSource</span></span>|<span data-ttu-id="db748-140">AA</span><span class="sxs-lookup"><span data-stu-id="db748-140">AA</span></span>|<span data-ttu-id="db748-141">000001</span><span class="sxs-lookup"><span data-stu-id="db748-141">000001</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db748-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db748-142">See Also</span></span>  
 <span data-ttu-id="db748-143">[第 1 部分： 分散的傳入批次的案例](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="db748-143">[Part 1: Fragmented Inbound Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md) </span></span>  
 [<span data-ttu-id="db748-144">第 3 部分：建立批次案例</span><span class="sxs-lookup"><span data-stu-id="db748-144">Part 3: Create-Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)
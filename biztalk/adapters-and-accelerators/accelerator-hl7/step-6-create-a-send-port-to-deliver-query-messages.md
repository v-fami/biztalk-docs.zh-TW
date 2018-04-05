---
title: 步驟 6： 建立傳送埠以傳送查詢訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, send ports
ms.assetid: a3cfa2aa-888d-4a82-9eb3-2e9cc29ee582
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43c373940d8ab1e847b66527d83ef24e952d84d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-create-a-send-port-to-deliver-query-messages"></a><span data-ttu-id="10eec-102">步驟 6： 建立傳送埠以傳送查詢訊息</span><span class="sxs-lookup"><span data-stu-id="10eec-102">Step 6: Create a Send Port to Deliver Query Messages</span></span>
<span data-ttu-id="10eec-103">在此步驟中，您建立傳送埠傳送傳入的查詢 (QRY ^ Q01 訊息) 醫院資訊系統 (HIS)。</span><span class="sxs-lookup"><span data-stu-id="10eec-103">In this step, you create the send port to deliver the incoming queries (QRY^Q01 messages) to the Hospital Information System (HIS).</span></span>  
  
### <a name="to-create-the-hissend-send-port"></a><span data-ttu-id="10eec-104">若要建立 HIS_Send 傳送埠</span><span class="sxs-lookup"><span data-stu-id="10eec-104">To create the HIS_Send send port</span></span>  
  
1.  <span data-ttu-id="10eec-105">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後選取**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="10eec-105">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then select **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="10eec-106">在 [傳送埠屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="10eec-106">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="10eec-107">使用</span><span class="sxs-lookup"><span data-stu-id="10eec-107">Use this</span></span>|<span data-ttu-id="10eec-108">動作</span><span class="sxs-lookup"><span data-stu-id="10eec-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="10eec-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="10eec-109">**Name**</span></span>|<span data-ttu-id="10eec-110">型別**HIS_Send**。</span><span class="sxs-lookup"><span data-stu-id="10eec-110">Type **HIS_Send**.</span></span>|  
    |<span data-ttu-id="10eec-111">**傳輸類型**</span><span class="sxs-lookup"><span data-stu-id="10eec-111">**Transport type**</span></span>|<span data-ttu-id="10eec-112">選取**MLLP**。</span><span class="sxs-lookup"><span data-stu-id="10eec-112">Select **MLLP**.</span></span>|  
    |<span data-ttu-id="10eec-113">**設定**</span><span class="sxs-lookup"><span data-stu-id="10eec-113">**Configure**</span></span>|<span data-ttu-id="10eec-114">按一下**設定**按鈕右邊的**類型**。</span><span class="sxs-lookup"><span data-stu-id="10eec-114">Click the **Configure** button to the right of **Type**.</span></span>|  
  
3.  <span data-ttu-id="10eec-115">在 MLLP 傳輸屬性 對話方塊中，輸入下列資訊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="10eec-115">In the MLLP Transport Properties dialog box, enter the following information and then click **OK**.</span></span>  
  
    |<span data-ttu-id="10eec-116">使用</span><span class="sxs-lookup"><span data-stu-id="10eec-116">Use this</span></span>|<span data-ttu-id="10eec-117">動作</span><span class="sxs-lookup"><span data-stu-id="10eec-117">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="10eec-118">**連接名稱**</span><span class="sxs-lookup"><span data-stu-id="10eec-118">**Connection Name**</span></span>|<span data-ttu-id="10eec-119">型別**HIS_SendMLLP**。</span><span class="sxs-lookup"><span data-stu-id="10eec-119">Type **HIS_SendMLLP**.</span></span>|  
    |<span data-ttu-id="10eec-120">**Host**</span><span class="sxs-lookup"><span data-stu-id="10eec-120">**Host**</span></span>|<span data-ttu-id="10eec-121">型別**localhost**。</span><span class="sxs-lookup"><span data-stu-id="10eec-121">Type **localhost**.</span></span>|  
    |<span data-ttu-id="10eec-122">**[通訊埠]**</span><span class="sxs-lookup"><span data-stu-id="10eec-122">**Port**</span></span>|<span data-ttu-id="10eec-123">型別**24000**。</span><span class="sxs-lookup"><span data-stu-id="10eec-123">Type **24000**.</span></span>|  
  
4.  <span data-ttu-id="10eec-124">在 [傳送埠屬性] 對話方塊的**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="10eec-124">In the Send Port Properties dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
5.  <span data-ttu-id="10eec-125">在主控台樹狀目錄中，按一下**篩選**，然後執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="10eec-125">In the Console Tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="10eec-126">使用</span><span class="sxs-lookup"><span data-stu-id="10eec-126">Use this</span></span>|<span data-ttu-id="10eec-127">動作</span><span class="sxs-lookup"><span data-stu-id="10eec-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="10eec-128">**屬性**</span><span class="sxs-lookup"><span data-stu-id="10eec-128">**Property**</span></span>|<span data-ttu-id="10eec-129">如**屬性**，選取**BTS。MessageType**。</span><span class="sxs-lookup"><span data-stu-id="10eec-129">For **Property**, select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="10eec-130">**運算子**</span><span class="sxs-lookup"><span data-stu-id="10eec-130">**Operator**</span></span>|<span data-ttu-id="10eec-131">選取 **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="10eec-131">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="10eec-132">**值**</span><span class="sxs-lookup"><span data-stu-id="10eec-132">**Value**</span></span>|<span data-ttu-id="10eec-133">型別**http://microsoft.com/HealthCare/HL7/2X#QRY_Q01_24_GLO_DEF**。</span><span class="sxs-lookup"><span data-stu-id="10eec-133">Type **http://microsoft.com/HealthCare/HL7/2X#QRY_Q01_24_GLO_DEF**.</span></span>|  
    |<span data-ttu-id="10eec-134">**Group By**</span><span class="sxs-lookup"><span data-stu-id="10eec-134">**Group By**</span></span>|<span data-ttu-id="10eec-135">選取**AND**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="10eec-135">Select **AND** from the drop-down list.</span></span>|  
    |<span data-ttu-id="10eec-136">**屬性**</span><span class="sxs-lookup"><span data-stu-id="10eec-136">**Property**</span></span>|<span data-ttu-id="10eec-137">如**屬性**在第二行中，選取**BTAHL7Schemas.MSH5_1**。</span><span class="sxs-lookup"><span data-stu-id="10eec-137">For **Property** on the second line, select **BTAHL7Schemas.MSH5_1**.</span></span>|  
    |<span data-ttu-id="10eec-138">**運算子**</span><span class="sxs-lookup"><span data-stu-id="10eec-138">**Operator**</span></span>|<span data-ttu-id="10eec-139">選取 **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="10eec-139">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="10eec-140">**值**</span><span class="sxs-lookup"><span data-stu-id="10eec-140">**Value**</span></span>|<span data-ttu-id="10eec-141">型別**HIS**。</span><span class="sxs-lookup"><span data-stu-id="10eec-141">Type **HIS**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="10eec-142">第一個篩選條件可讓您指定傳送埠只選取符合 QRY 訊息 ^ Q01 步驟 3A 中建立的結構描述。</span><span class="sxs-lookup"><span data-stu-id="10eec-142">The first filter specifies that the send port only selects messages conforming to the QRY^Q01 schema you created in step 3A.</span></span> <span data-ttu-id="10eec-143">第二個篩選指定的目的[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會傳送這些訊息。</span><span class="sxs-lookup"><span data-stu-id="10eec-143">The second filter specifies the destination to which the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine sends these messages.</span></span>  
  
6.  <span data-ttu-id="10eec-144">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="10eec-144">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="10eec-145">在管理主控台中，選取**傳送埠**，以滑鼠右鍵按一下**HIS_Send**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="10eec-145">In the Administration console, select **Send Ports**, right-click **HIS_Send**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="10eec-146">若要繼續[步驟 7： 建立傳送埠以傳送回應訊息](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="10eec-146">Proceed to [Step 7: Create a Send Port to Deliver Response Messages](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md).</span></span>
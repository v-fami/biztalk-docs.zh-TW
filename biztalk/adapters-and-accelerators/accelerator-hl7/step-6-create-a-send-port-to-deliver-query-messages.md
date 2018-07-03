---
title: 步驟 6： 建立傳送埠以傳遞查詢訊息 |Microsoft Docs
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
ms.openlocfilehash: 24e65ec7bc4e04850907609fc6d1d63e6f166593
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004047"
---
# <a name="step-6-create-a-send-port-to-deliver-query-messages"></a><span data-ttu-id="64c1e-102">步驟 6： 建立傳送埠以傳遞查詢訊息</span><span class="sxs-lookup"><span data-stu-id="64c1e-102">Step 6: Create a Send Port to Deliver Query Messages</span></span>
<span data-ttu-id="64c1e-103">在此步驟中，您建立的傳送埠以傳遞傳入的查詢 (QRY ^ Q01 訊息) 醫院資訊系統 (HIS)。</span><span class="sxs-lookup"><span data-stu-id="64c1e-103">In this step, you create the send port to deliver the incoming queries (QRY^Q01 messages) to the Hospital Information System (HIS).</span></span>  

### <a name="to-create-the-hissend-send-port"></a><span data-ttu-id="64c1e-104">若要建立 HIS_Send 傳送埠</span><span class="sxs-lookup"><span data-stu-id="64c1e-104">To create the HIS_Send send port</span></span>  

1. <span data-ttu-id="64c1e-105">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後選取**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-105">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then select **Static One-way Send Port**.</span></span>  

2. <span data-ttu-id="64c1e-106">在 [傳送埠屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="64c1e-106">In the Send Port Properties dialog box, do the following:</span></span>  


   |      <span data-ttu-id="64c1e-107">使用</span><span class="sxs-lookup"><span data-stu-id="64c1e-107">Use this</span></span>      |                        <span data-ttu-id="64c1e-108">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="64c1e-108">To do this</span></span>                        |
   |--------------------|----------------------------------------------------------|
   |      <span data-ttu-id="64c1e-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="64c1e-109">**Name**</span></span>      |                    <span data-ttu-id="64c1e-110">型別**HIS_Send**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-110">Type **HIS_Send**.</span></span>                    |
   | <span data-ttu-id="64c1e-111">**傳輸類型**</span><span class="sxs-lookup"><span data-stu-id="64c1e-111">**Transport type**</span></span> |                     <span data-ttu-id="64c1e-112">選取  **MLLP**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-112">Select **MLLP**.</span></span>                     |
   |   <span data-ttu-id="64c1e-113">**設定**</span><span class="sxs-lookup"><span data-stu-id="64c1e-113">**Configure**</span></span>    | <span data-ttu-id="64c1e-114">按一下 **設定**右邊的按鈕**型別**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-114">Click the **Configure** button to the right of **Type**.</span></span> |


3. <span data-ttu-id="64c1e-115">在 MLLP 傳輸屬性 對話方塊中，輸入下列資訊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-115">In the MLLP Transport Properties dialog box, enter the following information and then click **OK**.</span></span>  


   |      <span data-ttu-id="64c1e-116">使用</span><span class="sxs-lookup"><span data-stu-id="64c1e-116">Use this</span></span>       |       <span data-ttu-id="64c1e-117">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="64c1e-117">To do this</span></span>       |
   |---------------------|------------------------|
   | <span data-ttu-id="64c1e-118">**連接名稱**</span><span class="sxs-lookup"><span data-stu-id="64c1e-118">**Connection Name**</span></span> | <span data-ttu-id="64c1e-119">型別**HIS_SendMLLP**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-119">Type **HIS_SendMLLP**.</span></span> |
   |      <span data-ttu-id="64c1e-120">**主控件**</span><span class="sxs-lookup"><span data-stu-id="64c1e-120">**Host**</span></span>       |  <span data-ttu-id="64c1e-121">型別**localhost**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-121">Type **localhost**.</span></span>   |
   |      <span data-ttu-id="64c1e-122">**通訊埠**</span><span class="sxs-lookup"><span data-stu-id="64c1e-122">**Port**</span></span>       |    <span data-ttu-id="64c1e-123">型別**24000**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-123">Type **24000**.</span></span>     |


4. <span data-ttu-id="64c1e-124">在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-124">In the Send Port Properties dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  

5. <span data-ttu-id="64c1e-125">在主控台樹狀目錄中，按一下**篩選**，然後執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="64c1e-125">In the Console Tree, click **Filters**, and then do the following:</span></span>  


   |   <span data-ttu-id="64c1e-126">使用</span><span class="sxs-lookup"><span data-stu-id="64c1e-126">Use this</span></span>   |                              <span data-ttu-id="64c1e-127">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="64c1e-127">To do this</span></span>                               |
   |--------------|-----------------------------------------------------------------------|
   | <span data-ttu-id="64c1e-128">**屬性**</span><span class="sxs-lookup"><span data-stu-id="64c1e-128">**Property**</span></span> |             <span data-ttu-id="64c1e-129">針對**屬性**，選取**BTS。MessageType**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-129">For **Property**, select **BTS.MessageType**.</span></span>             |
   | <span data-ttu-id="64c1e-130">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="64c1e-130">**Operator**</span></span> |                <span data-ttu-id="64c1e-131">選取  **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="64c1e-131">Select **==** from the drop-down list.</span></span>                 |
   |  <span data-ttu-id="64c1e-132">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="64c1e-132">**Value**</span></span>   | <span data-ttu-id="64c1e-133">型別**<http://microsoft.com/HealthCare/HL7/2X#QRY_Q01_24_GLO_DEF>**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-133">Type **<http://microsoft.com/HealthCare/HL7/2X#QRY_Q01_24_GLO_DEF>**.</span></span> |
   | <span data-ttu-id="64c1e-134">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="64c1e-134">**Group By**</span></span> |                <span data-ttu-id="64c1e-135">選取  **AND**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="64c1e-135">Select **AND** from the drop-down list.</span></span>                |
   | <span data-ttu-id="64c1e-136">**屬性**</span><span class="sxs-lookup"><span data-stu-id="64c1e-136">**Property**</span></span> | <span data-ttu-id="64c1e-137">針對**屬性**在第二行中，選取**BTAHL7Schemas.MSH5_1**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-137">For **Property** on the second line, select **BTAHL7Schemas.MSH5_1**.</span></span> |
   | <span data-ttu-id="64c1e-138">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="64c1e-138">**Operator**</span></span> |                <span data-ttu-id="64c1e-139">選取  **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="64c1e-139">Select **==** from the drop-down list.</span></span>                 |
   |  <span data-ttu-id="64c1e-140">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="64c1e-140">**Value**</span></span>   |                             <span data-ttu-id="64c1e-141">型別**HIS**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-141">Type **HIS**.</span></span>                             |

   > [!NOTE]
   >  <span data-ttu-id="64c1e-142">第一個篩選條件可讓您指定傳送埠只會選取符合 QRY 訊息 ^ Q01 您在步驟 3A 中建立的結構描述。</span><span class="sxs-lookup"><span data-stu-id="64c1e-142">The first filter specifies that the send port only selects messages conforming to the QRY^Q01 schema you created in step 3A.</span></span> <span data-ttu-id="64c1e-143">第二個篩選指定的目的地[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會傳送這些訊息。</span><span class="sxs-lookup"><span data-stu-id="64c1e-143">The second filter specifies the destination to which the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine sends these messages.</span></span>  

6. <span data-ttu-id="64c1e-144">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="64c1e-144">Click **OK**.</span></span>  

7. <span data-ttu-id="64c1e-145">在 管理主控台中，選取**傳送埠**，以滑鼠右鍵按一下**HIS_Send**，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="64c1e-145">In the Administration console, select **Send Ports**, right-click **HIS_Send**, and then click **Start**.</span></span>  

   <span data-ttu-id="64c1e-146">請繼續進行[步驟 7： 建立傳送埠以傳遞回應訊息](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="64c1e-146">Proceed to [Step 7: Create a Send Port to Deliver Response Messages](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md).</span></span>
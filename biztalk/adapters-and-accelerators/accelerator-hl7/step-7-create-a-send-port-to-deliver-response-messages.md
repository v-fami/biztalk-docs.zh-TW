---
title: 步驟 7： 建立傳送埠以傳遞回應訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, send ports
ms.assetid: 5edaefb6-72f2-4317-9477-f3a0d0027e0c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4139e07c5ca503a8cb58b1aa88fe8e602a92ee07
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987823"
---
# <a name="step-7-create-a-send-port-to-deliver-response-messages"></a><span data-ttu-id="e629d-102">步驟 7： 建立傳送埠以傳遞回應訊息</span><span class="sxs-lookup"><span data-stu-id="e629d-102">Step 7: Create a Send Port to Deliver Response Messages</span></span>
<span data-ttu-id="e629d-103">在此步驟中，您建立的傳送埠以傳遞查詢傳回的回應許可、 放電和傳輸 (ADT) 系統。</span><span class="sxs-lookup"><span data-stu-id="e629d-103">In this step, you create the send port to deliver the query responses back to the Admissions, Discharge, and Transfer (ADT) system.</span></span>  

### <a name="to-create-the-adtsend-send-port"></a><span data-ttu-id="e629d-104">若要建立 ADT_Send 傳送埠</span><span class="sxs-lookup"><span data-stu-id="e629d-104">To create the ADT_Send send port</span></span>  

1. <span data-ttu-id="e629d-105">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後選取**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="e629d-105">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then select **Static One-way Send Port**.</span></span>  

2. <span data-ttu-id="e629d-106">在 [傳送埠屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e629d-106">In the Send Port Properties dialog box, do the following:</span></span>  


   |      <span data-ttu-id="e629d-107">使用</span><span class="sxs-lookup"><span data-stu-id="e629d-107">Use this</span></span>      |                        <span data-ttu-id="e629d-108">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="e629d-108">To do this</span></span>                        |
   |--------------------|----------------------------------------------------------|
   |      <span data-ttu-id="e629d-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e629d-109">**Name**</span></span>      |                    <span data-ttu-id="e629d-110">型別**ADT_Send**。</span><span class="sxs-lookup"><span data-stu-id="e629d-110">Type **ADT_Send**.</span></span>                    |
   | <span data-ttu-id="e629d-111">**傳輸類型**</span><span class="sxs-lookup"><span data-stu-id="e629d-111">**Transport type**</span></span> |                     <span data-ttu-id="e629d-112">選取  **MLLP**。</span><span class="sxs-lookup"><span data-stu-id="e629d-112">Select **MLLP**.</span></span>                     |
   |   <span data-ttu-id="e629d-113">**設定**</span><span class="sxs-lookup"><span data-stu-id="e629d-113">**Configure**</span></span>    | <span data-ttu-id="e629d-114">按一下 **設定**右邊的按鈕**型別**。</span><span class="sxs-lookup"><span data-stu-id="e629d-114">Click the **Configure** button to the right of **Type**.</span></span> |


3. <span data-ttu-id="e629d-115">在 MLLP 傳輸屬性 對話方塊中，輸入下列資訊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e629d-115">In the MLLP Transport Properties dialog box, enter the following information, and then click **OK**.</span></span>  


   |      <span data-ttu-id="e629d-116">使用</span><span class="sxs-lookup"><span data-stu-id="e629d-116">Use this</span></span>       |       <span data-ttu-id="e629d-117">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="e629d-117">To do this</span></span>       |
   |---------------------|------------------------|
   | <span data-ttu-id="e629d-118">**連接名稱**</span><span class="sxs-lookup"><span data-stu-id="e629d-118">**Connection Name**</span></span> | <span data-ttu-id="e629d-119">型別**ADT_SendMLLP**。</span><span class="sxs-lookup"><span data-stu-id="e629d-119">Type **ADT_SendMLLP**.</span></span> |
   |      <span data-ttu-id="e629d-120">**主控件**</span><span class="sxs-lookup"><span data-stu-id="e629d-120">**Host**</span></span>       |  <span data-ttu-id="e629d-121">型別**localhost**。</span><span class="sxs-lookup"><span data-stu-id="e629d-121">Type **localhost**.</span></span>   |
   |      <span data-ttu-id="e629d-122">**通訊埠**</span><span class="sxs-lookup"><span data-stu-id="e629d-122">**Port**</span></span>       |    <span data-ttu-id="e629d-123">型別**25000**。</span><span class="sxs-lookup"><span data-stu-id="e629d-123">Type **25000**.</span></span>     |


4. <span data-ttu-id="e629d-124">在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="e629d-124">In the Send Port Properties dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  

5. <span data-ttu-id="e629d-125">在主控台樹狀目錄中，按一下**篩選**，然後執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="e629d-125">In the Console Tree, click **Filters**, and then do the following:</span></span>  


   |   <span data-ttu-id="e629d-126">使用</span><span class="sxs-lookup"><span data-stu-id="e629d-126">Use this</span></span>   |                                        <span data-ttu-id="e629d-127">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="e629d-127">To do this</span></span>                                        |
   |--------------|------------------------------------------------------------------------------------------|
   | <span data-ttu-id="e629d-128">**屬性**</span><span class="sxs-lookup"><span data-stu-id="e629d-128">**Property**</span></span> |                               <span data-ttu-id="e629d-129">選取**BTS。MessageType**。</span><span class="sxs-lookup"><span data-stu-id="e629d-129">Select **BTS.MessageType**.</span></span>                                |
   | <span data-ttu-id="e629d-130">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="e629d-130">**Operator**</span></span> |                          <span data-ttu-id="e629d-131">選取  **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e629d-131">Select **==** from the drop-down list.</span></span>                          |
   |  <span data-ttu-id="e629d-132">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="e629d-132">**Value**</span></span>   |          <span data-ttu-id="e629d-133">型別**<http://microsoft.com/HealthCare/HL7/2X#DSR_Q01_24_GLO_DEF>**。</span><span class="sxs-lookup"><span data-stu-id="e629d-133">Type **<http://microsoft.com/HealthCare/HL7/2X#DSR_Q01_24_GLO_DEF>**.</span></span>           |
   | <span data-ttu-id="e629d-134">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="e629d-134">**Group By**</span></span> |                         <span data-ttu-id="e629d-135">選取  **AND**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e629d-135">Select **AND** from the drop-down list.</span></span>                          |
   | <span data-ttu-id="e629d-136">**屬性**</span><span class="sxs-lookup"><span data-stu-id="e629d-136">**Property**</span></span> | <span data-ttu-id="e629d-137">在第一個屬性中，按一下空白的方塊，，然後按**BTAHL7Schemas.MSH5_1**。</span><span class="sxs-lookup"><span data-stu-id="e629d-137">Under the first property, click the blank box, and then select **BTAHL7Schemas.MSH5_1**.</span></span> |
   | <span data-ttu-id="e629d-138">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="e629d-138">**Operator**</span></span> |                          <span data-ttu-id="e629d-139">選取  **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e629d-139">Select **==** from the drop-down list.</span></span>                          |
   |  <span data-ttu-id="e629d-140">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="e629d-140">**Value**</span></span>   |                                      <span data-ttu-id="e629d-141">型別**ADT**。</span><span class="sxs-lookup"><span data-stu-id="e629d-141">Type **ADT**.</span></span>                                       |

   > [!NOTE]
   >  <span data-ttu-id="e629d-142">第一個篩選條件可讓您指定傳送埠只會選取符合 DSR 訊息 ^ Q01 您在步驟 3A 中建立的結構描述。</span><span class="sxs-lookup"><span data-stu-id="e629d-142">The first filter specifies that the send port only selects messages conforming to the DSR^Q01 schema you created in step 3A.</span></span> <span data-ttu-id="e629d-143">第二個篩選指定的目的地[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會傳送這些訊息。</span><span class="sxs-lookup"><span data-stu-id="e629d-143">The second filter specifies the destination to which the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine sends these messages.</span></span>  

6. <span data-ttu-id="e629d-144">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="e629d-144">Click **OK**.</span></span>  

7. <span data-ttu-id="e629d-145">在管理主控台中，按一下**傳送埠**，以滑鼠右鍵按一下**ADT_Send**，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="e629d-145">In the Administration Console, click **Send Ports**, right-click **ADT_Send**, and then click **Start**.</span></span>  

   <span data-ttu-id="e629d-146">請繼續進行[步驟 8： 設定合作對象資訊](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md)。</span><span class="sxs-lookup"><span data-stu-id="e629d-146">Proceed to [Step 8: Configure Party Information](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md).</span></span>
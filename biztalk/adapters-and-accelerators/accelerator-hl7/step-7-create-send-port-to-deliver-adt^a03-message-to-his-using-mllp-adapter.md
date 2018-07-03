---
title: 步驟 7： 建立傳送埠以傳遞 ^ 他使用 MLLP 配接器將 adt^a03 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- creating, send ports
- send ports, creating
ms.assetid: d9e7f281-3d25-4675-a13e-0e2057f5e69a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 540a8745da811e7f14ab6ac5c1909bffe057c5f7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006103"
---
# <a name="step-7-create-a-send-port-to-deliver-the-adta03-message-to-his-using-the-mllp-adapter"></a><span data-ttu-id="a946c-102">步驟 7： 建立傳送埠以傳遞 ^ 他使用 MLLP 配接器將 adt^a03 訊息</span><span class="sxs-lookup"><span data-stu-id="a946c-102">Step 7: Create a Send Port to Deliver the ADT^A03 Message to HIS Using the MLLP Adapter</span></span>
<span data-ttu-id="a946c-103">在此步驟中，您可以建立要傳送訊息至醫院資訊系統 (HIS) 使用 MLLP 配接器的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a946c-103">In this step, you create the send port to send the message to the Hospital Information System (HIS) using the MLLP adapter.</span></span>  

### <a name="to-create-the-tutorialmllpsend-send-port"></a><span data-ttu-id="a946c-104">若要建立 Tutorial_MllpSend 傳送埠</span><span class="sxs-lookup"><span data-stu-id="a946c-104">To create the Tutorial_MllpSend send port</span></span>  

1. <span data-ttu-id="a946c-105">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="a946c-105">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  

2. <span data-ttu-id="a946c-106">在傳送埠屬性 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a946c-106">In the Send Port Properties dialog box, do the following actions:</span></span>  


   |      <span data-ttu-id="a946c-107">使用</span><span class="sxs-lookup"><span data-stu-id="a946c-107">Use this</span></span>      |                                <span data-ttu-id="a946c-108">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="a946c-108">To do this</span></span>                                 |
   |--------------------|---------------------------------------------------------------------------|
   |      <span data-ttu-id="a946c-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="a946c-109">**Name**</span></span>      |                        <span data-ttu-id="a946c-110">型別**Tutorial_MllpSend**。</span><span class="sxs-lookup"><span data-stu-id="a946c-110">Type **Tutorial_MllpSend**.</span></span>                        |
   | <span data-ttu-id="a946c-111">**傳輸類型**</span><span class="sxs-lookup"><span data-stu-id="a946c-111">**Transport type**</span></span> |                 <span data-ttu-id="a946c-112">選取  **MLLP**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a946c-112">Select **MLLP** from the drop-down list.</span></span>                  |
   |   <span data-ttu-id="a946c-113">**設定**</span><span class="sxs-lookup"><span data-stu-id="a946c-113">**Configure**</span></span>    | <span data-ttu-id="a946c-114">按一下 [**設定**來開啟**MLLP 傳輸屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a946c-114">Click **Configure** to open the **MLLP Transport Properties** dialog box.</span></span> |


3. <span data-ttu-id="a946c-115">在 MLLP 傳輸屬性 對話方塊中，執行下列動作，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a946c-115">In the MLLP Transport Properties dialog box, do the following actions and then click **OK**.</span></span>  


   |      <span data-ttu-id="a946c-116">使用</span><span class="sxs-lookup"><span data-stu-id="a946c-116">Use this</span></span>       |     <span data-ttu-id="a946c-117">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="a946c-117">To do this</span></span>      |
   |---------------------|---------------------|
   | <span data-ttu-id="a946c-118">**連接名稱**</span><span class="sxs-lookup"><span data-stu-id="a946c-118">**Connection Name**</span></span> | <span data-ttu-id="a946c-119">型別**1WaySend**。</span><span class="sxs-lookup"><span data-stu-id="a946c-119">Type **1WaySend**.</span></span>  |
   |      <span data-ttu-id="a946c-120">**主控件**</span><span class="sxs-lookup"><span data-stu-id="a946c-120">**Host**</span></span>       | <span data-ttu-id="a946c-121">型別**localhost**。</span><span class="sxs-lookup"><span data-stu-id="a946c-121">Type **localhost**.</span></span> |
   |      <span data-ttu-id="a946c-122">**通訊埠**</span><span class="sxs-lookup"><span data-stu-id="a946c-122">**Port**</span></span>       |   <span data-ttu-id="a946c-123">型別**14000**。</span><span class="sxs-lookup"><span data-stu-id="a946c-123">Type **14000**.</span></span>   |


4. <span data-ttu-id="a946c-124">在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="a946c-124">In the Send Port Properties dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  

5. <span data-ttu-id="a946c-125">在左窗格中，選取**篩選**，然後執行下列操作：</span><span class="sxs-lookup"><span data-stu-id="a946c-125">In the left pane, select **Filters**, and then do the following:</span></span>  

   |<span data-ttu-id="a946c-126">使用</span><span class="sxs-lookup"><span data-stu-id="a946c-126">Use this</span></span>|<span data-ttu-id="a946c-127">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="a946c-127">To do this</span></span>|  
   |--------------|----------------|  
   |<span data-ttu-id="a946c-128">**屬性**</span><span class="sxs-lookup"><span data-stu-id="a946c-128">**Property**</span></span>|<span data-ttu-id="a946c-129">選取**BTS。ReceivePortName**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a946c-129">Select **BTS.ReceivePortName** from the drop-down list.</span></span>|  
   |<span data-ttu-id="a946c-130">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="a946c-130">**Operator**</span></span>|<span data-ttu-id="a946c-131">選取  **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a946c-131">Select **==** from the drop-down list.</span></span>|  
   |<span data-ttu-id="a946c-132">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="a946c-132">**Value**</span></span>|<span data-ttu-id="a946c-133">型別**Tutorial_1WayReceive**。</span><span class="sxs-lookup"><span data-stu-id="a946c-133">Type **Tutorial_1WayReceive**.</span></span>|  

   > [!NOTE]
   >  <span data-ttu-id="a946c-134">1WayReceive 有任何訊息中指定的連接埠會接聽連接埠。</span><span class="sxs-lookup"><span data-stu-id="a946c-134">The port will listen to the port specified in 1WayReceive for any messages.</span></span>  

6. <span data-ttu-id="a946c-135">按一下 **套用**，然後按一下  **確定。**</span><span class="sxs-lookup"><span data-stu-id="a946c-135">Click **Apply**, and then click **OK.**</span></span>  

7. <span data-ttu-id="a946c-136">在管理主控台中，按一下**傳送埠**，以滑鼠右鍵按一下**Tutorial_MllpSend**，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="a946c-136">In the Administration Console, click **Send Ports**, right-click **Tutorial_MllpSend**, and then click **Start**.</span></span>  

   <span data-ttu-id="a946c-137">請繼續進行[步驟 8： 設定合作對象資訊](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md)。</span><span class="sxs-lookup"><span data-stu-id="a946c-137">Proceed to [Step 8: Configure Party Information](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md).</span></span>
---
title: 建立傳送至 SWIFT 的 FRR 傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
- FRR, creating send ports
ms.assetid: 1ad766db-d1da-437a-a520-a3b04f0695c4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1583072986eba20b5a0202e6973a5c08095aab01
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972319"
---
# <a name="creating-the-frr-send-port-for-sending-to-swift"></a><span data-ttu-id="6a6b5-102">建立傳送至 SWIFT 的 FRR 傳送埠</span><span class="sxs-lookup"><span data-stu-id="6a6b5-102">Creating the FRR Send Port for Sending to SWIFT</span></span>
<span data-ttu-id="6a6b5-103">若要執行 FIN 回應對帳，您必須建立傳送埠傳送訊息，以從[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]SWIFT 網路。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-103">To perform FIN Response Reconciliation, you need to create a send port that sends a message from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to the SWIFT Network.</span></span>  

 <span data-ttu-id="6a6b5-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="6a6b5-104">**Summary**</span></span>  

 <span data-ttu-id="6a6b5-105">建立傳送埠的下列屬性和元件：</span><span class="sxs-lookup"><span data-stu-id="6a6b5-105">Create a send port with the following properties and components:</span></span>  


|     <span data-ttu-id="6a6b5-106">屬性/元件</span><span class="sxs-lookup"><span data-stu-id="6a6b5-106">Property/Component</span></span>      |                                                               <span data-ttu-id="6a6b5-107">設定</span><span class="sxs-lookup"><span data-stu-id="6a6b5-107">Setting</span></span>                                                                |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
|          <span data-ttu-id="6a6b5-108">傳送埠</span><span class="sxs-lookup"><span data-stu-id="6a6b5-108">Send port</span></span>          |                                                         <span data-ttu-id="6a6b5-109">靜態單向連接埠</span><span class="sxs-lookup"><span data-stu-id="6a6b5-109">Static one-way port</span></span>                                                          |
|       <span data-ttu-id="6a6b5-110">傳輸類型</span><span class="sxs-lookup"><span data-stu-id="6a6b5-110">Transport type</span></span>        |                                                               <span data-ttu-id="6a6b5-111">MQSeries</span><span class="sxs-lookup"><span data-stu-id="6a6b5-111">MQSeries</span></span>                                                               |
| <span data-ttu-id="6a6b5-112">佇列定義 (MQSeries)</span><span class="sxs-lookup"><span data-stu-id="6a6b5-112">Queue Definition (MQSeries)</span></span> |                                                 <span data-ttu-id="6a6b5-113">MQSeries server 佇列管理員佇列</span><span class="sxs-lookup"><span data-stu-id="6a6b5-113">MQSeries server Queue manager Queue</span></span>                                                  |
|        <span data-ttu-id="6a6b5-114">傳送管線</span><span class="sxs-lookup"><span data-stu-id="6a6b5-114">Send pipeline</span></span>        | <span data-ttu-id="6a6b5-115">[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]建立 FRR 傳送管線</span><span class="sxs-lookup"><span data-stu-id="6a6b5-115">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] send pipeline that you created for FRR</span></span> |
|           <span data-ttu-id="6a6b5-116">篩選</span><span class="sxs-lookup"><span data-stu-id="6a6b5-116">Filters</span></span>           |                                                     <span data-ttu-id="6a6b5-117">下表所示</span><span class="sxs-lookup"><span data-stu-id="6a6b5-117">As shown in the table below</span></span>                                                      |

### <a name="to-add-a-custom-send-port-for-sending-to-swift"></a><span data-ttu-id="6a6b5-118">若要新增自訂的傳送埠傳送至 SWIFT</span><span class="sxs-lookup"><span data-stu-id="6a6b5-118">To add a custom send port for sending to SWIFT</span></span>  

1. <span data-ttu-id="6a6b5-119">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態一個 waySend 埠**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-119">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-waySend Port**.</span></span>  

2. <span data-ttu-id="6a6b5-120">在傳送埠屬性 對話方塊中，在**名稱**方塊中，輸入傳送埠，例如 FRRSWIFTSendPort 的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-120">In the Send Port Properties dialog box, in the **Name** box, type a name for the send port, such as FRRSWIFTSendPort.</span></span>  

3. <span data-ttu-id="6a6b5-121">針對**型別**，選取**MQSeries**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-121">For **Type**, select **MQSeries**.</span></span>  

4. <span data-ttu-id="6a6b5-122">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-122">Click **Configure**.</span></span>  

5. <span data-ttu-id="6a6b5-123">在 [MQSeries 傳輸屬性] 對話方塊中，按一下**佇列定義**，然後按一下省略符號 （...） 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-123">In the MQSeries Transport Properties dialog box, click **Queue Definition**, and then click the ellipsis () button.</span></span>  

6. <span data-ttu-id="6a6b5-124">在 [佇列定義] 對話方塊中，輸入 MQSeries server、 佇列管理員和佇列。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-124">In the Queue Definition dialog box, enter the MQSeries server, queue manager, and queue.</span></span> <span data-ttu-id="6a6b5-125">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-125">Click **OK**.</span></span>  

7. <span data-ttu-id="6a6b5-126">在 [MQSeries 傳輸屬性] 對話方塊中，確認內容會視需要。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-126">In the MQSeries Transport Properties dialog box, verify that the properties are as needed.</span></span> <span data-ttu-id="6a6b5-127">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-127">Click **OK**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="6a6b5-128">如需 MQSeries 傳輸屬性的詳細資訊，請參閱 MQSeries 文件。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-128">For more information about MQSeries transport properties, see the MQSeries documentation.</span></span>  

8. <span data-ttu-id="6a6b5-129">在傳送埠屬性 對話方塊中，如**傳送處理常式**，確認已選取 biztalkserverapplication。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-129">In the Send Port Properties dialog box, for **Send handler**, verify that BizTalkServerApplication is selected.</span></span>  

9. <span data-ttu-id="6a6b5-130">針對**傳送管線**，選取[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]建立 FRR 傳送管線。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-130">For **Send Pipeline**, select the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] send pipeline that you created for FRR.</span></span>  

10. <span data-ttu-id="6a6b5-131">按一下 **篩選器**左的窗格中，然後執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6a6b5-131">Click **Filters** in the left pane, and then do the following:</span></span>  


    |   <span data-ttu-id="6a6b5-132">使用</span><span class="sxs-lookup"><span data-stu-id="6a6b5-132">Use this</span></span>   |                            <span data-ttu-id="6a6b5-133">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="6a6b5-133">To do this</span></span>                             |
    |--------------|-------------------------------------------------------------------|
    | <span data-ttu-id="6a6b5-134">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6a6b5-134">**Property**</span></span> |  <span data-ttu-id="6a6b5-135">選取  **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-135">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_Failed**.</span></span>  |
    | <span data-ttu-id="6a6b5-136">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="6a6b5-136">**Operator**</span></span> |                          <span data-ttu-id="6a6b5-137">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-137">Select **==**.</span></span>                           |
    |  <span data-ttu-id="6a6b5-138">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="6a6b5-138">**Value**</span></span>   |                          <span data-ttu-id="6a6b5-139">型別**False**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-139">Type **False**.</span></span>                          |
    |  <span data-ttu-id="6a6b5-140">**群組**</span><span class="sxs-lookup"><span data-stu-id="6a6b5-140">**Group**</span></span>   |                          <span data-ttu-id="6a6b5-141">選取 **和**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-141">Select **And**.</span></span>                          |
    | <span data-ttu-id="6a6b5-142">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6a6b5-142">**Property**</span></span> | <span data-ttu-id="6a6b5-143">型別**Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SwiftBound**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-143">Type **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SwiftBound**.</span></span> |
    | <span data-ttu-id="6a6b5-144">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="6a6b5-144">**Operator**</span></span> |                          <span data-ttu-id="6a6b5-145">選取  **==**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-145">Select **==**.</span></span>                           |
    |  <span data-ttu-id="6a6b5-146">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="6a6b5-146">**Value**</span></span>   |                          <span data-ttu-id="6a6b5-147">型別 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-147">Type **True**.</span></span>                           |


11. <span data-ttu-id="6a6b5-148">按一下 **套用**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-148">Click **Apply**, and then click **OK**.</span></span>  

12. <span data-ttu-id="6a6b5-149">以滑鼠右鍵按一下傳送埠，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="6a6b5-149">Right-click the send port, and then click **Start**.</span></span>

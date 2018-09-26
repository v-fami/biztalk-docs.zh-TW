---
title: 步驟 6： 建立傳送埠以傳遞 ^ 給 RX 系統使用 File 配接器將 adt^a03 訊息 |Microsoft Docs
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
ms.assetid: 66c4b524-c8ff-43b5-9c44-6d7bc759ae2c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95a9200d4c03f11f2feca89042bfb57ba36de345
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004375"
---
# <a name="step-6-create-a-send-port-to-deliver-the-adta03-message-to-the-rx-system-using-the-file-adapter"></a><span data-ttu-id="d873c-102">步驟 6： 建立傳送埠以傳遞 ^ 給 RX 系統使用 File 配接器將 adt^a03 訊息</span><span class="sxs-lookup"><span data-stu-id="d873c-102">Step 6: Create a Send Port to Deliver the ADT^A03 Message to the RX System Using the File Adapter</span></span>
<span data-ttu-id="d873c-103">在此步驟中，您建立傳送埠的 Pharmacy 系統 (RX) 使用 File 配接器。</span><span class="sxs-lookup"><span data-stu-id="d873c-103">In this step, you create the send port for the Pharmacy System (RX) using the File adapter.</span></span>  

### <a name="to-create-the-tutorialsendmsgrx-send-port"></a><span data-ttu-id="d873c-104">若要建立 Tutorial_sendMsg_RX 傳送埠</span><span class="sxs-lookup"><span data-stu-id="d873c-104">To create the Tutorial_sendMsg_RX send port</span></span>  

1. <span data-ttu-id="d873c-105">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下**靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d873c-105">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  

2. <span data-ttu-id="d873c-106">在 **傳送埠屬性**對話方塊方塊中，執行下列動作，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d873c-106">In the **Send Port Properties** dialog box, do the following actions and then click **OK**.</span></span>  


   |      <span data-ttu-id="d873c-107">使用</span><span class="sxs-lookup"><span data-stu-id="d873c-107">Use this</span></span>      |                                <span data-ttu-id="d873c-108">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="d873c-108">To do this</span></span>                                 |
   |--------------------|---------------------------------------------------------------------------|
   |      <span data-ttu-id="d873c-109">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d873c-109">**Name**</span></span>      |                       <span data-ttu-id="d873c-110">型別**Tutorial_sendMsg_RX**。</span><span class="sxs-lookup"><span data-stu-id="d873c-110">Type **Tutorial_sendMsg_RX**.</span></span>                       |
   | <span data-ttu-id="d873c-111">**傳輸類型**</span><span class="sxs-lookup"><span data-stu-id="d873c-111">**Transport type**</span></span> |                 <span data-ttu-id="d873c-112">選取 **檔案**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d873c-112">Select **FILE** from the drop-down list.</span></span>                  |
   |   <span data-ttu-id="d873c-113">**設定**</span><span class="sxs-lookup"><span data-stu-id="d873c-113">**Configure**</span></span>    | <span data-ttu-id="d873c-114">按一下 [**設定**來開啟**File 傳輸屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d873c-114">Click **Configure** to open the **File Transport Properties** dialog box.</span></span> |


3. <span data-ttu-id="d873c-115">在 [FILE 傳輸屬性] 對話方塊中，執行下列動作，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d873c-115">In the FILE Transport Properties dialog box, do the following actions and then click **OK**.</span></span>  


   |        <span data-ttu-id="d873c-116">使用</span><span class="sxs-lookup"><span data-stu-id="d873c-116">Use this</span></span>        |                                                                     <span data-ttu-id="d873c-117">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="d873c-117">To do this</span></span>                                                                     |
   |------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
   | <span data-ttu-id="d873c-118">**目的地資料夾**</span><span class="sxs-lookup"><span data-stu-id="d873c-118">**Destination folder**</span></span> | <span data-ttu-id="d873c-119">瀏覽至**\<**<em>磁碟機</em>**:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_sendMsg_RX**。</span><span class="sxs-lookup"><span data-stu-id="d873c-119">Browse to **\<**<em>drive</em>**:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendMsg_RX**.</span></span> |
   |     <span data-ttu-id="d873c-120">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="d873c-120">**File name**</span></span>      |                                   <span data-ttu-id="d873c-121">型別 **%MessageID%.txt** （取代副檔名為.txt 的副檔名為.xml）。</span><span class="sxs-lookup"><span data-stu-id="d873c-121">Type **%MessageID%.txt** (replace the .xml extension with the .txt extension).</span></span>                                   |


4. <span data-ttu-id="d873c-122">在 [**傳送埠屬性**] 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="d873c-122">In the **Send Port Properties** dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  

5. <span data-ttu-id="d873c-123">在左窗格中，選取**篩選**，然後執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="d873c-123">In the left pane, select **Filters**, and then do the following actions.</span></span> <span data-ttu-id="d873c-124">按一下 **[確定]** 繼續進行。</span><span class="sxs-lookup"><span data-stu-id="d873c-124">Click **OK** to continue.</span></span>  


   |          <span data-ttu-id="d873c-125">使用</span><span class="sxs-lookup"><span data-stu-id="d873c-125">Use this</span></span>          |                                            <span data-ttu-id="d873c-126">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="d873c-126">To do this</span></span>                                            |
   |----------------------------|--------------------------------------------------------------------------------------------------|
   | <span data-ttu-id="d873c-127">**屬性**（第一次換行）</span><span class="sxs-lookup"><span data-stu-id="d873c-127">**Property** (first line)</span></span>  |                       <span data-ttu-id="d873c-128">選取**BTS。MessageType**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d873c-128">Select **BTS.MessageType** from the drop-down list.</span></span>                        |
   |        <span data-ttu-id="d873c-129">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="d873c-129">**Operator**</span></span>        |                              <span data-ttu-id="d873c-130">選取  **！ =** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d873c-130">Select **!=** from the drop-down list.</span></span>                              |
   |         <span data-ttu-id="d873c-131">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="d873c-131">**Value**</span></span>          |                <span data-ttu-id="d873c-132">型別**<http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF>**。</span><span class="sxs-lookup"><span data-stu-id="d873c-132">Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF>**.</span></span>                 |
   |        <span data-ttu-id="d873c-133">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="d873c-133">**Group By**</span></span>        |                              <span data-ttu-id="d873c-134">選取 **或**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d873c-134">Select **OR** from the drop-down list.</span></span>                              |
   | <span data-ttu-id="d873c-135">**屬性**（第二行）</span><span class="sxs-lookup"><span data-stu-id="d873c-135">**Property** (second line)</span></span> | <span data-ttu-id="d873c-136">按一下下方的欄位**屬性**，然後選取  **BTS。MessageType**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d873c-136">Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list.</span></span> |
   |        <span data-ttu-id="d873c-137">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="d873c-137">**Operator**</span></span>        |                              <span data-ttu-id="d873c-138">選取  **！ =** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d873c-138">Select **!=** from the drop-down list.</span></span>                              |
   |         <span data-ttu-id="d873c-139">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="d873c-139">**Value**</span></span>          |                <span data-ttu-id="d873c-140">型別 **<http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF>。**</span><span class="sxs-lookup"><span data-stu-id="d873c-140">Type **<http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF>.**</span></span>                 |
   |        <span data-ttu-id="d873c-141">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="d873c-141">**Group By**</span></span>        |                             <span data-ttu-id="d873c-142">選取  **AND**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d873c-142">Select **AND** from the drop-down list.</span></span>                              |
   | <span data-ttu-id="d873c-143">**屬性**（第三行）</span><span class="sxs-lookup"><span data-stu-id="d873c-143">**Property** (third line)</span></span>  |                                 <span data-ttu-id="d873c-144">選取  **BTAHL7Schemas.MSH3_1**。</span><span class="sxs-lookup"><span data-stu-id="d873c-144">Select **BTAHL7Schemas.MSH3_1**.</span></span>                                 |
   |        <span data-ttu-id="d873c-145">**[運算子]**</span><span class="sxs-lookup"><span data-stu-id="d873c-145">**Operator**</span></span>        |                              <span data-ttu-id="d873c-146">選取  **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d873c-146">Select **==** from the drop-down list.</span></span>                              |
   |         <span data-ttu-id="d873c-147">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="d873c-147">**Value**</span></span>          |                                   <span data-ttu-id="d873c-148">型別**Tutorial_ADTSystem**。</span><span class="sxs-lookup"><span data-stu-id="d873c-148">Type **Tutorial_ADTSystem**.</span></span>                                   |

   > [!NOTE]
   >  <span data-ttu-id="d873c-149">第一個篩選條件，表示醫院資訊系統 (HIS) 訂閱訊息，而不通知。</span><span class="sxs-lookup"><span data-stu-id="d873c-149">The first filter means that the Hospital Information System (HIS) is subscribing to a message, not an acknowledgment.</span></span> <span data-ttu-id="d873c-150">第二個篩選條件，表示他已訂閱的來源是許可出院和傳輸 (ADT) 系統的訊息。</span><span class="sxs-lookup"><span data-stu-id="d873c-150">The second filter means that HIS is subscribing to messages whose source is the Admissions Discharge and Transfer (ADT) System.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="d873c-151">BTAHL7 會捨棄訊息，在檔案放置位置\<*磁碟機*\>: Program Filessystem BizTalk <version> HL7SDKEnd 端對端 TutorialTutorial_sendMsg_RX 的加速器。</span><span class="sxs-lookup"><span data-stu-id="d873c-151">BTAHL7 drops the message at the file drop location \<*drive*\>:Program FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd-to-End TutorialTutorial_sendMsg_RX.</span></span>  

6. <span data-ttu-id="d873c-152">按一下 **套用**，然後按一下  **確定。**</span><span class="sxs-lookup"><span data-stu-id="d873c-152">Click **Apply**, and then click **OK.**</span></span>  

7. <span data-ttu-id="d873c-153">在管理主控台中，按一下**傳送埠**，以滑鼠右鍵按一下**Tutorial_sendMsg_RX**，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="d873c-153">In the Administration Console, click **Send Ports**, right-click **Tutorial_sendMsg_RX**, and then click **Start**.</span></span>  

   <span data-ttu-id="d873c-154">請繼續進行[步驟 7： 建立傳送埠以傳遞 ^ 他使用 MLLP 配接器將 adt^a03 訊息](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="d873c-154">Proceed to [Step 7: Create a Send Port to Deliver the ADT^A03 Message to HIS Using the MLLP Adapter](../../adapters-and-accelerators/accelerator-hl7/step-7-create-send-port-to-deliver-adt^a03-message-to-his-using-mllp-adapter.md).</span></span>
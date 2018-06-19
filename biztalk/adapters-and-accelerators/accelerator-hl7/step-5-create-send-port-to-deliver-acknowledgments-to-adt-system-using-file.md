---
title: 步驟 5： 建立傳送埠，以便將通知傳送到使用 File 配接器 ADT 系統 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- send ports, acknowledgements
- creating, send ports
- acknowledgements, send ports
- send ports, creating
ms.assetid: 565a2adf-fd86-46e3-8035-7e4748aefffc
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6e63590c8cc84a6c6c1a7e957900aa44cdcd61c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961836"
---
# <a name="step-5-create-a-send-port-to-deliver-acknowledgments-to-the-adt-system-using-the-file-adapter"></a><span data-ttu-id="1e11a-102">步驟 5： 建立傳送埠，以便將通知傳送到使用 File 配接器 ADT 系統</span><span class="sxs-lookup"><span data-stu-id="1e11a-102">Step 5: Create a Send Port to Deliver Acknowledgments to the ADT System Using the File Adapter</span></span>
<span data-ttu-id="1e11a-103">在此步驟中，您可以建立傳送埠，以產生使用 File 配接器的通知。</span><span class="sxs-lookup"><span data-stu-id="1e11a-103">In this step, you create the send port to generate acknowledgments using the File adapter.</span></span>  
  
### <a name="to-create-the-tutorialsendackadt-send-port"></a><span data-ttu-id="1e11a-104">若要建立 Tutorial_sendAck_ADT 傳送埠</span><span class="sxs-lookup"><span data-stu-id="1e11a-104">To create the Tutorial_sendAck_ADT send port</span></span>  
  
1.  <span data-ttu-id="1e11a-105">使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，建立\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端 Tutorial\Tutorial_sendAck_ADT 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e11a-105">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, create the \<*drive*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendAck_ADT folder.</span></span>  
  
2.  <span data-ttu-id="1e11a-106">在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="1e11a-106">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
3.  <span data-ttu-id="1e11a-107">在 [傳送埠屬性] 對話方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="1e11a-107">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="1e11a-108">使用</span><span class="sxs-lookup"><span data-stu-id="1e11a-108">Use this</span></span>|<span data-ttu-id="1e11a-109">動作</span><span class="sxs-lookup"><span data-stu-id="1e11a-109">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="1e11a-110">**名稱**</span><span class="sxs-lookup"><span data-stu-id="1e11a-110">**Name**</span></span>|<span data-ttu-id="1e11a-111">型別**Tutorial_sendAck_ADT**。</span><span class="sxs-lookup"><span data-stu-id="1e11a-111">Type **Tutorial_sendAck_ADT**.</span></span>|  
    |<span data-ttu-id="1e11a-112">**傳輸類型**</span><span class="sxs-lookup"><span data-stu-id="1e11a-112">**Transport type**</span></span>|<span data-ttu-id="1e11a-113">選取**檔案**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="1e11a-113">Select **FILE** from the drop-down list.</span></span>|  
    |<span data-ttu-id="1e11a-114">**設定**</span><span class="sxs-lookup"><span data-stu-id="1e11a-114">**Configure**</span></span>|<span data-ttu-id="1e11a-115">按一下**設定**開啟**File 傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1e11a-115">Click **Configure** to open the **File Transport Properties** dialog box.</span></span>|  
  
4.  <span data-ttu-id="1e11a-116">在 FILE 傳輸屬性 對話方塊中，執行下列動作，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="1e11a-116">In the FILE Transport Properties dialog box, do the following and then click **OK**.</span></span>  
  
    |<span data-ttu-id="1e11a-117">使用</span><span class="sxs-lookup"><span data-stu-id="1e11a-117">Use this</span></span>|<span data-ttu-id="1e11a-118">動作</span><span class="sxs-lookup"><span data-stu-id="1e11a-118">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="1e11a-119">**目的地資料夾**</span><span class="sxs-lookup"><span data-stu-id="1e11a-119">**Destination folder**</span></span>|<span data-ttu-id="1e11a-120">瀏覽至 **\<** *磁碟機***:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for HL7\SDK\End 端對端Tutorial\Tutorial_sendAck_ADT**。</span><span class="sxs-lookup"><span data-stu-id="1e11a-120">Browse to **\<***drive***:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendAck_ADT**.</span></span>|  
    |<span data-ttu-id="1e11a-121">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="1e11a-121">**File name**</span></span>|<span data-ttu-id="1e11a-122">型別 **%MessageID%.txt** （副檔名為.txt 取代.xml 副檔名）。</span><span class="sxs-lookup"><span data-stu-id="1e11a-122">Type **%MessageID%.txt** (replace the .xml extension with the .txt extension).</span></span>|  
  
5.  <span data-ttu-id="1e11a-123">在 [傳送埠屬性] 對話方塊的**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**。</span><span class="sxs-lookup"><span data-stu-id="1e11a-123">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
6.  <span data-ttu-id="1e11a-124">在左窗格中，按一下 **篩選**，然後執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="1e11a-124">In the left pane, click **Filters**, and then do the following:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1e11a-125">第一個篩選條件，表示您要訂閱的通知訊息。</span><span class="sxs-lookup"><span data-stu-id="1e11a-125">The first filter means that you are subscribing for the acknowledgment message.</span></span> <span data-ttu-id="1e11a-126">第二個篩選表示您要訂閱通知，並且用於 Tutorial_ADTSystem 「 發行者 」。</span><span class="sxs-lookup"><span data-stu-id="1e11a-126">The second filter means that you are subscribing to the acknowledgment that is destined for the publisher Tutorial_ADTSystem.</span></span>  
  
     <span data-ttu-id="1e11a-127">按一下**確定**當您準備好繼續進行。</span><span class="sxs-lookup"><span data-stu-id="1e11a-127">Click **OK** when you are ready to continue.</span></span>  
  
    |<span data-ttu-id="1e11a-128">使用</span><span class="sxs-lookup"><span data-stu-id="1e11a-128">Use this</span></span>|<span data-ttu-id="1e11a-129">動作</span><span class="sxs-lookup"><span data-stu-id="1e11a-129">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="1e11a-130">**屬性**</span><span class="sxs-lookup"><span data-stu-id="1e11a-130">**Property**</span></span>|<span data-ttu-id="1e11a-131">按一下下方的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="1e11a-131">Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list.</span></span>|  
    |<span data-ttu-id="1e11a-132">**運算子**</span><span class="sxs-lookup"><span data-stu-id="1e11a-132">**Operator**</span></span>|<span data-ttu-id="1e11a-133">選取 **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="1e11a-133">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="1e11a-134">**值**</span><span class="sxs-lookup"><span data-stu-id="1e11a-134">**Value**</span></span>|<span data-ttu-id="1e11a-135">型別**http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**。</span><span class="sxs-lookup"><span data-stu-id="1e11a-135">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_24_GLO_DEF**.</span></span>|  
    |<span data-ttu-id="1e11a-136">**Group By**</span><span class="sxs-lookup"><span data-stu-id="1e11a-136">**Group By**</span></span>|<span data-ttu-id="1e11a-137">選取**或**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="1e11a-137">Select **OR** from the drop-down list.</span></span>|  
    |<span data-ttu-id="1e11a-138">**屬性 （第二行）**</span><span class="sxs-lookup"><span data-stu-id="1e11a-138">**Property (second line)**</span></span>|<span data-ttu-id="1e11a-139">按一下下方的欄位**屬性**，然後選取**BTS。MessageType**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="1e11a-139">Click the field under **Property**, and then select **BTS.MessageType** from the drop-down list.</span></span>|  
    |<span data-ttu-id="1e11a-140">**運算子**</span><span class="sxs-lookup"><span data-stu-id="1e11a-140">**Operator**</span></span>|<span data-ttu-id="1e11a-141">選取 **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="1e11a-141">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="1e11a-142">**值**</span><span class="sxs-lookup"><span data-stu-id="1e11a-142">**Value**</span></span>|<span data-ttu-id="1e11a-143">型別**http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF。**</span><span class="sxs-lookup"><span data-stu-id="1e11a-143">Type **http://microsoft.com/HealthCare/HL7/2X#ACK_25_GLO_DEF.**</span></span>|  
    |<span data-ttu-id="1e11a-144">**Group By**</span><span class="sxs-lookup"><span data-stu-id="1e11a-144">**Group By**</span></span>|<span data-ttu-id="1e11a-145">選取**AND**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="1e11a-145">Select **AND** from the drop-down list.</span></span>|  
    |<span data-ttu-id="1e11a-146">**屬性**</span><span class="sxs-lookup"><span data-stu-id="1e11a-146">**Property**</span></span>|<span data-ttu-id="1e11a-147">在第一個屬性中，按一下空白的方塊，，然後選取**BTAHL7Schemas.MSH5_1**。</span><span class="sxs-lookup"><span data-stu-id="1e11a-147">Under the first property, click the blank box, and then select **BTAHL7Schemas.MSH5_1**.</span></span>|  
    |<span data-ttu-id="1e11a-148">**運算子**</span><span class="sxs-lookup"><span data-stu-id="1e11a-148">**Operator**</span></span>|<span data-ttu-id="1e11a-149">選取 **==** 從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="1e11a-149">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="1e11a-150">**值**</span><span class="sxs-lookup"><span data-stu-id="1e11a-150">**Value**</span></span>|<span data-ttu-id="1e11a-151">型別**Tutorial_ADTSystem**。</span><span class="sxs-lookup"><span data-stu-id="1e11a-151">Type **Tutorial_ADTSystem**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="1e11a-152">Tutorial_sendAck_ADT 傳送埠，BTAHL7 會卸除的通知在檔案放置位置\<*磁碟機*\>： 程式 FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd 端對端TutorialTutorial_sendAck_ADT。</span><span class="sxs-lookup"><span data-stu-id="1e11a-152">For the send port Tutorial_sendAck_ADT, BTAHL7 drops the acknowledgments at the file drop location \<*drive*\>:Program FilesMicrosoft BizTalk <version> Accelerator for HL7SDKEnd-to-End TutorialTutorial_sendAck_ADT.</span></span>  
  
7.  <span data-ttu-id="1e11a-153">按一下**套用**，然後按一下  **確定。**</span><span class="sxs-lookup"><span data-stu-id="1e11a-153">Click **Apply**, and then click **OK.**</span></span>  
  
8.  <span data-ttu-id="1e11a-154">在 管理主控台中，按一下 **傳送埠**，以滑鼠右鍵按一下**Tutorial_sendAck_ADT**，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="1e11a-154">In the Administration Console, click **Send Ports**, right-click **Tutorial_sendAck_ADT**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="1e11a-155">若要繼續[步驟 6： 建立傳送埠以傳送 ADT ^ A03 訊息使用 File 配接器之接收系統](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md)。</span><span class="sxs-lookup"><span data-stu-id="1e11a-155">Proceed to [Step 6: Create a Send Port to Deliver the ADT^A03 Message to the RX System Using the File Adapter](../../adapters-and-accelerators/accelerator-hl7/step-6-create-send-port-to-deliver-adt^a03-message-to-rx-system-using-file.md).</span></span>
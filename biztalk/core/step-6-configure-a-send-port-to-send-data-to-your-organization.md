---
title: "步驟 6： 設定傳送埠，以便將資料傳送至您的組織 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 796570ca-8178-4679-9213-d67a2a189bf9
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b513725024aec755515ccac998745220ee5dfa7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-configure-a-send-port-to-send-data-to-your-organization"></a><span data-ttu-id="07b9e-102">步驟 6： 設定傳送埠，以便將資料傳送至您的組織</span><span class="sxs-lookup"><span data-stu-id="07b9e-102">Step 6: Configure a Send Port to Send Data to Your Organization</span></span>
<span data-ttu-id="07b9e-103">![步驟 6 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-6of9.gif "Step_6of9")</span><span class="sxs-lookup"><span data-stu-id="07b9e-103">![Step 6 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-6of9.gif "Step_6of9")</span></span>  
  
 <span data-ttu-id="07b9e-104">在這個步驟中，您會設定傳送埠，以便將 850 訊息從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送到代表您組織的 OrderSystem 合作對象。</span><span class="sxs-lookup"><span data-stu-id="07b9e-104">In this step you configure a send port to send the 850 message from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the OrderSystem party that represents your organization.</span></span> <span data-ttu-id="07b9e-105">這個傳送埠會套用**Inbound4010850_to_OrderFile**對應，對應中指定的格式輸出訊息從輸入訊息的格式轉換成。</span><span class="sxs-lookup"><span data-stu-id="07b9e-105">This send port applies the **Inbound4010850_to_OrderFile** map, transforming the output message from the format of the input message to the format specified in the map.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="07b9e-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="07b9e-106">Prerequisites</span></span>  
 <span data-ttu-id="07b9e-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="07b9e-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-a-send-port-for-the-850-message"></a><span data-ttu-id="07b9e-108">若要指定 850 訊息的傳送埠</span><span class="sxs-lookup"><span data-stu-id="07b9e-108">To configure a send port for the 850 message</span></span>  
  
1.  <span data-ttu-id="07b9e-109">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**管線**，然後按一下 **重新整理**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click **Pipelines**, and then click **Refresh**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07b9e-110">您可能必須先重新整理管線，才可以為您將要建立的傳送埠選取 SendOrderFilePipeline。</span><span class="sxs-lookup"><span data-stu-id="07b9e-110">Refreshing the pipelines list may be necessary to be able to select the SendOrderFilePipeline for the send port that you will create.</span></span>  
  
2.  <span data-ttu-id="07b9e-111">以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-111">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
3.  <span data-ttu-id="07b9e-112">在**傳送埠屬性**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="07b9e-112">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="07b9e-113">使用</span><span class="sxs-lookup"><span data-stu-id="07b9e-113">Use this</span></span>|<span data-ttu-id="07b9e-114">動作</span><span class="sxs-lookup"><span data-stu-id="07b9e-114">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="07b9e-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="07b9e-115">**Name**</span></span>|<span data-ttu-id="07b9e-116">輸入`toOrderSystem`。</span><span class="sxs-lookup"><span data-stu-id="07b9e-116">Enter `toOrderSystem`.</span></span>|  
    |<span data-ttu-id="07b9e-117">**型別**</span><span class="sxs-lookup"><span data-stu-id="07b9e-117">**Type**</span></span>|<span data-ttu-id="07b9e-118">選取**檔案**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-118">Select **FILE**.</span></span>|  
    |<span data-ttu-id="07b9e-119">**設定**</span><span class="sxs-lookup"><span data-stu-id="07b9e-119">**Configure**</span></span>|<span data-ttu-id="07b9e-120">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-120">Click **Configure**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="07b9e-121">傳送埠的傳輸類型是 FILE，因為測試訊息是將傳送到資料夾的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="07b9e-121">The transport type of the send port is FILE because the test message is a flat file to be delivered into a folder.</span></span>  
  
4.  <span data-ttu-id="07b9e-122">在**FILE 傳輸屬性**對話方塊方塊中，執行下列動作，然後按一下**確定**:</span><span class="sxs-lookup"><span data-stu-id="07b9e-122">In the **FILE Transport Properties** dialog box, do the following and then click **OK**:</span></span>  
  
    |<span data-ttu-id="07b9e-123">使用</span><span class="sxs-lookup"><span data-stu-id="07b9e-123">Use this</span></span>|<span data-ttu-id="07b9e-124">動作</span><span class="sxs-lookup"><span data-stu-id="07b9e-124">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="07b9e-125">**目的地資料夾**</span><span class="sxs-lookup"><span data-stu-id="07b9e-125">**Destination folder**</span></span>|<span data-ttu-id="07b9e-126">按一下**瀏覽**，然後在**瀏覽資料夾**對話方塊中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\ 案例 A\toOrderSystem</span><span class="sxs-lookup"><span data-stu-id="07b9e-126">Click **Browse**, and in the **Browse for Folder** dialog box, move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\ Scenario A\toOrderSystem</span></span>|  
    |<span data-ttu-id="07b9e-127">**檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="07b9e-127">**File name**</span></span>|<span data-ttu-id="07b9e-128">輸入`%MessageID%.txt`，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-128">Enter `%MessageID%.txt`, and then click **OK**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="07b9e-129">值設定為**檔案名稱**屬性可確保，輸出檔會使用副檔名.txt。</span><span class="sxs-lookup"><span data-stu-id="07b9e-129">The value set for the **File name** property ensures that the output file will have a .txt extension.</span></span>  
  
5.  <span data-ttu-id="07b9e-130">在**傳送埠屬性**對話方塊中，針對**傳送管線**，選取**SendOrderFilePipeline**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-130">In the **Send Port Properties** dialog box, for **Send pipeline**, select **SendOrderFilePipeline**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07b9e-131">**SendOrderFilePipeline**傳送管線包括的一般檔案組合器來組合.txt 輸出檔案中，使用對應來源為輸入 850 訊息資料。</span><span class="sxs-lookup"><span data-stu-id="07b9e-131">The **SendOrderFilePipeline** send pipeline includes a flat-file assembler that assembles the .txt output file, using data mapped from the input 850 message.</span></span> <span data-ttu-id="07b9e-132">因為輸出檔案是 .txt 檔案，所以它不會出現在「交換/通知」狀態報告中。</span><span class="sxs-lookup"><span data-stu-id="07b9e-132">Since the output file is a .txt file, it will not show up in the Interchange/ACK status report.</span></span>  
  
6.  <span data-ttu-id="07b9e-133">在主控台樹狀目錄中，按一下**篩選**，然後執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="07b9e-133">In the console tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="07b9e-134">使用</span><span class="sxs-lookup"><span data-stu-id="07b9e-134">Use this</span></span>|<span data-ttu-id="07b9e-135">動作</span><span class="sxs-lookup"><span data-stu-id="07b9e-135">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="07b9e-136">**屬性**</span><span class="sxs-lookup"><span data-stu-id="07b9e-136">**Property**</span></span>|<span data-ttu-id="07b9e-137">選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-137">Select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="07b9e-138">**運算子**</span><span class="sxs-lookup"><span data-stu-id="07b9e-138">**Operator**</span></span>|<span data-ttu-id="07b9e-139">選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="07b9e-139">Select **==**.</span></span>|  
    |<span data-ttu-id="07b9e-140">**值**</span><span class="sxs-lookup"><span data-stu-id="07b9e-140">**Value**</span></span>|<span data-ttu-id="07b9e-141">輸入`ReceiveEDI_fromTHEM_A`。</span><span class="sxs-lookup"><span data-stu-id="07b9e-141">Enter `ReceiveEDI_fromTHEM_A`.</span></span>|  
    |<span data-ttu-id="07b9e-142">**群組依據**</span><span class="sxs-lookup"><span data-stu-id="07b9e-142">**Group by**</span></span>|<span data-ttu-id="07b9e-143">選取**和**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-143">Select **And**.</span></span>|  
    |<span data-ttu-id="07b9e-144">**屬性**</span><span class="sxs-lookup"><span data-stu-id="07b9e-144">**Property**</span></span>|<span data-ttu-id="07b9e-145">在下一行中，選取**BTS。MessageType**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-145">On the next line, select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="07b9e-146">**運算子**</span><span class="sxs-lookup"><span data-stu-id="07b9e-146">**Operator**</span></span>|<span data-ttu-id="07b9e-147">選取**！ =**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-147">Select **!=**.</span></span>|  
    |<span data-ttu-id="07b9e-148">**值**</span><span class="sxs-lookup"><span data-stu-id="07b9e-148">**Value**</span></span>|<span data-ttu-id="07b9e-149">輸入`http://schemas.microsoft.com/Edi/X12#X12_997_Root`。</span><span class="sxs-lookup"><span data-stu-id="07b9e-149">Enter `http://schemas.microsoft.com/Edi/X12#X12_997_Root`.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="07b9e-150">篩選器將確保此傳送埠將收取由 Receive_EDI_fromTHEM_A 接收位置所收到的訊息，而該傳送埠將不會收取 997 通知，而只收取 850 訊息。</span><span class="sxs-lookup"><span data-stu-id="07b9e-150">The filter ensures that the send port will pick up messages that were received by the Receive_EDI_fromTHEM_A receive location, and that the send port will not pick up 997 acknowledgments, but will pick only 850 messages.</span></span>  
  
7.  <span data-ttu-id="07b9e-151">在主控台樹狀目錄中，按一下**[輸出對應]**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-151">In the console tree, click **OutboundMaps**.</span></span> <span data-ttu-id="07b9e-152">在**輸出對應**窗格，請在**對應**資料行，第一個資料列上，選取**Inbound4010850_to_OrderFile**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-152">In the **Outbound Maps** pane, in the **Map** column, on the first row, select **Inbound4010850_to_OrderFile**.</span></span> <span data-ttu-id="07b9e-153">(中的項目**來源文件**資料行都將是 X12_00401_850。)</span><span class="sxs-lookup"><span data-stu-id="07b9e-153">(The entry in the **Source Document** column will be X12_00401_850.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07b9e-154">這個步驟可確保輸出訊息將會包含只對應來源為根據的輸入訊息資料的**Inbound4010850_to_OrderFile**對應。</span><span class="sxs-lookup"><span data-stu-id="07b9e-154">This step ensures that the output message will consist only of the data mapped from the input message according to the **Inbound4010850_to_OrderFile** map.</span></span>  
  
8.  <span data-ttu-id="07b9e-155">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-155">Click **OK**.</span></span>  
  
9. <span data-ttu-id="07b9e-156">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="07b9e-156">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **Send Ports**.</span></span> <span data-ttu-id="07b9e-157">以滑鼠右鍵按一下**toOrderSystem**，然後按一下 **啟動**登錄並啟動 連接埠。</span><span class="sxs-lookup"><span data-stu-id="07b9e-157">Right-click **toOrderSystem**, and then click **Start** to enlist and start the port.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="07b9e-158">後續步驟</span><span class="sxs-lookup"><span data-stu-id="07b9e-158">Next Steps</span></span>  
 <span data-ttu-id="07b9e-159">設定傳送埠 (**toTHEM_997**) 將 997 通知送回給 Fabrikam，如中所述[步驟 7： 設定傳送埠以傳送通知給您的交易夥伴](../core/step-7-configure-a-send-port-to-send-the-acknowledgment-to-trading-partner.md)。</span><span class="sxs-lookup"><span data-stu-id="07b9e-159">You configure the send port (**toTHEM_997**) to send the 997 acknowledgment back to Fabrikam, as described in [Step 7: Configure a Send Port to Send the Acknowledgment to Your Trading Partner](../core/step-7-configure-a-send-port-to-send-the-acknowledgment-to-trading-partner.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07b9e-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07b9e-160">See Also</span></span>  
 [<span data-ttu-id="07b9e-161">設定靜態傳送埠以傳送 EDI 交換和通知</span><span class="sxs-lookup"><span data-stu-id="07b9e-161">Configuring a Static Send Port to Send EDI Interchanges and Acknowledgments</span></span>](../core/configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments.md)
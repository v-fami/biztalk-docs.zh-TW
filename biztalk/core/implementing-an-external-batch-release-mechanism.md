---
title: 實作外部批次釋放機制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5633a448-cc29-4931-a3ad-206ae25c989b
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 298857d60662bbe2240a5cfb6cc797e4fda7abdb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010367"
---
# <a name="implementing-an-external-batch-release-mechanism"></a><span data-ttu-id="6030a-102">實作外部批次釋放機制</span><span class="sxs-lookup"><span data-stu-id="6030a-102">Implementing an External Batch Release Mechanism</span></span>
<span data-ttu-id="6030a-103">您可以使用外部釋放觸發程序來觸發釋放批次。</span><span class="sxs-lookup"><span data-stu-id="6030a-103">You can trigger the release of a batch using an external release trigger.</span></span> <span data-ttu-id="6030a-104">您可讓後端的企業營運系統應用程式在達到特定的臨界值時，自動觸發釋放。</span><span class="sxs-lookup"><span data-stu-id="6030a-104">The release could be automatically triggered by a back-end, line-of-business application upon reaching a certain threshold.</span></span> <span data-ttu-id="6030a-105">這項機制是除了會自動觸發批次釋放，由排程或交易集或字元計數，或手動觸發批次，依序按一下**覆寫**按鈕**批次設定**頁面的單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6030a-105">This mechanism is in addition to automatically triggering the batch release by a schedule or a count of transaction sets or characters, or manually triggering the batch by clicking the **Override** button in the **Batch Configuration** page of the one-way agreement tab.</span></span>  
  
 <span data-ttu-id="6030a-106">若要實作外部釋放觸發程序，您必須設定接收埠和位置來處理 OverrideControlMessage。</span><span class="sxs-lookup"><span data-stu-id="6030a-106">To implement an external release trigger, you need to set up a receive port and location to process the OverrideControlMessage.</span></span> <span data-ttu-id="6030a-107">接收位置必須使用 `Edi.BatchControlMessageRecvPipeline` 接收管線。</span><span class="sxs-lookup"><span data-stu-id="6030a-107">The receive location must use the `Edi.BatchControlMessageRecvPipeline` receive pipeline.</span></span> <span data-ttu-id="6030a-108">這是相同的管線，以供 BatchControlMessageRecvLoc 接收位置，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用來處理手動覆寫的訊息。</span><span class="sxs-lookup"><span data-stu-id="6030a-108">This is the same pipeline that is used by the BatchControlMessageRecvLoc receive location that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses to process manual override messages.</span></span> <span data-ttu-id="6030a-109">不過，BatchControlMessageRecvLoc 是 SQL 類型的接收位置，而您為外部釋放觸發程序設定的接收位置則可使用任何配接器類型。</span><span class="sxs-lookup"><span data-stu-id="6030a-109">However, BatchControlMessageRecvLoc is a SQL-type receive location, while the receive location that you set up for an external release trigger can use any adapter type.</span></span>  
  
 <span data-ttu-id="6030a-110">外部批次釋放是由 XML 控制訊息觸發的。</span><span class="sxs-lookup"><span data-stu-id="6030a-110">An external batch release is triggered by an XML control message.</span></span> <span data-ttu-id="6030a-111">若要觸發批次，後端應用程式需要將控制訊息路由傳送至接收位置。</span><span class="sxs-lookup"><span data-stu-id="6030a-111">To trigger the batch, the back-end application routes the control message to the receive location.</span></span> <span data-ttu-id="6030a-112">您可以修改控制訊息來啟動、覆寫或終止批次。</span><span class="sxs-lookup"><span data-stu-id="6030a-112">You can modify the control message to activate, override, or terminate the batch.</span></span> <span data-ttu-id="6030a-113">請參閱下面建立控制訊息的程序。</span><span class="sxs-lookup"><span data-stu-id="6030a-113">See the procedure below for creating the control message.</span></span>  
  
 <span data-ttu-id="6030a-114">若要啟用外部釋放觸發程序，您必須選取**外部釋放觸發程序**中的屬性**批次組態**頁面**協議屬性**對話方塊針對 X12 或 EDIFACT 的方塊。</span><span class="sxs-lookup"><span data-stu-id="6030a-114">To enable the external release trigger, you must select the **External release trigger** property in the **Batch Configuration** page of the **Agreement Properties** dialog box for either X12 or EDIFACT.</span></span> <span data-ttu-id="6030a-115">此屬性指示批次發行時必須有外部發行訊息。</span><span class="sxs-lookup"><span data-stu-id="6030a-115">This property indicates that an external release message is required for batch release.</span></span> <span data-ttu-id="6030a-116">**覆寫** 按鈕，**停止** 按鈕，並**啟用**範圍控制項仍然會有效如果**外部釋放觸發程序**屬性已選取。</span><span class="sxs-lookup"><span data-stu-id="6030a-116">The **Override** button, **Stop** button, and **Activation** range controls remain valid if the **External release trigger** property has been selected.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6030a-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="6030a-117">Prerequisites</span></span>  
 <span data-ttu-id="6030a-118">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="6030a-118">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-create-a-receive-location-for-the-external-batch-release-trigger-message"></a><span data-ttu-id="6030a-119">若要建立外部批次釋放觸發程序訊息的接收位置</span><span class="sxs-lookup"><span data-stu-id="6030a-119">To create a receive location for the external batch release trigger message</span></span>  
  
1. <span data-ttu-id="6030a-120">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，建立單向接收埠。</span><span class="sxs-lookup"><span data-stu-id="6030a-120">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, create a one-way receive port.</span></span> <span data-ttu-id="6030a-121">如需有關如何建立接收埠的指示，請參閱 <<c0> [ 如何建立接收埠](../core/how-to-create-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="6030a-121">For instructions on how to create a receive port, see [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).</span></span>  
  
2. <span data-ttu-id="6030a-122">在接收埠中建立單向接收位置。</span><span class="sxs-lookup"><span data-stu-id="6030a-122">Create a one-way receive location in the receive port.</span></span>  
  
3. <span data-ttu-id="6030a-123">選取傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="6030a-123">Select the transport type.</span></span> <span data-ttu-id="6030a-124">您可以為這個接收位置選取任何類型。</span><span class="sxs-lookup"><span data-stu-id="6030a-124">You can select any type for this receive location.</span></span> <span data-ttu-id="6030a-125">一般是選取 [FILE] 類型，然後輸入接收檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="6030a-125">A common solution is to select the FILE type, and enter a folder to receive the file.</span></span>  
  
4. <span data-ttu-id="6030a-126">若是接收管線，選取 `BatchControlMessageRecvPipeline`。</span><span class="sxs-lookup"><span data-stu-id="6030a-126">For Receive pipeline, select `BatchControlMessageRecvPipeline`.</span></span>  
  
5. <span data-ttu-id="6030a-127">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="6030a-127">Click **OK**.</span></span>  
  
### <a name="to-create-the-external-batch-release-trigger-message"></a><span data-ttu-id="6030a-128">若要建立外部批次釋放觸發程序訊息</span><span class="sxs-lookup"><span data-stu-id="6030a-128">To create the external batch release trigger message</span></span>  
  
1. <span data-ttu-id="6030a-129">在 [記事本] 中建立新檔案，命名時以 .xml 為副檔名。</span><span class="sxs-lookup"><span data-stu-id="6030a-129">In Notepad, create a new file and name it with an .xml extension.</span></span>  
  
2. <span data-ttu-id="6030a-130">將下列程式碼加入至此檔案中：</span><span class="sxs-lookup"><span data-stu-id="6030a-130">Add the following to the file:</span></span>  
  
   ```  
   <?xml version="1.0" encoding="utf-8"?>  
   <ControlMessage xmlns="http://SQLControlMessage.IssueSelect">  
     <PAM_Control xmlns="http://SQLControlMessage.IssueSelect">  
       <DestinationParty>[Party ID]</DestinationParty>  
       <EdiMessageType>[0 for X12\HIPAA|1 for Edifact]</EdiMessageType>  
       <ActionType>EdiBatchOverride</ActionType>  
       <ActionDateTime>[yyyy-mm-ddThh:mm:ss.sss]</ActionDateTime>  
       <UsedOnce>0</UsedOnce>  
       <BatchId>[Batch ID]</BatchId>  
       <BatchName>[Batch Name]</BatchName>  
       <DestinationPartyName>[Destination Party/Partner name]</DestinationPartyName>  
       <SenderPartyName>[Sender Party/Partner name]</SenderPartyName>  
       <AgreementName>[Agreement Name]</AgreementName>  
       <ReceiverPartyNameType>[Receiver Party/Partner name]</ReceiverPartyNameType>  
       <ToBeBatched>1</ToBeBatched>  
     </PAM_Control>  
   </ControlMessage>  
   ```  
  
    <span data-ttu-id="6030a-131">取代以上節錄的值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6030a-131">Replace the values in the above excerpt as follows:</span></span>  
  
   - <span data-ttu-id="6030a-132">指定的動作類型。</span><span class="sxs-lookup"><span data-stu-id="6030a-132">Specify the action type.</span></span> <span data-ttu-id="6030a-133">通常**ActionType**必須設為**EdiBatchOverride**覆寫在 「 合約 」 中完成的批次設定。</span><span class="sxs-lookup"><span data-stu-id="6030a-133">Typically, the **ActionType** must be set to **EdiBatchOverride** to override the batch settings done in the agreement.</span></span> <span data-ttu-id="6030a-134">您也可以將這設**EdiBatchTerminate**終止批次透過外部觸發程序。</span><span class="sxs-lookup"><span data-stu-id="6030a-134">You can also set this to **EdiBatchTerminate** to terminate the batch through an external trigger.</span></span>  
  
     > [!NOTE]
     >  <span data-ttu-id="6030a-135">Microsoft 建議您不要使用外部釋放觸發程序啟動批次。</span><span class="sxs-lookup"><span data-stu-id="6030a-135">Microsoft recommends you should not use external release trigger to activate a batch.</span></span> <span data-ttu-id="6030a-136">因此，您不應指定**ActionType**作為**EdiBatchActivate**。</span><span class="sxs-lookup"><span data-stu-id="6030a-136">So, you should not specify **ActionType** as **EdiBatchActivate**.</span></span>  
  
   - <span data-ttu-id="6030a-137">決定批次識別碼和批次名稱。</span><span class="sxs-lookup"><span data-stu-id="6030a-137">Determine the Batch ID and Batch Name.</span></span> <span data-ttu-id="6030a-138">若要這樣做，請開啟**協議屬性**對話方塊方塊，然後在單向協議 索引標籤中，按一下**批次組態**。</span><span class="sxs-lookup"><span data-stu-id="6030a-138">To do so, open the **Agreement Properties** dialog box, and on the one-way agreement tab, click **Batch Configuration**.</span></span> <span data-ttu-id="6030a-139">按一下索引標籤，以覆寫輸入的值之批次**批次名稱**並**批次識別碼**欄位到**BatchName**並**BatchID**節點的 「 控制 」 訊息。</span><span class="sxs-lookup"><span data-stu-id="6030a-139">Click the tab for the batch to be overridden and enter the value of **Batch name** and **Batch ID** fields into the **BatchName** and **BatchID** nodes of the control message.</span></span>  
  
   - <span data-ttu-id="6030a-140">指定目的地合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="6030a-140">Specify the destination party name.</span></span> <span data-ttu-id="6030a-141">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**合作對象** 節點，以及從**合作對象與商務設定檔**頁面上，取得批次接收合作對象/夥伴名稱交換。</span><span class="sxs-lookup"><span data-stu-id="6030a-141">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Parties** node, and from the **Parties and Business Profiles** page, get the name of the party/partner that will be receiving the batched interchanges.</span></span> <span data-ttu-id="6030a-142">輸入中的名稱**ReceiverPartyNameType**控制訊息的節點。</span><span class="sxs-lookup"><span data-stu-id="6030a-142">Enter the name in the **ReceiverPartyNameType** node of the control message.</span></span>  
  
   - <span data-ttu-id="6030a-143">指定傳送者合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="6030a-143">Specify the sender party name.</span></span> <span data-ttu-id="6030a-144">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**合作對象** 節點，以及從**合作對象與商務設定檔**頁面上，取得將用來傳送批次的交換的合作對象/夥伴名稱.</span><span class="sxs-lookup"><span data-stu-id="6030a-144">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Parties** node, and from the **Parties and Business Profiles** page, get the name of the party/partner that will be sending the batched interchanges.</span></span> <span data-ttu-id="6030a-145">輸入中的名稱**SenderPartyName**控制訊息的節點。</span><span class="sxs-lookup"><span data-stu-id="6030a-145">Enter the name in the **SenderPartyName** node of the control message.</span></span>  
  
   - <span data-ttu-id="6030a-146">指定合約名稱。</span><span class="sxs-lookup"><span data-stu-id="6030a-146">Specify the agreement name.</span></span> <span data-ttu-id="6030a-147">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象** 節點，並從**合作對象與商務設定檔**頁面上，於**協議** 區段中，以滑鼠右鍵按一下具有批次組態，必須要使用來覆寫 「 控制 」 訊息，然後按一下協議**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6030a-147">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Parties** node, and from the **Parties and Business Profiles** page, in the **Agreements** section, right-click the agreement that has the batch configuration that needs be to overridden using the control message, and then click **Properties**.</span></span> <span data-ttu-id="6030a-148">在 **協議屬性**對話方塊中，於**一般**索引標籤**一般屬性**頁面上，複製的值**名稱**欄位**協議參數**區段，然後將它貼在**AgreementName**控制訊息的節點。</span><span class="sxs-lookup"><span data-stu-id="6030a-148">In the **Agreement Properties** dialog box, in the **General** tab, on the **General Properties** page, copy the value from the **Name** field in the **Agreement Parameters** section, and paste it in the **AgreementName** node of the control message.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="6030a-149">您不需要指定目的地合作對象識別碼。</span><span class="sxs-lookup"><span data-stu-id="6030a-149">You do not need to specify a destination party ID.</span></span> <span data-ttu-id="6030a-150">在 「 控制 」 訊息僅為回溯相容性被必要項目。</span><span class="sxs-lookup"><span data-stu-id="6030a-150">The element is required in the control message only for backward compatibility.</span></span>  
  
3. <span data-ttu-id="6030a-151">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="6030a-151">Save the file.</span></span>  
  
### <a name="to-enable-the-external-release-trigger"></a><span data-ttu-id="6030a-152">若要啟用外部釋放觸發程序</span><span class="sxs-lookup"><span data-stu-id="6030a-152">To enable the external release trigger</span></span>  
  
1. <span data-ttu-id="6030a-153">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象** 節點，並從**合作對象與商務設定檔**頁面上，於**協議** 區段中，以滑鼠右鍵按一下具有批次組態，必須要使用來覆寫 「 控制 」 訊息，然後按一下協議**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6030a-153">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Parties** node, and from the **Parties and Business Profiles** page, in the **Agreements** section, right-click the agreement that has the batch configuration that needs be to overridden using the control message, and then click **Properties**.</span></span> <span data-ttu-id="6030a-154">在 **協議屬性** 對話方塊中，於單向協議 索引標籤中，按一下**批次組態**。</span><span class="sxs-lookup"><span data-stu-id="6030a-154">In the **Agreement Properties** dialog box, on the one-way agreement tab, click **Batch Configuration**.</span></span>  
  
2. <span data-ttu-id="6030a-155">在 **批次組態**頁面上，按一下您想要有外部釋放觸發程序，然後在批次的索引標籤**Release**區段中，選取**外部釋放觸發程序**.</span><span class="sxs-lookup"><span data-stu-id="6030a-155">In the **Batch Configuration** page, click the tab for the batch for which you want to have an external release trigger, and then under the **Release** section, select **External release trigger**.</span></span>  
  
3. <span data-ttu-id="6030a-156">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="6030a-156">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6030a-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6030a-157">See Also</span></span>  
 <span data-ttu-id="6030a-158">[設定 EDI 批次](../core/configuring-edi-batches.md) </span><span class="sxs-lookup"><span data-stu-id="6030a-158">[Configuring EDI Batches](../core/configuring-edi-batches.md) </span></span>  
 [<span data-ttu-id="6030a-159">如何建立接收位置</span><span class="sxs-lookup"><span data-stu-id="6030a-159">How to Create a Receive Location</span></span>](../core/how-to-create-a-receive-location.md)
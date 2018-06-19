---
title: 步驟 10： 設定 X12 和 AS2 交易夥伴協議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8fcdb3af-727a-4d20-9dcf-cf162e7d3398
caps.latest.revision: 46
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd0ce0ef6fef056c52e06fc1843024cbcf683c84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279198"
---
# <a name="step-10-configure-the-x12-and-as2-trading-partner-agreement"></a><span data-ttu-id="2f07a-102">步驟 10： 設定 X12 和 AS2 交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="2f07a-102">Step 10: Configure the X12 and AS2 Trading Partner Agreement</span></span>
<span data-ttu-id="2f07a-103">![步驟 10 的 11](../core/media/tut-step10-of-11.gif "Tut_Step10_of_11")</span><span class="sxs-lookup"><span data-stu-id="2f07a-103">![Step 10 of 11](../core/media/tut-step10-of-11.gif "Tut_Step10_of_11")</span></span>  
  
 <span data-ttu-id="2f07a-104">在本步驟中，您將設定要透過 HTTP 傳輸 EDIINT/AS2 編碼訊息的 X12 和 AS2 交易夥伴協議。</span><span class="sxs-lookup"><span data-stu-id="2f07a-104">In this step you set up X12 and AS2 trading partner agreements to transport an EDIINT/AS2-encoded message over HTTP.</span></span> <span data-ttu-id="2f07a-105">此 Fabrikam 合作對象會傳送 EDI 交換至 Contoso，再由 Contoso 將 997 通知和非同步 MDN 傳回 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="2f07a-105">This Fabrikam party sends the EDI interchange to Contoso, which returns the 997 acknowledgment and an asynchronous MDN to Fabrikam.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2f07a-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="2f07a-106">Prerequisites</span></span>  
 <span data-ttu-id="2f07a-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="2f07a-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-create-an-as2-agreement"></a><span data-ttu-id="2f07a-108">若要建立 AS2 協議</span><span class="sxs-lookup"><span data-stu-id="2f07a-108">To create an AS2 agreement</span></span>  
  
1.  <span data-ttu-id="2f07a-109">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft BizTalk Server**，然後按一下 **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-109">Click **Start**, click **All Programs**, click **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="2f07a-110">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**的主控台樹狀目錄中，然後在**合作對象與商務設定檔**頁面上，以滑鼠右鍵按一下 **[fabrikam_profile]**，指向 **新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-110">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click **Parties** in the console tree, and in the **Parties and Business Profiles** page, right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.</span></span>  
  
3.  <span data-ttu-id="2f07a-111">在**一般屬性** 頁面上，針對**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f07a-111">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  
  
4.  <span data-ttu-id="2f07a-112">從**通訊協定**下拉式清單中，選取**AS2**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-112">From the **Protocol** drop-down list, select **AS2**.</span></span>  
  
5.  <span data-ttu-id="2f07a-113">在**第二個夥伴** 區段中，從**名稱**下拉式清單中，選取**Contoso**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-113">In the **Second Partner** section, from the **Name** drop-down list, select **Contoso**.</span></span>  
  
6.  <span data-ttu-id="2f07a-114">在**第二個夥伴** 區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-114">In the **Second Partner** section, from the **Profile** drop-down list, select **Contoso_Profile**.</span></span>  
  
     <span data-ttu-id="2f07a-115">您會發現兩個新的索引標籤取得旁新增**一般** 索引標籤。每個索引標籤各用於設定一個單向 AS2 協議。</span><span class="sxs-lookup"><span data-stu-id="2f07a-115">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way AS2 agreement.</span></span>  
  
7.  <span data-ttu-id="2f07a-116">在**一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-116">In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**.</span></span>  
  
8.  <span data-ttu-id="2f07a-117">在上執行下列工作**Fabrikam-> Contoso**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2f07a-117">Perform the following tasks on the **Fabrikam->Contoso** tab.</span></span>  
  
    1.  <span data-ttu-id="2f07a-118">在**識別碼**頁面上，輸入的值**AS2-從**和**AS2-要**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-118">On the **Identifiers** page, enter values for **AS2-From** and **AS2-To**.</span></span> <span data-ttu-id="2f07a-119">如**AS2-從**，輸入`Fabrikam`。</span><span class="sxs-lookup"><span data-stu-id="2f07a-119">For **AS2-From**, enter `Fabrikam`.</span></span> <span data-ttu-id="2f07a-120">如**AS2-To**，輸入`Contoso`。</span><span class="sxs-lookup"><span data-stu-id="2f07a-120">For **AS2- To**, enter `Contoso`.</span></span>  
  
    2.  <span data-ttu-id="2f07a-121">在**驗證**頁面上，選取**對驗證與 MDN 使用協議設定，而非訊息標頭**核取方塊</span><span class="sxs-lookup"><span data-stu-id="2f07a-121">On the **Validation** page, select the **Use agreement settings for validation and MDN instead of message header** check box</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2f07a-122">設定此屬性可確保產生 MDN 時使用的是合作對象屬性，而不是使用已接收之 AS2 訊息的 AS2 標頭。</span><span class="sxs-lookup"><span data-stu-id="2f07a-122">Setting this property ensures that the party properties will be used when generating the MDN, rather than the AS2 headers of the received AS2 message.</span></span>  
  
    3.  <span data-ttu-id="2f07a-123">在**通知 (Mdn)** 頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2f07a-123">In the **Acknowledgements (MDNs)** page, do the following:</span></span>  
  
        1.  <span data-ttu-id="2f07a-124">選取**要求 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2f07a-124">Select the **Request MDN** check box.</span></span>  
  
        2.  <span data-ttu-id="2f07a-125">請確定**要求簽署的 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2f07a-125">Make sure the **Request Signed MDN** check box is cleared.</span></span>  
  
        3.  <span data-ttu-id="2f07a-126">選取**要求非同步 MDN**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2f07a-126">Select the **Request asynchronous MDN** check box.</span></span>  
  
        4.  <span data-ttu-id="2f07a-127">在**回條傳遞選項 (URL)** 文字方塊中，輸入`http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam`。</span><span class="sxs-lookup"><span data-stu-id="2f07a-127">In the **Receipt-Delivery-Option (URL)** text box, enter `http://localhost/Fabrikam/Default.aspx?Destination=_MDNToFabrikam`.</span></span>  
  
9. <span data-ttu-id="2f07a-128">在上執行下列工作**Contoso-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2f07a-128">Perform the following tasks on the **Contoso->Fabrikam** tab.</span></span>  
  
    1.  <span data-ttu-id="2f07a-129">在**識別碼**頁面上，輸入的值**AS2-從**和**AS2-要**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-129">On the **Identifiers** page, enter values for **AS2-From** and **AS2-To**.</span></span> <span data-ttu-id="2f07a-130">如**AS2-從**，輸入`Contoso`。</span><span class="sxs-lookup"><span data-stu-id="2f07a-130">For **AS2-From**, enter `Contoso`.</span></span> <span data-ttu-id="2f07a-131">如**AS2-To**，輸入`Fabrikam`。</span><span class="sxs-lookup"><span data-stu-id="2f07a-131">For **AS2- To**, enter `Fabrikam`.</span></span>  
  
    2.  <span data-ttu-id="2f07a-132">在**傳送埠**頁面**交換設定**區段的**傳送埠** 清單中，針對**名稱**選取**Send_Async_997**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-132">On the **Send Ports** page under the **Interchange Settings** section, in the **Send Ports** list, for **Name** select **Send_Async_997**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2f07a-133">必須輸入 Send_Async_997 傳送埠**傳送埠**清單以便[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以解析外寄 997 訊息的合作對象。</span><span class="sxs-lookup"><span data-stu-id="2f07a-133">The Send_Async_997 send port needs to be entered into the **Send Ports** list so that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can resolve the party for the outgoing 997 message.</span></span> <span data-ttu-id="2f07a-134">傳送管線會將傳送埠的名稱與合作對象屬性中的傳送埠進行比對。</span><span class="sxs-lookup"><span data-stu-id="2f07a-134">The send pipeline matches the name of the send port with the send port in the agreement properties.</span></span> <span data-ttu-id="2f07a-135">必須這麼做的原因是，這樣一來 [AS2-To] 屬性不會在訊息的內容中升級，而該屬性是傳送管線試圖解析合作對象時會最先比對的項目。</span><span class="sxs-lookup"><span data-stu-id="2f07a-135">This is necessary because in this case, the AS2-To property is not promoted in the context of the message, which is the first match that the send pipeline attempts to make to resolve the party.</span></span> <span data-ttu-id="2f07a-136">如需詳細資訊，請參閱[外寄 AS2 訊息的協議解析](../core/agreement-resolution-for-outgoing-as2-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="2f07a-136">For more information, see [Agreement Resolution for Outgoing AS2 Messages](../core/agreement-resolution-for-outgoing-as2-messages.md).</span></span>  
  
10. <span data-ttu-id="2f07a-137">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-137">Click **Apply**.</span></span>  
  
11. <span data-ttu-id="2f07a-138">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-138">Click **OK**.</span></span> <span data-ttu-id="2f07a-139">新增的協議會列在**協議**區段**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="2f07a-139">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="2f07a-140">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="2f07a-140">The newly added agreement is enabled by default.</span></span>  
  
### <a name="to-create-an-x12-agreement"></a><span data-ttu-id="2f07a-141">若要建立 X12 協議</span><span class="sxs-lookup"><span data-stu-id="2f07a-141">To create an X12 agreement</span></span>  
  
1.  <span data-ttu-id="2f07a-142">以滑鼠右鍵按一下**fabrikam_profile**，指向 **新增**，然後按一下**協議**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-142">Right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="2f07a-143">在**一般屬性** 頁面上，針對**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f07a-143">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  
  
3.  <span data-ttu-id="2f07a-144">從**通訊協定**下拉式清單中，選取**X12**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-144">From the **Protocol** drop-down list, select **X12**.</span></span>  
  
4.  <span data-ttu-id="2f07a-145">在**第二個夥伴** 區段中，從**名稱**下拉式清單中，選取**Contoso**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-145">In the **Second Partner** section, from the **Name** drop-down list, select **Contoso**.</span></span>  
  
5.  <span data-ttu-id="2f07a-146">在**第二個夥伴** 區段中，從**設定檔**下拉式清單中，選取**contoso_profile**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-146">In the **Second Partner** section, from the **Profile** drop-down list, select **Contoso_Profile**.</span></span>  
  
     <span data-ttu-id="2f07a-147">您會發現兩個新的索引標籤取得旁新增**一般** 索引標籤。每個索引標籤各用於設定一個單向 X12 協議。</span><span class="sxs-lookup"><span data-stu-id="2f07a-147">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way X12 agreement.</span></span>  
  
6.  <span data-ttu-id="2f07a-148">在**一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，然後選取**儲存報告的訊息內容**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-148">In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**, and then select **Store message payload for reporting**.</span></span>  
  
7.  <span data-ttu-id="2f07a-149">在上執行下列工作**Fabrikam-> Contoso**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2f07a-149">Perform the following tasks on the **Fabrikam->Contoso** tab.</span></span>  
  
    1.  <span data-ttu-id="2f07a-150">在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="2f07a-150">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span> <span data-ttu-id="2f07a-151">此教學課程中，設定**ISA5**至**ZZ**， **ISA6**至**7654321**， **ISA7**至**ZZ**，和**ISA8**至**1234567**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-151">For this tutorial, set **ISA5** to **ZZ**, **ISA6** to **7654321**, **ISA7** to **ZZ**, and **ISA8** to **1234567**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2f07a-152">對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。</span><span class="sxs-lookup"><span data-stu-id="2f07a-152">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires the qualifier and identifier fields for sender and receiver in order to perform agreement resolution.</span></span> <span data-ttu-id="2f07a-153">它會比對的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**交換標頭與協議屬性中。</span><span class="sxs-lookup"><span data-stu-id="2f07a-153">It will match the values of **ISA5**, **ISA6**, **ISA7**, and **ISA8** in the interchange header with those in the properties of an agreement.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2f07a-154">也比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 來解析協議。</span><span class="sxs-lookup"><span data-stu-id="2f07a-154"> will also resolve the agreement by matching the sender qualifier and identifier (without the receiver qualifier and identifier).</span></span> <span data-ttu-id="2f07a-155">若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。</span><span class="sxs-lookup"><span data-stu-id="2f07a-155">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement, it will use the fallback agreement properties.</span></span>  
  
    2.  <span data-ttu-id="2f07a-156">在**通知**頁面**交換設定**區段中，選取**預期 997**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2f07a-156">On the **Acknowledgements** page under the **Interchange Settings** section, select the **997 Expected** check box.</span></span>  
  
    3.  <span data-ttu-id="2f07a-157">在**驗證**頁面**交換設定**區段中，請確定**檢查重複的 ISA13**未選項。</span><span class="sxs-lookup"><span data-stu-id="2f07a-157">On the **Validation** page under the **Interchange Settings** section, make sure **Check for duplicate ISA13** option is unchecked.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2f07a-158">清除**檢查重複的 ISA13**屬性可讓您接收相同訊息的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="2f07a-158">Clearing the **Check for duplicate ISA13** property enables you to receive multiple instances of the same message.</span></span>  
  
    4.  <span data-ttu-id="2f07a-159">在**本機主機設定**頁面**交換設定**下**接收者的設定**，清除**通知的路由設定為上的傳送管線要求-回應接收埠**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-159">On the **Local Host Settings** page under the **Interchange Settings** section, under **Receiver’s Settings**, clear **Route ACK to send pipeline on request-response receive port**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2f07a-160">清除此屬性，讓您可透過個別傳送埠傳送 997 通知，而不是透過與雙向接收埠關聯的傳送埠傳送。</span><span class="sxs-lookup"><span data-stu-id="2f07a-160">Clearing this property enables you to send the 997 acknowledgment via a separate send port, rather than sending it over the send port associated with the two-way receive port.</span></span>  
  
8.  <span data-ttu-id="2f07a-161">在上執行下列工作**Contoso-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2f07a-161">Perform the following tasks on the **Contoso->Fabrikam** tab.</span></span>  
  
    1.  <span data-ttu-id="2f07a-162">在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="2f07a-162">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  <span data-ttu-id="2f07a-163">這個逐步解說中，設定**ISA5**至**ZZ**， **ISA6**至**1234567**， **ISA7**至**ZZ**，和**ISA8**至**7654321**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-163">For this walkthrough, set **ISA5** to **ZZ**, **ISA6** to **1234567**, **ISA7** to **ZZ**, and **ISA8** to **7654321**.</span></span>  
  
    2.  <span data-ttu-id="2f07a-164">在**字元集和分隔符號**頁面**交換設定** 區段中，如**尾碼**，選取**CR LF**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-164">On the **Charset and Separators** page under the **Interchange Settings** section, for **Suffix**, select **CR LF**.</span></span>  
  
    3.  <span data-ttu-id="2f07a-165">在**信封**頁面**交易集設定**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="2f07a-165">On the **Envelopes** page under the **Transaction Set Settings** section, do the following:</span></span>  
  
        |<span data-ttu-id="2f07a-166">使用</span><span class="sxs-lookup"><span data-stu-id="2f07a-166">Use this</span></span>|<span data-ttu-id="2f07a-167">動作</span><span class="sxs-lookup"><span data-stu-id="2f07a-167">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="2f07a-168">**預設值**</span><span class="sxs-lookup"><span data-stu-id="2f07a-168">**Default**</span></span>|<span data-ttu-id="2f07a-169">選取**預設**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-169">Select **Default**.</span></span> <span data-ttu-id="2f07a-170">**注意：** 當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **GS7**，和**GS8**可用即使值**交易類型**，**版本/版次**，和**目標命名空間**都不符合訊息。</span><span class="sxs-lookup"><span data-stu-id="2f07a-170">**Note:**  When you select this row as the default, the values for **GS1**, **GS2**, **GS3**, **GS7**, and **GS8** are used even if the values for **Transaction Type**, **Version/Release**, and **Target namespace** are not a match for the message.</span></span>|  
        |<span data-ttu-id="2f07a-171">**交易類型**</span><span class="sxs-lookup"><span data-stu-id="2f07a-171">**Transaction Type**</span></span>|<span data-ttu-id="2f07a-172">例如，選取您的測試訊息的訊息類型**864-文字訊息**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-172">Select the message type of your test message, for example, **864 – Text Message**.</span></span>|  
        |<span data-ttu-id="2f07a-173">**版本/版次**</span><span class="sxs-lookup"><span data-stu-id="2f07a-173">**Version/Release**</span></span>|<span data-ttu-id="2f07a-174">輸入**00401**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-174">Enter **00401**.</span></span>|  
        |<span data-ttu-id="2f07a-175">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="2f07a-175">**Target namespace**</span></span>|<span data-ttu-id="2f07a-176">選取**http://schemas.microsoft.com/BizTalk/EDI/X12/2006**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-176">Select **http://schemas.microsoft.com/BizTalk/EDI/X12/2006**.</span></span>|  
        |<span data-ttu-id="2f07a-177">**GS1**</span><span class="sxs-lookup"><span data-stu-id="2f07a-177">**GS1**</span></span>|<span data-ttu-id="2f07a-178">確認已選取測試訊息的訊息類型，例如**TX-簡訊 (864)**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-178">Verify that the message type of the test message is selected, for example, **TX - Text Message (864)**.</span></span>|  
        |<span data-ttu-id="2f07a-179">**GS2**</span><span class="sxs-lookup"><span data-stu-id="2f07a-179">**GS2**</span></span>|<span data-ttu-id="2f07a-180">輸入**01**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-180">Enter **01**.</span></span>|  
        |<span data-ttu-id="2f07a-181">**GS3**</span><span class="sxs-lookup"><span data-stu-id="2f07a-181">**GS3**</span></span>|<span data-ttu-id="2f07a-182">輸入**7654321**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-182">Enter **7654321**.</span></span>|  
        |<span data-ttu-id="2f07a-183">**GS4**</span><span class="sxs-lookup"><span data-stu-id="2f07a-183">**GS4**</span></span>|<span data-ttu-id="2f07a-184">選取您想要的日期格式。</span><span class="sxs-lookup"><span data-stu-id="2f07a-184">Select the date format that you want.</span></span> <span data-ttu-id="2f07a-185">選取**CCYYMMDD**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-185">Select **CCYYMMDD**.</span></span> <span data-ttu-id="2f07a-186">**注意：** 您必須在下拉式清單中選取值，不只是按一下欄位以顯示預設值。</span><span class="sxs-lookup"><span data-stu-id="2f07a-186">**Note:**  You have to select the value in the drop-down list, not just click in the field to display the default.</span></span> <span data-ttu-id="2f07a-187">如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。</span><span class="sxs-lookup"><span data-stu-id="2f07a-187">If you click in the field without selecting the value from the drop-down list, the value will not actually be selected.</span></span>|  
        |<span data-ttu-id="2f07a-188">**GS5**</span><span class="sxs-lookup"><span data-stu-id="2f07a-188">**GS5**</span></span>|<span data-ttu-id="2f07a-189">選擇您要的時間格式。</span><span class="sxs-lookup"><span data-stu-id="2f07a-189">Select the time format that you want.</span></span> <span data-ttu-id="2f07a-190">選取 **[hhmmssdd]**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-190">Select **HHMMSSdd**.</span></span>|  
        |<span data-ttu-id="2f07a-191">**GS7**</span><span class="sxs-lookup"><span data-stu-id="2f07a-191">**GS7**</span></span>|<span data-ttu-id="2f07a-192">選取**T-Transportation Data Coordinating Committee (TDCC)**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-192">Select **T - Transportation Data Coordinating Committee (TDCC)**.</span></span>|  
        |<span data-ttu-id="2f07a-193">**GS8**</span><span class="sxs-lookup"><span data-stu-id="2f07a-193">**GS8**</span></span>|<span data-ttu-id="2f07a-194">請確認已輸入 EDI 版本做**00401**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-194">Verify that the EDI version has been entered as **00401**.</span></span>|  
  
9. <span data-ttu-id="2f07a-195">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-195">Click **Apply**.</span></span>  
  
10. <span data-ttu-id="2f07a-196">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-196">Click **OK**.</span></span> <span data-ttu-id="2f07a-197">新增的協議會列在**協議**區段**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="2f07a-197">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="2f07a-198">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="2f07a-198">The newly added agreement is enabled by default.</span></span>  
  
11. <span data-ttu-id="2f07a-199">重新啟動 BizTalk 服務。</span><span class="sxs-lookup"><span data-stu-id="2f07a-199">Restart the BizTalk service.</span></span> <span data-ttu-id="2f07a-200">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台]**平台設定**，按一下 [**主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下 **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="2f07a-200">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under **Platform Settings**, click **Host Instances**, right-click **BizTalkServerApplication**, and then click **Restart**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2f07a-201">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2f07a-201">Next Steps</span></span>  
 <span data-ttu-id="2f07a-202">中所述，您會測試 AS2 方案，[步驟 11： 測試 AS2 方案](../core/step-11-test-the-as2-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="2f07a-202">You test the AS2 solution, as described in [Step 11: Test the AS2 Solution](../core/step-11-test-the-as2-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f07a-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f07a-203">See Also</span></span>  
 <span data-ttu-id="2f07a-204">[設定 AS2 屬性](../core/configuring-as2-properties.md) </span><span class="sxs-lookup"><span data-stu-id="2f07a-204">[Configuring AS2 Properties](../core/configuring-as2-properties.md) </span></span>  
 [<span data-ttu-id="2f07a-205">設定 EDI 屬性</span><span class="sxs-lookup"><span data-stu-id="2f07a-205">Configuring EDI Properties</span></span>](../core/configuring-edi-properties.md)
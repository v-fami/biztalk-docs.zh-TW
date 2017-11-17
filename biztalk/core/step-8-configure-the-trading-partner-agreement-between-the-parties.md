---
title: "步驟 8： 設定合作對象之間交易夥伴協議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f532f85-3f09-4b60-b7bb-817ee3c79899
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25e49bf5dcae7324fa3b68fe5080d094b4a2f603
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-configure-the-trading-partner-agreement-between-the-parties"></a><span data-ttu-id="eaa92-102">步驟 8： 設定合作對象之間交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="eaa92-102">Step 8: Configure the Trading Partner Agreement between the Parties</span></span>
<span data-ttu-id="eaa92-103">![步驟 8 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-8of9.gif "Step_8of9")</span><span class="sxs-lookup"><span data-stu-id="eaa92-103">![Step 8 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-8of9.gif "Step_8of9")</span></span>  
  
 <span data-ttu-id="eaa92-104">在此步驟中，您要設定 X12 交易夥伴協議定義交換 X12 參數兩個交易夥伴，OrderSystem 與 Fabrikam 之間的訊息。</span><span class="sxs-lookup"><span data-stu-id="eaa92-104">In this step, you configure an X12 trading partner agreement to define the parameters for exchanging X12 messages between the two trading partners, OrderSystem and Fabrikam.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eaa92-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="eaa92-105">Prerequisites</span></span>  
 <span data-ttu-id="eaa92-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="eaa92-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-an-agreement"></a><span data-ttu-id="eaa92-107">若要設定協議</span><span class="sxs-lookup"><span data-stu-id="eaa92-107">To configure an agreement</span></span>  
  
1.  <span data-ttu-id="eaa92-108">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-108">Click **Start**, click **All Programs**, click **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="eaa92-109">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**的主控台樹狀目錄中，然後在**合作對象與商務設定檔**頁面上，以滑鼠右鍵按一下**[fabrikam_profile]**，指向 **新增**，然後按一下 **協議**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click **Parties** in the console tree, and in the **Parties and Business Profiles** page, right-click **Fabrikam_Profile**, point to **New**, and then click **Agreement**.</span></span>  
  
3.  <span data-ttu-id="eaa92-110">在**一般屬性** 頁面上，針對**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="eaa92-110">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  
  
4.  <span data-ttu-id="eaa92-111">從**通訊協定**下拉式清單中，選取**X12**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-111">From the **Protocol** drop-down list, select **X12**.</span></span>  
  
5.  <span data-ttu-id="eaa92-112">在**第二個合作對象** 區段中，從**合作對象**下拉式清單中，選取**OrderSystem**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-112">In the **Second Party** section, from the **Party** drop-down list, select **OrderSystem**.</span></span>  
  
6.  <span data-ttu-id="eaa92-113">在**第二個合作對象** 區段中，從**商務**下拉式清單中，選取**ordersystem_profile**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-113">In the **Second Party** section, from the **Business** drop-down list, select **OrderSystem_Profile**.</span></span>  
  
     <span data-ttu-id="eaa92-114">您會發現兩個新的索引標籤取得旁新增**一般** 索引標籤。每個索引標籤各用於設定一個單向協議，而每個單向協議各代表一筆完整的訊息交易 (包含訊息傳輸與通知傳輸)。</span><span class="sxs-lookup"><span data-stu-id="eaa92-114">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way agreement and each one-way agreement represents one complete transaction of message (including message transfer and acknowledgement transfer).</span></span>  
  
7.  <span data-ttu-id="eaa92-115">在**一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，然後選取**儲存報告的訊息內容**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-115">In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**, and then select **Store message payload for reporting**.</span></span>  
  
8.  <span data-ttu-id="eaa92-116">在上執行下列工作**Fabrikam-> OrderSystem**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="eaa92-116">Perform the following tasks on the **Fabrikam->OrderSystem** tab.</span></span>  
  
    1.  <span data-ttu-id="eaa92-117">在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="eaa92-117">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  
  
        |<span data-ttu-id="eaa92-118">使用</span><span class="sxs-lookup"><span data-stu-id="eaa92-118">Use this</span></span>|<span data-ttu-id="eaa92-119">動作</span><span class="sxs-lookup"><span data-stu-id="eaa92-119">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="eaa92-120">**傳送者辨識符號 (ISA5)**</span><span class="sxs-lookup"><span data-stu-id="eaa92-120">**Sender qualifier (ISA5)**</span></span>|<span data-ttu-id="eaa92-121">選取**ZZ-使用者相互定義**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-121">Select **ZZ - Mutually Defined**.</span></span>|  
        |<span data-ttu-id="eaa92-122">**寄件者識別項 (ISA6)**</span><span class="sxs-lookup"><span data-stu-id="eaa92-122">**Sender identifier (ISA6)**</span></span>|<span data-ttu-id="eaa92-123">輸入**THEM**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-123">Enter **THEM**.</span></span>|  
        |<span data-ttu-id="eaa92-124">**接收者辨識符號 (ISA7)**</span><span class="sxs-lookup"><span data-stu-id="eaa92-124">**Receiver qualifier (ISA7)**</span></span>|<span data-ttu-id="eaa92-125">選取**ZZ-使用者相互定義**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-125">Select **ZZ - Mutually Defined**.</span></span>|  
        |<span data-ttu-id="eaa92-126">**接收者識別項 (ISA8)**</span><span class="sxs-lookup"><span data-stu-id="eaa92-126">**Receiver identifier (ISA8)**</span></span>|<span data-ttu-id="eaa92-127">輸入**美國**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-127">Enter **US**.</span></span>|  
  
        > [!NOTE]
        >  <span data-ttu-id="eaa92-128">對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。</span><span class="sxs-lookup"><span data-stu-id="eaa92-128">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires the qualifier and identifier fields for sender and receiver in order to perform agreement resolution.</span></span> <span data-ttu-id="eaa92-129">它會比對的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**交換標頭與協議屬性中。</span><span class="sxs-lookup"><span data-stu-id="eaa92-129">It will match the values of **ISA5**, **ISA6**, **ISA7**, and **ISA8** in the interchange header with those in the properties of an agreement.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="eaa92-130">也比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 來解析協議。</span><span class="sxs-lookup"><span data-stu-id="eaa92-130"> will also resolve the agreement by matching the sender qualifier and identifier (without the receiver qualifier and identifier).</span></span> <span data-ttu-id="eaa92-131">若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。</span><span class="sxs-lookup"><span data-stu-id="eaa92-131">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement, it will use the fallback agreement properties.</span></span>  
  
    2.  <span data-ttu-id="eaa92-132">在**通知**頁面的 **交換設定**區段中，按一下**預期 997**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-132">On the **Acknowledgements** page, under the **Interchange Settings** section, click **997 Expected**.</span></span> <span data-ttu-id="eaa92-133">若是選取這個核取方塊，則會提示接收管線在收到 850 交換時產生 997 通知。</span><span class="sxs-lookup"><span data-stu-id="eaa92-133">Selecting this check box prompts the receive pipeline to generate a 997 acknowledgment when it receives the 850 interchange..</span></span>  
  
    3.  <span data-ttu-id="eaa92-134">在**驗證**頁面**交換設定**區段中，請確定**交換控制編號 （檢查重複的 isa13）**未選項。</span><span class="sxs-lookup"><span data-stu-id="eaa92-134">On the **Validation** page under the **Interchange Settings** section, make sure **Interchange Control Number (Check for duplicate ISA13)** option is unchecked.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="eaa92-135">清除**檢查重複的 ISA13**屬性可讓您接收相同訊息的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="eaa92-135">Clearing the **Check for duplicate ISA13** property enables you to receive multiple instances of the same message.</span></span>  
  
    4.  <span data-ttu-id="eaa92-136">在**本機主機設定**頁面的 **交換設定**區段中，清除**通知的路由設定為傳送管線在要求-回應接收埠**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-136">On the **Local Host Settings** page, under the **Interchange Settings** section, clear **Route ACK to send pipeline on request-response receive port**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="eaa92-137">清除**通知的路由設定**屬性是必要的因為這個解決方案會傳回非同步通知透過個別傳送埠，而不是透過與雙向關聯的傳送埠將同步通知接收埠。</span><span class="sxs-lookup"><span data-stu-id="eaa92-137">Clearing the **Route ACK** property is required because this solution returns an asynchronous acknowledgment via a separate send port, rather than a synchronous acknowledgment via the send port associated with a two-way receive port.</span></span>  
  
    5.  <span data-ttu-id="eaa92-138">在**本機主機設定**頁面**交易集設定**區段中，選取要用來處理內送交換的結構描述的命名空間。</span><span class="sxs-lookup"><span data-stu-id="eaa92-138">On the **Local Host Settings** page under the **Transaction Set Settings** section, select the namespace for the schema to be used to process the incoming interchange.</span></span>  
  
        |<span data-ttu-id="eaa92-139">使用</span><span class="sxs-lookup"><span data-stu-id="eaa92-139">Use this</span></span>|<span data-ttu-id="eaa92-140">動作</span><span class="sxs-lookup"><span data-stu-id="eaa92-140">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="eaa92-141">**預設值**</span><span class="sxs-lookup"><span data-stu-id="eaa92-141">**Default**</span></span>|<span data-ttu-id="eaa92-142">選取欄中的核取方塊</span><span class="sxs-lookup"><span data-stu-id="eaa92-142">Select the checkbox in the column</span></span>|  
        |<span data-ttu-id="eaa92-143">**如 ST1**</span><span class="sxs-lookup"><span data-stu-id="eaa92-143">**For ST1**</span></span>|<span data-ttu-id="eaa92-144">選取**850-Purchase Order**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-144">Select **850 - Purchase Order**.</span></span>|  
        |<span data-ttu-id="eaa92-145">**GS2**</span><span class="sxs-lookup"><span data-stu-id="eaa92-145">**GS2**</span></span>|<span data-ttu-id="eaa92-146">輸入**THEM**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-146">Enter **THEM**.</span></span>|  
        |<span data-ttu-id="eaa92-147">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="eaa92-147">**Target Namespace**</span></span>|<span data-ttu-id="eaa92-148">選取**http://schemas.microsoft.com/BizTalk/EDI/X12/2006**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-148">Select **http://schemas.microsoft.com/BizTalk/EDI/X12/2006**.</span></span>|  
  
        > [!NOTE]
        >  <span data-ttu-id="eaa92-149">設定屬性可以讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 判斷要用於處理內送 850 交換的結構描述。</span><span class="sxs-lookup"><span data-stu-id="eaa92-149">Setting the properties enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to determine the schema to be used in processing the incoming 850 interchange.</span></span> <span data-ttu-id="eaa92-150">如果交換的 GS02 和 ST01 值是輸入在格線行中，則將會使用同一行的目標命名空間來判斷要使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="eaa92-150">If an interchange has the values of GS02 and ST01 that are entered on a line of the grid, then the target namespace for the same line will be used to determine the schema to be used.</span></span>  
  
9. <span data-ttu-id="eaa92-151">在上執行下列工作**OrderSystem-> Fabrikam**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="eaa92-151">Perform the following tasks on the **OrderSystem->Fabrikam** tab.</span></span>  
  
    1.  <span data-ttu-id="eaa92-152">在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="eaa92-152">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  
  
        |<span data-ttu-id="eaa92-153">使用</span><span class="sxs-lookup"><span data-stu-id="eaa92-153">Use this</span></span>|<span data-ttu-id="eaa92-154">動作</span><span class="sxs-lookup"><span data-stu-id="eaa92-154">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="eaa92-155">**傳送者辨識符號 (ISA5)**</span><span class="sxs-lookup"><span data-stu-id="eaa92-155">**Sender qualifier (ISA5)**</span></span>|<span data-ttu-id="eaa92-156">選取**ZZ-使用者相互定義**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-156">Select **ZZ - Mutually Defined**.</span></span>|  
        |<span data-ttu-id="eaa92-157">**寄件者識別項 (ISA6)**</span><span class="sxs-lookup"><span data-stu-id="eaa92-157">**Sender identifier (ISA6)**</span></span>|<span data-ttu-id="eaa92-158">輸入**美國**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-158">Enter **US**.</span></span>|  
        |<span data-ttu-id="eaa92-159">**接收者辨識符號 (ISA7)**</span><span class="sxs-lookup"><span data-stu-id="eaa92-159">**Receiver qualifier (ISA7)**</span></span>|<span data-ttu-id="eaa92-160">選取**ZZ-使用者相互定義**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-160">Select **ZZ - Mutually Defined**.</span></span>|  
        |<span data-ttu-id="eaa92-161">**接收者識別項 (ISA8)**</span><span class="sxs-lookup"><span data-stu-id="eaa92-161">**Receiver identifier (ISA8)**</span></span>|<span data-ttu-id="eaa92-162">輸入**THEM**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-162">Enter **THEM**.</span></span>|  
  
    2.  <span data-ttu-id="eaa92-163">在**字元集和分隔符號**頁面的 **交換設定**區段中，選取**CR LF**如**尾碼**屬性。</span><span class="sxs-lookup"><span data-stu-id="eaa92-163">On the **Charset and Separators** page, under the **Interchange Settings** section, select **CR LF** for the **Suffix** property.</span></span>  
  
    3.  <span data-ttu-id="eaa92-164">在**傳送埠**頁面**交換設定**區段中，fabrikam 會傳送通知的傳送埠產生關聯。</span><span class="sxs-lookup"><span data-stu-id="eaa92-164">On the **Send Ports** page under the **Interchange Settings** section, associate the send port that will be sending the acknowledgement back to Fabrikam.</span></span> <span data-ttu-id="eaa92-165">在**傳送埠**方格下方**名稱**資料行，按一下空白儲存格，然後從下拉式清單中，選取 傳送埠 (**toTHEM_997**) 建立，以便傳送 997通知給 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="eaa92-165">In the **Send ports** grid, under the **Name** column, click an empty cell, and from the drop-down list, select the send port (**toTHEM_997**) created for sending the 997 acknowledgement to Fabrikam.</span></span>  
  
    4.  <span data-ttu-id="eaa92-166">在**信封**頁面**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。</span><span class="sxs-lookup"><span data-stu-id="eaa92-166">On the **Envelopes** page under the **Transaction Set Settings** section, enter values for all columns in the first line of the grid.</span></span>  
  
        |<span data-ttu-id="eaa92-167">使用</span><span class="sxs-lookup"><span data-stu-id="eaa92-167">Use this</span></span>|<span data-ttu-id="eaa92-168">動作</span><span class="sxs-lookup"><span data-stu-id="eaa92-168">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="eaa92-169">**預設值**</span><span class="sxs-lookup"><span data-stu-id="eaa92-169">**Default**</span></span>|<span data-ttu-id="eaa92-170">選取核取方塊**預設**資料行。</span><span class="sxs-lookup"><span data-stu-id="eaa92-170">Select the checkbox in the **Default** column.</span></span> <span data-ttu-id="eaa92-171">**注意：**當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **GS7**，和**GS8**可用即使值**交易類型**，**版本/版次**，和**目標命名空間**都不符合訊息。</span><span class="sxs-lookup"><span data-stu-id="eaa92-171">**Note:**  When you select this row as the default, the values for **GS1**, **GS2**, **GS3**, **GS7**, and **GS8** are used even if the values for **Transaction Type**, **Version/Release**, and **Target namespace** are not a match for the message.</span></span>|  
        |<span data-ttu-id="eaa92-172">**交易類型**</span><span class="sxs-lookup"><span data-stu-id="eaa92-172">**Transaction Type**</span></span>|<span data-ttu-id="eaa92-173">選取的測試訊息，訊息類型**850-Purchase Order**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-173">Select the message type of your test message, **850 - Purchase Order**.</span></span>|  
        |<span data-ttu-id="eaa92-174">**版本/版次**</span><span class="sxs-lookup"><span data-stu-id="eaa92-174">**Version/Release**</span></span>|<span data-ttu-id="eaa92-175">輸入 EDI 版本， **00401**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-175">Enter the EDI version, **00401**.</span></span>|  
        |<span data-ttu-id="eaa92-176">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="eaa92-176">**Target namespace**</span></span>|<span data-ttu-id="eaa92-177">選取**http://schemas.microsoft.com/Edi/X12**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-177">Select **http://schemas.microsoft.com/Edi/X12**.</span></span>|  
        |<span data-ttu-id="eaa92-178">**GS1**</span><span class="sxs-lookup"><span data-stu-id="eaa92-178">**GS1**</span></span>|<span data-ttu-id="eaa92-179">確認**PO-Purchase Order (850)**已選取。</span><span class="sxs-lookup"><span data-stu-id="eaa92-179">Verify that **PO - Purchase Order (850)** is selected.</span></span>|  
        |<span data-ttu-id="eaa92-180">**GS2**</span><span class="sxs-lookup"><span data-stu-id="eaa92-180">**GS2**</span></span>|<span data-ttu-id="eaa92-181">輸入**1234567**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-181">Enter **1234567**.</span></span><br /><br /> <span data-ttu-id="eaa92-182">**寄件者應用程式識別碼。**</span><span class="sxs-lookup"><span data-stu-id="eaa92-182">**Sender Application ID.**</span></span>|  
        |<span data-ttu-id="eaa92-183">**GS3**</span><span class="sxs-lookup"><span data-stu-id="eaa92-183">**GS3**</span></span>|<span data-ttu-id="eaa92-184">輸入**0000000**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-184">Enter **0000000**.</span></span><br /><br /> <span data-ttu-id="eaa92-185">**接收者應用程式識別碼。**</span><span class="sxs-lookup"><span data-stu-id="eaa92-185">**Receiver Application ID.**</span></span>|  
        |<span data-ttu-id="eaa92-186">**GS4**</span><span class="sxs-lookup"><span data-stu-id="eaa92-186">**GS4**</span></span>|<span data-ttu-id="eaa92-187">選取**CCYYMMDD**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-187">Select **CCYYMMDD**.</span></span> <span data-ttu-id="eaa92-188">**注意：**您必須在下拉式清單中選取值，不只是按一下欄位以顯示預設值。</span><span class="sxs-lookup"><span data-stu-id="eaa92-188">**Note:**  You have to select the value in the drop-down list, not just click in the field to display the default.</span></span> <span data-ttu-id="eaa92-189">如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。</span><span class="sxs-lookup"><span data-stu-id="eaa92-189">If you click in the field without selecting the value from the drop-down list, the value will not actually be selected.</span></span>|  
        |<span data-ttu-id="eaa92-190">**GS5**</span><span class="sxs-lookup"><span data-stu-id="eaa92-190">**GS5**</span></span>|<span data-ttu-id="eaa92-191">選取**HHMM**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-191">Select **HHMM**.</span></span>|  
        |<span data-ttu-id="eaa92-192">**GS7**</span><span class="sxs-lookup"><span data-stu-id="eaa92-192">**GS7**</span></span>|<span data-ttu-id="eaa92-193">選取**X-Accredited 的 Standards Committee X12**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-193">Select **X - Accredited Standards Committee X12**.</span></span>|  
        |<span data-ttu-id="eaa92-194">**GS8**</span><span class="sxs-lookup"><span data-stu-id="eaa92-194">**GS8**</span></span>|<span data-ttu-id="eaa92-195">確認**00401**已輸入。</span><span class="sxs-lookup"><span data-stu-id="eaa92-195">Verify that **00401** has been entered.</span></span>|  
  
        > [!NOTE]
        >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="eaa92-196">將值，來設定 GS01、 GS02、 GS03、 GS04、 GS05、 GS07 和 GS08 輸出的輸入值為基礎的通知**交易類型**，**版本/版次**，和**目標命名空間**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-196"> will set the values for GS01, GS02, GS03, GS04, GS05, GS07, and GS08 of the outbound acknowledgments based on the values entered for **Transaction Type**, **Version/Release**, and **Target namespace**.</span></span> <span data-ttu-id="eaa92-197">傳送管線會嘗試將交易集類型、X12 版本和目標命名空間，與訊息標頭中的對應值進行比對。</span><span class="sxs-lookup"><span data-stu-id="eaa92-197">The send pipeline attempts to match the transaction set type, the X12 version, and the target namespace with the corresponding values in the header of the message.</span></span> <span data-ttu-id="eaa92-198">如果成功，它會使用相關聯的 GS 值**交易類型**，**版本/版次**，和**目標命名空間**值。</span><span class="sxs-lookup"><span data-stu-id="eaa92-198">If successful, it uses the GS values associated with the **Transaction Type**, **Version/Release**, and **Target namespace** values.</span></span>  
  
10. <span data-ttu-id="eaa92-199">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-199">Click **Apply**.</span></span>  
  
11. <span data-ttu-id="eaa92-200">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-200">Click **OK**.</span></span> <span data-ttu-id="eaa92-201">新增的協議會列在**協議**區段**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="eaa92-201">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="eaa92-202">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="eaa92-202">The newly added agreement is enabled by default.</span></span>  
  
12. <span data-ttu-id="eaa92-203">重新啟動 BizTalk 服務。</span><span class="sxs-lookup"><span data-stu-id="eaa92-203">Restart the BizTalk Service.</span></span> <span data-ttu-id="eaa92-204">在 BizTalk Server 管理主控台中，在**平台設定**，按一下**主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下  **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="eaa92-204">In the BizTalk Server Administration Console, under **Platform Settings**, click **Host Instances**, right-click **BizTalkServerApplication**, and then click **Restart**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eaa92-205">BizTalk 服務在 EDI 狀態報告啟動或停用之後必須重新啟動，讓變更生效。</span><span class="sxs-lookup"><span data-stu-id="eaa92-205">The BizTalk Service needs to be restarted after EDI status reporting has been activated or deactivated for the change to take effect.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="eaa92-206">後續步驟</span><span class="sxs-lookup"><span data-stu-id="eaa92-206">Next Steps</span></span>  
 <span data-ttu-id="eaa92-207">測試 EDI 解決方案中所述[步驟 9： 測試 EDI 解決方案](../core/step-9-test-the-edi-solution.md)</span><span class="sxs-lookup"><span data-stu-id="eaa92-207">Test the EDI solution as described in [Step 9: Test the EDI Solution](../core/step-9-test-the-edi-solution.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa92-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaa92-208">See Also</span></span>  
 [<span data-ttu-id="eaa92-209">設定編碼協議屬性</span><span class="sxs-lookup"><span data-stu-id="eaa92-209">Configuring Encoding Agreement Properties</span></span>](../core/configuring-encoding-agreement-properties.md)
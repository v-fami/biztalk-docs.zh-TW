---
title: 設定批次處理 (EDIFACT) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f711ff4b-702b-419b-9c17-dce60ea437a0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 116c196d4688e4e7d21c8951c32838539cf10aa4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234662"
---
# <a name="configuring-batching-edifact"></a><span data-ttu-id="6a4a2-102">設定批次處理 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="6a4a2-102">Configuring Batching (EDIFACT)</span></span>
<span data-ttu-id="6a4a2-103">批次定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何產生 EDI 批次並傳送給合作對象。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-103">Batches define how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates and sends an EDI batches to the party.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6a4a2-104">所有屬性已停都用此頁面上即使您清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-104">All properties are disabled on this page even if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span> <span data-ttu-id="6a4a2-105">**新批次**按鈕已停用此頁面上。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-105">The **New Batch** button is disabled on this page.</span></span>  
>   
>  <span data-ttu-id="6a4a2-106">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-106">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="6a4a2-107">比方說，如果您建立兩個合作對象的合作對象 A 與合作對象 B 和合作對象 a 清除核取方塊，**新批次**會停用按鈕**合作對象 a-> 合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-107">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the **New Batch** button is disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6a4a2-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="6a4a2-108">Prerequisites</span></span>  
 <span data-ttu-id="6a4a2-109">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-batching-settings"></a><span data-ttu-id="6a4a2-110">若要設定批次處理的設定值</span><span class="sxs-lookup"><span data-stu-id="6a4a2-110">To configure batching settings</span></span>  
  
1.  <span data-ttu-id="6a4a2-111">建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-111">Create an EDIFACT encoding agreement as described in [Configuring General Settings (EDIFACT)](../core/configuring-general-settings-edifact.md).</span></span> <span data-ttu-id="6a4a2-112">若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-112">To update an existing agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6a4a2-113">在單向協議索引標籤底下**交換設定**區段中，按一下**批次組態**。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-113">On a one-way agreement tab, under **Interchange Settings** section, click **Batching Configuration**.</span></span>  
  
3.  <span data-ttu-id="6a4a2-114">從**批次組態**頁面上，按一下**新批次**來建立新的批次組態。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-114">From the **Batch Configuration** page click **New Batch** to create a new batch configuration.</span></span> <span data-ttu-id="6a4a2-115">A **Batch1**索引標籤會加入。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-115">A **Batch1** tab is added.</span></span>  
  
4.  <span data-ttu-id="6a4a2-116">在**識別** 索引標籤的區段中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6a4a2-116">In the **Identification** section of the tab perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="6a4a2-117">輸入**批次**名稱。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-117">Enter the **Batch** name.</span></span> <span data-ttu-id="6a4a2-118">這個值會當做此批次組態的索引標籤識別項。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-118">This value is used as the tab identifier for this batch configuration.</span></span>  
  
    2.  <span data-ttu-id="6a4a2-119">輸入在此批次組態的描述**批次描述**。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-119">Enter a description of this batch configuration in **Batch description**.</span></span>  
  
    3.  <span data-ttu-id="6a4a2-120">**批次識別碼**是唯讀文字方塊套用批次的設定之後，顯示唯一的批次識別碼。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-120">**Batch ID** is a read-only text box that displays a unique batch ID after you apply the settings for the batch.</span></span>  
  
    4.  <span data-ttu-id="6a4a2-121">**協調流程執行個體識別碼**是唯讀文字方塊顯示批次相關聯的批次處理協調流程執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-121">**Orchestration instance ID** is a read-only text box that displays the batching orchestration instance ID that the batch is associated with.</span></span> <span data-ttu-id="6a4a2-122">在批次啟動之後，就會顯示協調流程執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-122">An orchestration instance ID is displayed after a batch is started.</span></span>  
  
5.  <span data-ttu-id="6a4a2-123">在**篩選** 索引標籤的區段中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6a4a2-123">In the **Filter** section of the tab perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="6a4a2-124">按一下**篩選**。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-124">Click **Filter**.</span></span>  
  
    2.  <span data-ttu-id="6a4a2-125">在**批次篩選條件**對話方塊方塊中，輸入屬性、 運算子和值，來建置批次處理協調流程的訂閱篩選條件。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-125">In the **Batch Filter** dialog box, enter the property, operator and values to build the subscription filter for the batching orchestration.</span></span> <span data-ttu-id="6a4a2-126">這些篩選子句會判定路由協調流程要將哪些交易集路由到 MessageBox 以進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-126">These filter clauses determine which transaction sets the routing orchestration will route to the MessageBox for batching.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6a4a2-127">若要指定某個群組的所有訊息都必須批次處理，請將批次篩選條件中的合作對象屬性設為該合作對象的名稱。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-127">To specify that all messages to a group will be batched, set the party property in the batch filter to the party name.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6a4a2-128">如需批次處理程序的詳細資訊，請參閱[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-128">For more information about the batching process, see [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).</span></span>  
  
    3.  <span data-ttu-id="6a4a2-129">若要刪除的資料列，選取資料列，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-129">To delete a row, select the row and click **Delete**.</span></span>  
  
    4.  <span data-ttu-id="6a4a2-130">若要向上或向下移動一個資料列，按一下 **移**或**下移**按鈕。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-130">To move a row up or down, click the **Move Up** or **Move Down** buttons.</span></span>  
  
6.  <span data-ttu-id="6a4a2-131">在**發行** 索引標籤的區段中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6a4a2-131">In the **Release** section of the tab perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="6a4a2-132">選取**排程**來建立和傳送批次根據預先決定的排程。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-132">Select **Schedule** to create and send a batch according to a predetermined schedule.</span></span> <span data-ttu-id="6a4a2-133">若要定義排程，請按一下**排程器**再繼續執行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6a4a2-133">To define the schedule, click **Scheduler** and then proceed as follows:</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6a4a2-134">批次排程可能會受到特殊事件影響。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-134">A batch schedule may be affected by special events.</span></span> <span data-ttu-id="6a4a2-135">例如，日光節約時間的開始。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-135">An example is the onset of daylight savings time.</span></span> <span data-ttu-id="6a4a2-136">如果按照每小時的基準，將批次排定在日光節約時間開始後不到一個小時的時間，則以遞增小時的方式重設時鐘後，將不會建立和傳送批次。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-136">If a batch were scheduled on an hourly basis less than an hour after the onset of daylight savings time, the batch would not be created and sent after clocks were reset by incrementing the hour.</span></span> <span data-ttu-id="6a4a2-137">您可以按一下導致略過批次的特殊事件補償**啟動**按鈕**批次**頁面，即可手動啟動批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-137">You can compensate for special events that result in a skipped batch by clicking the **Start** button on the **Batches** page to start the batching orchestration manually.</span></span> <span data-ttu-id="6a4a2-138">您可能也必須停止重複的批次。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-138">You may also have to stop a duplicated batch.</span></span>  
  
        -   <span data-ttu-id="6a4a2-139">若要每小時傳送一個批次，請選取**每小時**。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-139">To send a batch on an hourly basis, select **Hourly**.</span></span> <span data-ttu-id="6a4a2-140">從下拉式清單中，為**初次釋放於**選取，表示批次第一次釋放的日期，然後輸入時間。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-140">From the drop-down list for **First release at**, select a date for the first release of the batch, and then enter the time.</span></span> <span data-ttu-id="6a4a2-141">如**後續釋放每個**、 從清單中選取下拉式清單中期間是否**小時**或**分鐘**，然後輸入將的小時或是分鐘數目分隔每個批次。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-141">For **Subsequent release every**, select from the drop-down list whether the period is in **Hours** or **Minutes**, and then enter the number of hours or minutes that will separate each batch.</span></span>  
  
        -   <span data-ttu-id="6a4a2-142">若要每天傳送批次，請選取**每日**。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-142">To send a batch on a daily basis, select **Daily**.</span></span> <span data-ttu-id="6a4a2-143">從下拉式清單中，為**初次釋放於**選取，表示批次第一次釋放的日期，然後輸入時間。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-143">From the drop-down list for **First release at**, select a date for the first release of the batch, and then enter the time.</span></span> <span data-ttu-id="6a4a2-144">如**後續釋放每個**，輸入每個批次分隔的天數。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-144">For **Subsequent release every**, enter the number of days that will separate each batch.</span></span>  
  
        -   <span data-ttu-id="6a4a2-145">若要於每週傳送批次，請選取**每週**。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-145">To send a batch on a weekly basis, select **Weekly**.</span></span> <span data-ttu-id="6a4a2-146">從下拉式清單中，為**初次釋放於**選取，表示批次第一次釋放的日期，然後輸入時間。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-146">From the drop-down list for **First release at**, select a date for the first release of the batch, and then enter the time.</span></span> <span data-ttu-id="6a4a2-147">如**後續釋放每個**，輸入第一次釋放當週和每次後續釋放週之間的週數。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-147">For **Subsequent release every**, enter the number of weeks between the week of the first release and the week of each subsequent release.</span></span> <span data-ttu-id="6a4a2-148">然後選取星期幾要釋放批次。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-148">Then select the days of the week that the batch will be released on.</span></span>  
  
            > [!NOTE]
            >  <span data-ttu-id="6a4a2-149">將所做的日期，在中設定第一次釋放**初次釋放於**欄位中，即使未在對話方塊中選取該星期幾。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-149">The first release will be made at the date and set in the **First release at** field, even if that day of the week was not selected in the dialog box.</span></span>  
  
            > [!NOTE]
            >  <span data-ttu-id="6a4a2-150">如果您已在對話方塊中選取一或多個星期別，則會在第一週中第一次釋放之後的任何選定日子釋放批次。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-150">If you selected one or more days of the week in the dialog box, a release will be made on any selected day of that first week that comes after the first release.</span></span> <span data-ttu-id="6a4a2-151">例如，如果選取星期一和星期五，而第一次釋放是在星期三，則會在第一週的星期五釋放。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-151">For example, if Monday and Friday have been selected, and the first release was on a Wednesday, a release will be made on Friday of the first week.</span></span> <span data-ttu-id="6a4a2-152">後續版本會發生 *n* 之後的第一週、 週與 *n* 中的值所決定**後續釋放每個**欄位。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-152">Subsequent releases will occur *n* weeks after the first week, with *n* determined by the value in the **Subsequent release every** field.</span></span> <span data-ttu-id="6a4a2-153">釋放作業將會在對話方塊中選取每個星期別進行。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-153">Release will occur on each day of the week selected in the dialog box.</span></span>  
  
        -   <span data-ttu-id="6a4a2-154">選取**傳送空的批次訊號**時不收到任何訊息已由批次處理協調流程排程傳送批次時，傳送空的批次訊號。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-154">Select **Send empty batch signal** to send an empty batch signal if no messages have been received by the batching orchestration when the batch is scheduled to be sent.</span></span>  
  
    2.  <span data-ttu-id="6a4a2-155">選取**最大數目的交易集**來建立和傳送批次，每當有特定數目的交易集或訊息路由到 MessageBox 進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-155">Select **Maximum number of transaction sets in** to create and send a batch whenever a certain number of transaction sets or messages has been routed to the MessageBox for batching.</span></span> <span data-ttu-id="6a4a2-156">選取要計算交易訊息的部分設定中 (任一**群組**或**交換**)，然後輸入批次的群組或交換中應有的交易集數目上限。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-156">Select the part of the message to count the transaction sets in (either **Group** or **Interchange**), and then enter the maximum number of transaction sets to be in the batched group or interchange.</span></span>  
  
         <span data-ttu-id="6a4a2-157">例如，如果您想要批次處理成一個批次的兩個交換選取**交換**從下拉式清單，並輸入`2`在文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-157">For example, if you want to batch two interchanges into one batch select **Interchange** from the drop-down and enter `2` in the text box.</span></span>  
  
    3.  <span data-ttu-id="6a4a2-158">選取**的交換中的字元數上限**來建立和傳送批次，可供批次處理的特定數目的字元時。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-158">Select **Maximum number of characters in an interchange** to create and send a batch when a specific number of characters are available for batch processing.</span></span> <span data-ttu-id="6a4a2-159">輸入批次群組或交換中的字元數上限。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-159">Enter the maximum number of characters in the batched group or interchange.</span></span>  
  
         <span data-ttu-id="6a4a2-160">批次處理協調流程會累積批次處理項目，直到這些項目中的字元數 (減去信封中的計數) 超過最大計數為止。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-160">The batching orchestration will accumulate batching elements until the character count in those elements (minus the count in the envelope) exceeds the maximum count.</span></span> <span data-ttu-id="6a4a2-161">接著它會批次處理所有項目 (最後一個項目除外，因為這個項目會導致計數超過最大計數)。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-161">It will then batch all but the last element (which caused the count to exceed the maximum count).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6a4a2-162">輸入的最大字元數，應該要大到足以產生對您稱得上有意義的批次。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-162">For the maximum number of characters, enter a number large enough that you will generate meaningful batches.</span></span> <span data-ttu-id="6a4a2-163">這個數目至少必須大於批次標頭的字元總數加上訊息的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-163">That number should at least be greater than the total number of characters in the batch headers and the maximum number of characters in a message.</span></span> <span data-ttu-id="6a4a2-164">數目太小可能會產生空的批次。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-164">A number that is too small could result in empty batches.</span></span>  
  
    4.  <span data-ttu-id="6a4a2-165">選取**外部釋放觸發程序**來建立和傳送批次給 BizTalk Server 外部的應用程式執行外部觸發程序時。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-165">Select **External release trigger** to create and then send a batch when an external trigger is executed by an application external to BizTalk Server.</span></span> <span data-ttu-id="6a4a2-166">如需如何設定這項機制的詳細資訊，請參閱[實作外部批次釋放機制](../core/implementing-an-external-batch-release-mechanism.md)。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-166">For more information about how to set up this mechanism, see [Implementing an External Batch Release Mechanism](../core/implementing-an-external-batch-release-mechanism.md).</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6a4a2-167">**覆寫**按鈕和**啟動範圍**控制項仍然會有效如果**外部釋放**選取了觸發程序屬性。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-167">The **Override** button and **Activation range** controls remain valid if the **External release** trigger property has been selected.</span></span>  
  
7.  <span data-ttu-id="6a4a2-168">在**啟用** 索引標籤的區段中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6a4a2-168">In the **Activation** section of the tab perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="6a4a2-169">選取**立即開始**讓批次處理協調流程立即開始批次處理訊息。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-169">Select **Start Immediately** to have the batching orchestration begin batching messages immediately.</span></span>  
  
         <span data-ttu-id="6a4a2-170">若要啟動批次處理協調流程在特定日期，請清除**立即開始**方塊和選取的日期和時間啟動批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-170">To start the batching orchestration on a specific date, clear the **Start Immediately** box and select a date and time to activate the batching orchestration.</span></span>  
  
8.  <span data-ttu-id="6a4a2-171">在**終止** 索引標籤的區段中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6a4a2-171">In the **Termination** section of the tab perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="6a4a2-172">保留**沒有結束日期**選取如果您不要指定停用批次處理協調流程的結束日期。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-172">Keep **No end date** selected if you do not want to specify an end date for the batching orchestration to be deactivated.</span></span>  
  
    2.  <span data-ttu-id="6a4a2-173">選取**發生幾次之後結束**來指定已產生批次數目之後，將會停用批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-173">Select **End after (occurrences)** to specify that the batching orchestration will be deactivated after a certain number of batches have been generated.</span></span> <span data-ttu-id="6a4a2-174">在文字方塊中輸入需要的數字。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-174">Enter the number desired in the text box.</span></span>  
  
    3.  <span data-ttu-id="6a4a2-175">選取**結束**來指定將會停用批次處理協調流程的結束日期。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-175">Select **End by** to specify an end date that the batching orchestration will be deactivated.</span></span> <span data-ttu-id="6a4a2-176">在此時間之後，將不再收集批次處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-176">Messages will no longer be collected for batching as of this time.</span></span> <span data-ttu-id="6a4a2-177">從行事曆中選取結束日期，或是直接在文字方塊中變更日期或時間。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-177">Select an end date from the calendar or change the date or time directly in the text box.</span></span>  
  
9. <span data-ttu-id="6a4a2-178">按一下**套用**套用您在先前步驟中所提供的批次設定。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-178">Click **Apply** to apply the batch settings you provided in the previous steps.</span></span> <span data-ttu-id="6a4a2-179">按一下 之後**套用**，批次識別碼建立，而且會顯示在**批次識別碼**文字欄位中的**識別**> 一節。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-179">After you click **Apply**, a batch ID is created and is displayed in the **Batch ID** text field in the **Identification** section.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a4a2-180">訊息**批次處理未啟動**底下會顯示**啟動** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-180">A message **Batching is not activated** will be displayed under the **Start** button.</span></span>  
  
10. <span data-ttu-id="6a4a2-181">按一下**啟動**即可手動啟動批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-181">Click **Start** to activate a batching orchestration manually.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a4a2-182">若要確定，批次處理協調流程便會立即啟動當您按一下**啟動**按鈕，更新 batchcontrolmessagereccvloc SQL 配接器接收位置的輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-182">To make sure that the batching orchestration will be promptly activated when you click the **Start** button, update the polling interval for the SQL adapter in the BatchControlMessageReccvLoc receive location.</span></span> <span data-ttu-id="6a4a2-183">如需詳細資訊，請參閱[(X12) 逐步解說： 傳送批次 EDI 交換](../core/walkthrough-x12-sending-batched-edi-interchanges.md)。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-183">For more information, see [Walkthrough (X12): Sending Batched EDI Interchanges](../core/walkthrough-x12-sending-batched-edi-interchanges.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a4a2-184">按一下 之後**啟動**，按一下 **重新整理**。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-184">After you click **Start**, click **Refresh**.</span></span> <span data-ttu-id="6a4a2-185">您可能需要等候一些時間讓批次與協調流程執行個體產生關聯。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-185">It can take a while to associate the batch with the orchestration instance.</span></span> <span data-ttu-id="6a4a2-186">如果您按一下**重新整理**批次都與協調流程之前，您會看到訊息**批次處理已啟動批次處理協調流程，但尚未產生**。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-186">If you click **Refresh** before the batch is associated with the orchestration, you see the message **Batching is activated, Batching orchestration not instantiated yet**.</span></span> <span data-ttu-id="6a4a2-187">按一下**重新整理**，請參閱關聯的協調流程中的執行個體識別碼**協調流程執行個體識別碼**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-187">Click **Refresh** again to see the associated orchestration’s instance ID in the **Orchestration instance ID** text box.</span></span> <span data-ttu-id="6a4a2-188">訊息**批次處理已啟動**下顯示**啟動** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-188">The message **Batching is activated** is displayed under the **Start** button.</span></span>  
  
11. <span data-ttu-id="6a4a2-189">按一下**覆寫**來強制批次處理協調流程傳送批次，不論是否已符合釋放準則。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-189">Click **Override** to forces the batching orchestration to send a batch, whether or not the release criteria have been met.</span></span> <span data-ttu-id="6a4a2-190">使用此選項會覆寫現有的批次準則，變成使用現有的項目來建立並立即傳送批次。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-190">Using this option overrides the existing batch criteria, with the result that a batch is created using existing elements and then sent immediately.</span></span> <span data-ttu-id="6a4a2-191">此後，批次處理協調流程會依據建立的設定，再繼續批次處理。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-191">After this, the batching orchestration resumes batch processing according to the established settings.</span></span>  
  
12. <span data-ttu-id="6a4a2-192">按一下**停止**，而不傳送批次結束作用中的批次處理協調流程，並手動停用批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-192">Click **Stop** to terminate an active batching orchestration without sending a batch and deactivate the batching orchestration manually.</span></span>  
  
13. <span data-ttu-id="6a4a2-193">按一下**重新整理**，重新整理批次處理協調流程的狀態。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-193">Click **Refresh** to refresh the status of the batching orchestration.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a4a2-194">您可以使用下拉式清單頂端的**批次組態**來篩選顯示所選取的批次組態索引標籤頁面**所有**（可看見所有批次的索引標籤），**主動**（若要查看作用中批次的索引標籤），或**Inactive** （可看見非作用中批次的索引標籤）。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-194">You can use the drop-down list at the top of **the Batch Configuration** page to filter the batch configuration tabs displayed by selecting **All** (to see tabs for all batches), **Active** (to see tabs for active batches), or **Inactive** (to see tabs for inactive batches).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a4a2-195">如果您在協調流程正在處理批次時變更組態設定，則新的設定不會套用至該批次。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-195">If you change the configuration settings while the orchestration is processing a batch, the new settings will not be applied to that batch.</span></span> <span data-ttu-id="6a4a2-196">這可能會在傳送管線中產生驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-196">This can result in validation errors in the send pipeline.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6a4a2-197">若要加速啟動開發伺服器上的協調流程合作對象，您可以在該伺服器上縮短批次處理 SQL 配接器接收位置 (BatchControlMessageRecvLoc) 的輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-197">To speed up activation of the batching orchestration party on a development server, you can decrease the polling interval for the batching SQL adapter receive location (BatchControlMessageRecvLoc) on that server.</span></span> <span data-ttu-id="6a4a2-198">建議您將開發伺服器的輪詢間隔設定為 30 秒。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-198">We recommend you set the polling interval for a development server to 30 seconds.</span></span>  
  
14. <span data-ttu-id="6a4a2-199">按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6a4a2-199">Click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a4a2-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a4a2-200">See Also</span></span>  
 [<span data-ttu-id="6a4a2-201">設定交換設定 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="6a4a2-201">Configuring Interchange Settings (EDIFACT)</span></span>](../core/configuring-interchange-settings-edifact.md)
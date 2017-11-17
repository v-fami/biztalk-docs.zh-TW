---
title: "保留的批次的交換 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 907e07f3-1f3e-485e-a82d-b28eb7658e0a
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e7ea2bdef1fe2b2c3db92421d610b0b889e0460
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="preserving-a-batched-interchange"></a><span data-ttu-id="87fbe-102">保留批次交換</span><span class="sxs-lookup"><span data-stu-id="87fbe-102">Preserving a Batched Interchange</span></span>
<span data-ttu-id="87fbe-103">本主題說明如何設定協議，以單一文件的方式處理批次 EDI 交換，而不需要分割交換中的交易集。</span><span class="sxs-lookup"><span data-stu-id="87fbe-103">This topic describes how to configure an agreement for processing a batched EDI interchange as a single document without splitting the transaction sets from the interchange.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="87fbe-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="87fbe-104">Prerequisites</span></span>  
 <span data-ttu-id="87fbe-105">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="87fbe-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-the-receiving-and-sending-of-a-preserved-batch"></a><span data-ttu-id="87fbe-106">若要設定保留批次的接收和傳送</span><span class="sxs-lookup"><span data-stu-id="87fbe-106">To configure the receiving and sending of a preserved batch</span></span>  
  
1.  <span data-ttu-id="87fbe-107">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**節點。</span><span class="sxs-lookup"><span data-stu-id="87fbe-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **Parties** node.</span></span> <span data-ttu-id="87fbe-108">在**合作對象與商務設定檔**頁面上，按一下會解析為內送的批次交換的協議的合作對象。</span><span class="sxs-lookup"><span data-stu-id="87fbe-108">In the **Parties and Business Profiles** page, click the party that has the agreement that will resolve to the incoming batched interchange.</span></span> <span data-ttu-id="87fbe-109">在**協議**區段頁面上，以滑鼠右鍵按一下 在協議，按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="87fbe-109">In the **Agreement** section of the page, right-click the agreement and click **Properties**.</span></span> <span data-ttu-id="87fbe-110">在**協議屬性** 對話方塊中單向協議索引標籤上 （要輸入批次的交換將解析），執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="87fbe-110">In the **Agreement Properties** dialog box, in the one-way agreement tab (to which the inbound batched interchange will resolve), do the following:</span></span>  
  
    1.  <span data-ttu-id="87fbe-111">在**識別碼**頁面上，輸入 ISA5、 ISA6、 ISA7 和 ISA8 的輸入值的值。</span><span class="sxs-lookup"><span data-stu-id="87fbe-111">In the **Identifiers** page, enter the values for enter values for ISA5, ISA6, ISA7, and ISA8.</span></span> <span data-ttu-id="87fbe-112">確定您輸入的值正確無誤，能讓內送批次交換解析成此協議。</span><span class="sxs-lookup"><span data-stu-id="87fbe-112">Make sure you enter the correct values so that the incoming batched interchange resolves to this agreement.</span></span>  
  
    2.  <span data-ttu-id="87fbe-113">在**本機主機設定**頁面 (下**交換設定**) 下**接收者的設定** 區段中，針對**輸入批次處理選項**，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="87fbe-113">In the **Local Host Settings** page (under **Interchange Settings**), under **Receiver’s Settings** section, for the **Inbound batch processing option**, select one the following options:</span></span>  
  
        -   <span data-ttu-id="87fbe-114">**保留交換-發生錯誤時暫停交換**– 選取此選項以指定 BizTalk Server 應該讓交換保持完整，建立整個批次交換的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="87fbe-114">**Preserve Interchange - suspend Interchange on Error** – Select this option to specify that BizTalk Server should leave the interchange intact, creating an XML document for the entire batched interchange.</span></span> <span data-ttu-id="87fbe-115">使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便會暫停整個交換。</span><span class="sxs-lookup"><span data-stu-id="87fbe-115">With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend the entire interchange.</span></span>  
  
        -   <span data-ttu-id="87fbe-116">**保留交換-發生錯誤時暫停交易集**– 選取此選項以指定 BizTalk Server 應該讓交換保持完整，建立整個批次交換的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="87fbe-116">**Preserve Interchange - suspend Transaction Sets on Error** – Select this option to specify that BizTalk Server should leave the interchange intact, creating an XML document for the entire batched interchange.</span></span> <span data-ttu-id="87fbe-117">使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便只會暫停這些交易集，但繼續處理其他所有的交易集。</span><span class="sxs-lookup"><span data-stu-id="87fbe-117">With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend only those transaction sets, while continuing to process all other transaction sets.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="87fbe-118">如果您選取上述兩個選項中的任一項，交換、群組和交易集區段屬性 (負責決定 BizTalk Server 如何建立外寄交換的 ISA、GS 和 ST 標頭) 即不適用。</span><span class="sxs-lookup"><span data-stu-id="87fbe-118">If you select either of the two options mentioned above, the interchange, group, and transaction set segment properties (which determine how BizTalk Server will create the ISA, GS, and ST headers of an outgoing interchange) do not apply.</span></span> <span data-ttu-id="87fbe-119">該交換、群組，以及將保留之交換中的交易集標頭，都會在傳送管線處理該交換的傳送時加以保留。</span><span class="sxs-lookup"><span data-stu-id="87fbe-119">The interchange, group, and transaction-set headers that exist in the interchange that is being preserved are retained when the send pipeline processes it for sending.</span></span> <span data-ttu-id="87fbe-120">但是，如果您想使用在協議中針對交換指定的值，請將 `EDI.PopulateInterchangeValues` 內容屬性設定為 true。</span><span class="sxs-lookup"><span data-stu-id="87fbe-120">However, if you do want to use the values specified for the interchange in the agreement, set the `EDI.PopulateInterchangeValues` context property to true.</span></span>  
  
2.  <span data-ttu-id="87fbe-121">為保留的批次建立 Visual Studio 專案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="87fbe-121">Create a Visual Studio project for the preserved batch as follows:</span></span>  
  
    1.  <span data-ttu-id="87fbe-122">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立 BizTalk 專案並針對批次內的所有訊息新增結構描述。</span><span class="sxs-lookup"><span data-stu-id="87fbe-122">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a BizTalk project and add the schemas for all the messages within the batch.</span></span>  
  
    2.  <span data-ttu-id="87fbe-123">建立及部署專案。</span><span class="sxs-lookup"><span data-stu-id="87fbe-123">Build and deploy the project.</span></span>  
  
3.  <span data-ttu-id="87fbe-124">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，建立傳送保留的批次所需的傳送埠，如下所示：</span><span class="sxs-lookup"><span data-stu-id="87fbe-124">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, create a send port to send preserved batches as follows:</span></span>  
  
    1.  <span data-ttu-id="87fbe-125">傳送管線設定為**EdiSend**或**AS2EdiSend**。</span><span class="sxs-lookup"><span data-stu-id="87fbe-125">Set the send pipeline to **EdiSend** or **AS2EdiSend**.</span></span>  
  
    2.  <span data-ttu-id="87fbe-126">將傳送埠的篩選條件設定為內容屬性 `EDI.ReuseEnvelope == True`。</span><span class="sxs-lookup"><span data-stu-id="87fbe-126">Set the filter of the send port to the context property `EDI.ReuseEnvelope == True`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="87fbe-127">設定此篩選條件可確保傳送埠會訂閱保留的所有批次交換。</span><span class="sxs-lookup"><span data-stu-id="87fbe-127">Setting this filter ensures that the send port will subscribe to all batched interchanges that are preserved.</span></span> <span data-ttu-id="87fbe-128">EdiReceive 接收管線會升級內容屬性 `EDI.ReuseEnvelope`，以將交換識別為保留的交換。</span><span class="sxs-lookup"><span data-stu-id="87fbe-128">The EdiReceive receive pipeline promotes the context property `EDI.ReuseEnvelope` to identify the interchange as preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87fbe-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87fbe-129">See Also</span></span>  
 <span data-ttu-id="87fbe-130">[設定 EDI 批次](../core/configuring-edi-batches.md) </span><span class="sxs-lookup"><span data-stu-id="87fbe-130">[Configuring EDI Batches](../core/configuring-edi-batches.md) </span></span>  
 [<span data-ttu-id="87fbe-131">如何建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="87fbe-131">How to Create a Send Port</span></span>](../core/how-to-create-a-send-port2.md)
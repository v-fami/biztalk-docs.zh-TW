---
title: "分割批次的 EDI 交換 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29c79b06-cc88-4cc8-aa99-40f24a1bdcde
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 441eafe79de57963dc1df5ac19334542f41a23d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="splitting-a-batched-edi-interchange"></a><span data-ttu-id="c1c94-102">分割批次 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="c1c94-102">Splitting a Batched EDI Interchange</span></span>
> [!NOTE]
>  <span data-ttu-id="c1c94-103">本主題中提及的所有使用者介面選項都可用於**本機主機設定**頁面 (**接收者的設定**區段) 中的單向協議索引標籤**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c1c94-103">All the user interface options mentioned in this topic are available in the **Local Host Settings** page (**Receiver’s Settings** section) of the one-way agreement tabs in the **Agreement Properties** dialog box.</span></span>  
  
 <span data-ttu-id="c1c94-104">EDI 接收管線會分割內送的 EDI 交換批次如果您已將**輸入批次處理選項**協議屬性設**將交換分割為交易集**。</span><span class="sxs-lookup"><span data-stu-id="c1c94-104">The EDI receive pipeline splits an incoming EDI interchange batch if you have set the **Inbound batch processing option** agreement property to **Split Interchange as Transaction Sets**.</span></span>  
  
 <span data-ttu-id="c1c94-105">當 EDI 接收管線分割內送批次 EDI 交換時，會為每個 EDI 交易集/訊息建立一個 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="c1c94-105">When the EDI receive pipeline splits an incoming batched EDI interchange, it creates one XML file for each EDI transaction set/message.</span></span> <span data-ttu-id="c1c94-106">管線會將整個交易和群組標頭升級至每個從交換分割出的交易集內容中。</span><span class="sxs-lookup"><span data-stu-id="c1c94-106">The pipeline promotes the entire interchange and group headers into the context of each transaction set split from the interchange.</span></span> <span data-ttu-id="c1c94-107">此外還會升級特定交換和群組標頭，例如 ISA6、GS1 和 GS2，如此就能使用這些欄位進行路由。</span><span class="sxs-lookup"><span data-stu-id="c1c94-107">It also promotes certain specific interchange and group headers, such as ISA6, GS1, and GS2, so that these fields can be used for routing.</span></span> <span data-ttu-id="c1c94-108">您可以藉由選取遮罩標頭中的安全性資訊**遮罩安全性/授權/密碼資訊**屬性。</span><span class="sxs-lookup"><span data-stu-id="c1c94-108">You can mask the security information in the header by selecting the **Mask security/authorization/password information** property.</span></span>  
  
 <span data-ttu-id="c1c94-109">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 嘗試將交換分割成交易集時，特定 ISA (ISA1 到 ISA13) 或 UNB 標頭欄位中的任何錯誤都將導致交換遭拒。</span><span class="sxs-lookup"><span data-stu-id="c1c94-109">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] attempts to split an interchange into transaction sets, any error in certain ISA (ISA1 through ISA13) or UNB header fields will lead to the interchange being rejected.</span></span> <span data-ttu-id="c1c94-110">如果協議或後援協議屬性中啟用了檢查重複的交換控制編號，則交換控制編號重複時也會發生同樣的情況。</span><span class="sxs-lookup"><span data-stu-id="c1c94-110">This is also the case when the interchange control number is a duplicate, if the check for a duplicate interchange control number is enabled in the agreement or fallback agreement properties.</span></span> <span data-ttu-id="c1c94-111">其他交換標頭欄位 (X12 交換的 ISA1 到 ISA13 以外) 或群組標頭欄位中的錯誤，可能不會造成交換程序失敗。</span><span class="sxs-lookup"><span data-stu-id="c1c94-111">An error in other interchange header fields (other than ISA1 through ISA13 for X12 interchange) or in the group header fields would not cause interchange processing to fail.</span></span>  
  
 <span data-ttu-id="c1c94-112">如果**將交換分割為交易集-發生錯誤時暫停交易集**協議屬性中選取[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會暫停交易集發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c1c94-112">If **Split Interchange as Transaction Sets - suspend Transaction Sets on Error** is selected in agreement properties, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the transaction set if an error occurs.</span></span> <span data-ttu-id="c1c94-113">如果**將交換分割為交易集-發生錯誤時暫停交換**選取時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會擱置交換。</span><span class="sxs-lookup"><span data-stu-id="c1c94-113">If **Split Interchange as Transaction Sets – suspend Interchange on Error** is selected, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the interchange.</span></span>  
  
 <span data-ttu-id="c1c94-114">每個 XML 批次元素都會路由至 MessageBox，並且由訂閱批次元素的傳送埠或協調流程處理。</span><span class="sxs-lookup"><span data-stu-id="c1c94-114">Each XML batch element is routed to the MessageBox, and processed by the send ports or orchestrations that subscribe to the batch element.</span></span> <span data-ttu-id="c1c94-115">交換中的交易集在處理為分割訊息之後，可能不會保留其排序。</span><span class="sxs-lookup"><span data-stu-id="c1c94-115">The ordering of transaction sets in the interchange may not be retained after they are processed as split messages.</span></span> <span data-ttu-id="c1c94-116">在接收端，訊息將依在交換中出現的順序處理，並且依同樣的順序放入 MessageBox，但是您必須使用群組或循序傳遞傳送埠在傳送端維持該排序。</span><span class="sxs-lookup"><span data-stu-id="c1c94-116">On the receive side, the messages will be processed in the order that they appear in the interchange, and they will be placed in the MessageBox in that order, but you would have to use convoys or ordered delivery send ports to maintain that order on the send side.</span></span>  
  
 <span data-ttu-id="c1c94-117">如果分割自批次的元素將納入外寄批次中，則 BatchMarker 管線元件會升級所需的屬性。</span><span class="sxs-lookup"><span data-stu-id="c1c94-117">If the elements split from a batch will be included in an outgoing batch, the BatchMarker pipeline component promotes the required properties.</span></span> <span data-ttu-id="c1c94-118">如需詳細資訊，請參閱[批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="c1c94-118">For more information, see [Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c94-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1c94-119">See Also</span></span>  
 <span data-ttu-id="c1c94-120">[處理內送的批次](../core/processing-incoming-batches.md) </span><span class="sxs-lookup"><span data-stu-id="c1c94-120">[Processing Incoming Batches](../core/processing-incoming-batches.md) </span></span>  
 [<span data-ttu-id="c1c94-121">批次處理外寄 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="c1c94-121">Batching Outgoing EDI Messages</span></span>](../core/batching-outgoing-edi-messages.md)
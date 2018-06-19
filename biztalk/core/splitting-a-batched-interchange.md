---
title: 分割批次的交換 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67bef19-77fb-47a9-88f3-ee20043b3691
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 745f94d4ec56222d3c1d3e03c0817933248f4b8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278942"
---
# <a name="splitting-a-batched-interchange"></a><span data-ttu-id="ed966-102">分割批次交換</span><span class="sxs-lookup"><span data-stu-id="ed966-102">Splitting a Batched Interchange</span></span>
<span data-ttu-id="ed966-103">本主題會說明如何藉由分割交換中的交易集，來設定處理批次 EDI 交換的協議。</span><span class="sxs-lookup"><span data-stu-id="ed966-103">This topic describes how to configure an agreement for processing a batched EDI interchange by splitting the transaction sets from the interchange.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ed966-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="ed966-104">Prerequisites</span></span>  
 <span data-ttu-id="ed966-105">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="ed966-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-receive-a-split-edi-interchange"></a><span data-ttu-id="ed966-106">若要接收分割的 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="ed966-106">To receive a split EDI interchange</span></span>  
  
1.  <span data-ttu-id="ed966-107">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**節點。</span><span class="sxs-lookup"><span data-stu-id="ed966-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **Parties** node.</span></span> <span data-ttu-id="ed966-108">在**合作對象與商務設定檔**頁面上，按一下會解析為內送的批次交換的協議的合作對象。</span><span class="sxs-lookup"><span data-stu-id="ed966-108">In the **Parties and Business Profiles** page, click the party that has the agreement that will resolve to the incoming batched interchange.</span></span> <span data-ttu-id="ed966-109">在**協議**區段頁面上，以滑鼠右鍵按一下 在協議，按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="ed966-109">In the **Agreement** section of the page, right-click the agreement and click **Properties**.</span></span> <span data-ttu-id="ed966-110">在**協議屬性** 對話方塊中單向協議索引標籤上 （要輸入批次的交換將解析），執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="ed966-110">In the **Agreement Properties** dialog box, in the one-way agreement tab (to which the inbound batched interchange will resolve), do the following:</span></span>  
  
    1.  <span data-ttu-id="ed966-111">在**識別碼**頁面上，確定您輸入正確的值，讓內送的批次的交換解析成此協議。</span><span class="sxs-lookup"><span data-stu-id="ed966-111">In the **Identifiers** page, make sure you enter the correct values so that the incoming batched interchange resolves to this agreement.</span></span>  
  
        -   <span data-ttu-id="ed966-112">如果是**X12**： 設定 ISA5、 ISA6、 ISA7 和 ISA8。</span><span class="sxs-lookup"><span data-stu-id="ed966-112">In case of **X12**: Set ISA5, ISA6, ISA7, and ISA8.</span></span>  
  
        -   <span data-ttu-id="ed966-113">如果是**Edifact**： 設定 UNB2.1、 UNB2.2、 UNB3.1 和 UNB3.2。</span><span class="sxs-lookup"><span data-stu-id="ed966-113">In case of **Edifact**: Set UNB2.1, UNB2.2, UNB3.1, and UNB3.2.</span></span>  
  
    2.  <span data-ttu-id="ed966-114">在**本機主機設定**頁面 (下**交換設定**) 下**接收者的設定** 區段中，針對**輸入批次處理選項**，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="ed966-114">In the **Local Host Settings** page (under **Interchange Settings**), under **Receiver’s Settings** section, for the **Inbound batch processing option**, select one the following options:</span></span>  
  
        -   <span data-ttu-id="ed966-115">**將交換分割為交易集-發生錯誤時暫停交易集**– 選取此選項以指定 BizTalk Server 應該剖析每個交易集在個別的 XML 文件的交換。</span><span class="sxs-lookup"><span data-stu-id="ed966-115">**Split Interchange as Transaction Sets - suspend Transaction Sets on Error** – Select this option to specify that BizTalk Server should parse each transaction set in an interchange into a separate XML document.</span></span> <span data-ttu-id="ed966-116">然後，BizTalk Server 便會將適當的信封套用至交易集，並將交易集文件路由到 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="ed966-116">BizTalk Server will then apply the appropriate envelope to the transaction set and route the transaction set document to the MessageBox.</span></span> <span data-ttu-id="ed966-117">使用此選項時，如果交換中的一或多個交易集驗證失敗，BizTalk Server 將只會暫停這些交易集。</span><span class="sxs-lookup"><span data-stu-id="ed966-117">With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend only those transaction sets.</span></span>  
  
        -   <span data-ttu-id="ed966-118">**將交換分割為交易集-發生錯誤時暫停交換**– 選取此選項以指定 BizTalk Server 應該剖析每個交易集在個別的 XML 文件的交換。</span><span class="sxs-lookup"><span data-stu-id="ed966-118">**Split Interchange as Transaction Sets - suspend Interchange on Error** – Select this option to specify that BizTalk Server should parse each transaction set in an interchange into a separate XML document.</span></span> <span data-ttu-id="ed966-119">然後，BizTalk Server 便會將適當的信封套用至交易集，並將交易集文件路由到 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="ed966-119">BizTalk Server will then apply the appropriate envelope to the transaction set and route the transaction set document to the MessageBox.</span></span> <span data-ttu-id="ed966-120">使用此選項時，如果交換中的一或多個交易集的驗證失敗，BizTalk Server 便會暫停整個交換。</span><span class="sxs-lookup"><span data-stu-id="ed966-120">With this option, if one or more transaction sets in the interchange fail validation, BizTalk Server will suspend the entire interchange.</span></span>  
  
2.  <span data-ttu-id="ed966-121">為保留的批次建立 Visual Studio 專案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ed966-121">Create a Visual Studio project for the preserved batch as follows:</span></span>  
  
    1.  <span data-ttu-id="ed966-122">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立 BizTalk 專案並針對批次內的所有訊息新增結構描述。</span><span class="sxs-lookup"><span data-stu-id="ed966-122">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a BizTalk project and add the schemas for all the messages within the batch.</span></span>  
  
    2.  <span data-ttu-id="ed966-123">建立及部署專案。</span><span class="sxs-lookup"><span data-stu-id="ed966-123">Build and deploy the project.</span></span>  
  
3.  <span data-ttu-id="ed966-124">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，建立傳送分割批次所需的傳送埠，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ed966-124">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, create a send port to send split batches as follows:</span></span>  
  
    1.  <span data-ttu-id="ed966-125">傳送管線設定為**EdiSend**或**AS2EdiSend**。</span><span class="sxs-lookup"><span data-stu-id="ed966-125">Set the send pipeline to **EdiSend** or **AS2EdiSend**.</span></span>  
  
    2.  <span data-ttu-id="ed966-126">將傳送埠的篩選條件設定為取得每個交易集的必要值，例如，設定為 BTS.MessageType。</span><span class="sxs-lookup"><span data-stu-id="ed966-126">Set the filter of the send port to the value required to pick up each transaction set, for example, to BTS.MessageType.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed966-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed966-127">See Also</span></span>  
 <span data-ttu-id="ed966-128">[設定 EDI 批次](../core/configuring-edi-batches.md) </span><span class="sxs-lookup"><span data-stu-id="ed966-128">[Configuring EDI Batches](../core/configuring-edi-batches.md) </span></span>  
 [<span data-ttu-id="ed966-129">如何建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="ed966-129">How to Create a Send Port</span></span>](../core/how-to-create-a-send-port2.md)
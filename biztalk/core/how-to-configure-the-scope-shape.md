---
title: "如何設定 「 範圍 」 圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shape [Orchestration Designer], about Scope shape
- Scope shape [Orchestration Designer], configuring
- Scope shape [Orchestration Designer], variables
- Scope shape [Orchestration Designer]
- configuring [Orchestration Designer], Scope shape
- Scope shape [Orchestration Designer], transactions
ms.assetid: 3c518db0-d68c-4f72-9d5c-48540811e289
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef17f5d1ab94875af118d17551da4334525535fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-scope-shape"></a><span data-ttu-id="29187-102">如何設定範圍圖形</span><span class="sxs-lookup"><span data-stu-id="29187-102">How to Configure the Scope Shape</span></span>
<span data-ttu-id="29187-103">**範圍**圖形為其內容提供內容架構。</span><span class="sxs-lookup"><span data-stu-id="29187-103">The **Scope** shape provides a contextual framework for its contents.</span></span> <span data-ttu-id="29187-104">第一個區塊**範圍**圖形是內容區塊或主體中，基本的動作範圍的發生; 它類似 try/catch 陳述式中的 try 區塊。</span><span class="sxs-lookup"><span data-stu-id="29187-104">The first block of a **Scope** shape is the context block, or body, in which the basic actions of the scope take place; it is analogous to the try block in a try/catch statement.</span></span> <span data-ttu-id="29187-105">緊接著內文，**範圍**圖形可能還包含一個或多個例外狀況處理常式區塊和補償區塊。</span><span class="sxs-lookup"><span data-stu-id="29187-105">Following the body, the **Scope** shape may also include one or more exception-handler blocks and a compensation block.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29187-106">在多重電腦環境中其中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SQL Server 位於不同的電腦，如果 Coordinated Universal Time (UTC) 是在不同的兩部電腦上則**逾時**您設定的屬性**範圍**圖形可能會比預期的 UTC 時間因為在較早觸發[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SQL Server 機器未同步處理。</span><span class="sxs-lookup"><span data-stu-id="29187-106">In a multiple machine environment where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server are located on different machines, if the Coordinated Universal Time (UTC) is different on the two machines then the **Timeout** property you configure for the **Scope** shape may get triggered earlier than expected because of the UTC time on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server machines is unsynchronized.</span></span> <span data-ttu-id="29187-107">請注意，這並不是時區問題，因為 Coordinated Universal Time 不受時區影響。</span><span class="sxs-lookup"><span data-stu-id="29187-107">Note that this is not a time zones issue as Coordinated Universal Time is unaffected by time zones.</span></span>  
  
### <a name="to-configure-a-scope-shape-as-a-transaction-boundary"></a><span data-ttu-id="29187-108">若要將範圍圖形設定為交易界限</span><span class="sxs-lookup"><span data-stu-id="29187-108">To configure a Scope shape as a transaction boundary</span></span>  
  
1.  <span data-ttu-id="29187-109">在 [屬性] 視窗中，設定**交易類型**屬性**不可部分完成**或**長時間執行**。</span><span class="sxs-lookup"><span data-stu-id="29187-109">In the Properties window, set the **Transaction Type** property to **Atomic** or **Long Running**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29187-110">協調流程本身必須為長時間執行的交易，您才能將 [交易類型] 設定為 [不可部分完成] 或 [長時間執行]。</span><span class="sxs-lookup"><span data-stu-id="29187-110">The orchestration must itself be a long-running transaction in order for you to set the Transaction Type to Atomic or Long Running.</span></span>  
  
2.  <span data-ttu-id="29187-111">如果**交易類型**設**不可部分完成**，然後在 [屬性] 視窗中，指定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="29187-111">If the **Transaction Type** is set to **Atomic**, then in the Properties window, specify the following properties:</span></span>  
  
    |<span data-ttu-id="29187-112">屬性</span><span class="sxs-lookup"><span data-stu-id="29187-112">Property</span></span>|<span data-ttu-id="29187-113">Description</span><span class="sxs-lookup"><span data-stu-id="29187-113">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="29187-114">批次</span><span class="sxs-lookup"><span data-stu-id="29187-114">Batch</span></span>|<span data-ttu-id="29187-115">布林值，決定此交易是否能與其他交易跨越協調流程的多個執行個體，以批次方式執行。</span><span class="sxs-lookup"><span data-stu-id="29187-115">Boolean value that determines if this transaction can be batched with other transactions across multiple instances of the orchestration.</span></span> <span data-ttu-id="29187-116">在 BizTalk Server 中絕對不會使用這個屬性，因為 BizTalk Server 並不支援跨越協調流程的多個執行個體，以批次方式進行不可部分完成的執行。</span><span class="sxs-lookup"><span data-stu-id="29187-116">This property is never used in BizTalk Server because BizTalk Server does not support batching atomic transactions across multiple instances of orchestrations.</span></span> <span data-ttu-id="29187-117">這個屬性會在未來的版本中被取代。</span><span class="sxs-lookup"><span data-stu-id="29187-117">This property will be deprecated in the future release.</span></span>|  
    |<span data-ttu-id="29187-118">隔離等級</span><span class="sxs-lookup"><span data-stu-id="29187-118">Isolation Level</span></span>|<span data-ttu-id="29187-119">決定可在並行交易之間存取資料的程度：</span><span class="sxs-lookup"><span data-stu-id="29187-119">Determines the degree to which data is accessible among concurrent transactions:</span></span><br /><br /> <span data-ttu-id="29187-120">讀取認可，若要避免選取存取在並行交易中的資料修改，直到經過認可的交易。</span><span class="sxs-lookup"><span data-stu-id="29187-120">-   Read Committed—To prevent the selected transaction from accessing data modifications in concurrent transactions until they are committed.</span></span> <span data-ttu-id="29187-121">此選項為 Microsoft SQL Server 的預設設定。</span><span class="sxs-lookup"><span data-stu-id="29187-121">This option is the Microsoft SQL Server default setting.</span></span><br /><span data-ttu-id="29187-122">可重複讀取 — 需要讀取的鎖定，直到選取的交易完成為止。</span><span class="sxs-lookup"><span data-stu-id="29187-122">-   Repeatable Read—To require read locks until the selected transaction is complete.</span></span><br /><span data-ttu-id="29187-123">可序列化 — 防止並行交易修改資料，直到選取的交易完成為止。</span><span class="sxs-lookup"><span data-stu-id="29187-123">-   Serializable—To prevent concurrent transactions from making data modifications until the selected transaction is complete.</span></span> <span data-ttu-id="29187-124">此選項是最嚴格的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="29187-124">This option is the most restrictive isolation level.</span></span>|  
    |<span data-ttu-id="29187-125">重試</span><span class="sxs-lookup"><span data-stu-id="29187-125">Retry</span></span>|<span data-ttu-id="29187-126">布林值，決定此交易是否在發生錯誤時重試。</span><span class="sxs-lookup"><span data-stu-id="29187-126">Boolean value that determines whether this transaction is retried when an error occurs.</span></span> <span data-ttu-id="29187-127">預設值為 **True**。</span><span class="sxs-lookup"><span data-stu-id="29187-127">The default value is **True**.</span></span> <span data-ttu-id="29187-128">**注意：**如果擲回 Microsoft.XLANG.BaseTypes.RetryTransactionException，或是協調流程引擎無法存放其狀態或認可的交易不可部分完成的交易將會重試。</span><span class="sxs-lookup"><span data-stu-id="29187-128">**Note:**  An atomic transaction will be retried if you throw Microsoft.XLANG.BaseTypes.RetryTransactionException, or if the orchestration engine is unable to store its state or commit the transaction.</span></span>|  
    |<span data-ttu-id="29187-129">逾時</span><span class="sxs-lookup"><span data-stu-id="29187-129">Timeout</span></span>|<span data-ttu-id="29187-130">決定由於閒置而視為交易失敗的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="29187-130">Determines the time in seconds until the transaction fails due to inactivity.</span></span> <span data-ttu-id="29187-131">如果不想使用逾時，請將此屬性的值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="29187-131">If you do not want to use a timeout, set the value of this property to 0.</span></span> <span data-ttu-id="29187-132">**注意：**這是 DTC 逾時，協調流程引擎不會強制執行。</span><span class="sxs-lookup"><span data-stu-id="29187-132">**Note:**  This is a DTC timeout, and is not enforced by the orchestration engine.</span></span> <span data-ttu-id="29187-133">唯有對於不可部分完成的交易，引擎才不會中斷交易。</span><span class="sxs-lookup"><span data-stu-id="29187-133">For atomic transactions only, the engine will not interrupt the transaction.</span></span> <span data-ttu-id="29187-134">在認可之前，引擎都會正常地繼續進行。此時唯有在透過 DTC 交易內的一個物件參與的情況下，認可才會失敗。</span><span class="sxs-lookup"><span data-stu-id="29187-134">It proceeds normally until commitment, at which point it fails to commit only if participating in a DTC transaction through one of the objects inside it.</span></span>|  
  
3.  <span data-ttu-id="29187-135">如果**交易類型**設**長時間執行**，然後在 [屬性] 視窗中，指定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="29187-135">If the **Transaction Type** is set to **Long Running**, then in the Properties window, specify the following property:</span></span>  
  
    |<span data-ttu-id="29187-136">屬性</span><span class="sxs-lookup"><span data-stu-id="29187-136">Property</span></span>|<span data-ttu-id="29187-137">Description</span><span class="sxs-lookup"><span data-stu-id="29187-137">Description</span></span>|  
    |--------------|-----------------|  
    |<span data-ttu-id="29187-138">逾時</span><span class="sxs-lookup"><span data-stu-id="29187-138">Timeout</span></span>|<span data-ttu-id="29187-139">決定由於交易逾時而視為失敗之交易的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="29187-139">Determines the time in seconds until the transaction times out and is considered a failed transaction.</span></span> <span data-ttu-id="29187-140">如果不想使用逾時，請將此屬性的值設定為 0。</span><span class="sxs-lookup"><span data-stu-id="29187-140">If you do not want to use a timeout, set the value of this property to 0.</span></span>|  
  
### <a name="to-configure-a-scope-shape-to-contain-local-variables"></a><span data-ttu-id="29187-141">若要設定範圍圖形以包含區域變數</span><span class="sxs-lookup"><span data-stu-id="29187-141">To configure a Scope shape to contain local variables</span></span>  
  
1.  <span data-ttu-id="29187-142">在 [協調流程檢視] 視窗中，按兩下範圍。</span><span class="sxs-lookup"><span data-stu-id="29187-142">Double-click the scope in the Orchestration View window.</span></span>  
  
2.  <span data-ttu-id="29187-143">以滑鼠右鍵按一下範圍下的 [變數] 資料夾，然後按一下**新變數**。</span><span class="sxs-lookup"><span data-stu-id="29187-143">Right-click the Variables folder under the scope and then click **New Variable**.</span></span>  
  
3.  <span data-ttu-id="29187-144">在中繼續執行步驟 2 中 [加入變數][如何新增協調流程變數](../core/how-to-add-orchestration-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="29187-144">Proceed from step 2 in "To add a variable" in [How to Add Orchestration Variables](../core/how-to-add-orchestration-variables.md).</span></span>
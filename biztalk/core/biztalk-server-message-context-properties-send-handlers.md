---
title: BizTalk Server 訊息內容屬性 （傳送處理常式） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a065ba89-9fdb-47dc-9021-fb95cf347cdc
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfd3dca7c807ef48c82d46743e749e19a40001bc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016297"
---
# <a name="biztalk-server-message-context-properties-send-handlers"></a><span data-ttu-id="650e8-102">BizTalk Server 訊息內容屬性 （傳送處理常式）</span><span class="sxs-lookup"><span data-stu-id="650e8-102">BizTalk Server Message Context Properties (Send Handlers)</span></span>
<span data-ttu-id="650e8-103">在執行階段，必須可從 BizTalk Server 協調流程存取的，除了有訊息內容以外，還有訊息包含的補充資訊。</span><span class="sxs-lookup"><span data-stu-id="650e8-103">In addition to the message payload, the supplementary information that a message contains must be accessible from the BizTalk Server orchestration at run time.</span></span>  
  
## <a name="tibco-rv-message-information-promoted-as-message-context-properties"></a><span data-ttu-id="650e8-104">已升級為訊息內容屬性的 TIBCO RV 訊息資訊</span><span class="sxs-lookup"><span data-stu-id="650e8-104">TIBCO RV Message Information Promoted as Message Context Properties</span></span>  
  
|<span data-ttu-id="650e8-105">資料識別</span><span class="sxs-lookup"><span data-stu-id="650e8-105">Data Identification</span></span>|<span data-ttu-id="650e8-106">類型</span><span class="sxs-lookup"><span data-stu-id="650e8-106">Type</span></span>|<span data-ttu-id="650e8-107">可路由傳送</span><span class="sxs-lookup"><span data-stu-id="650e8-107">Routable</span></span>|<span data-ttu-id="650e8-108">傳送位置</span><span class="sxs-lookup"><span data-stu-id="650e8-108">Send Location</span></span>|  
|-------------------------|----------|--------------|-------------------|  
|<span data-ttu-id="650e8-109">傳送主體</span><span class="sxs-lookup"><span data-stu-id="650e8-109">Send Subject</span></span>|<span data-ttu-id="650e8-110">string</span><span class="sxs-lookup"><span data-stu-id="650e8-110">string</span></span>|<span data-ttu-id="650e8-111">是</span><span class="sxs-lookup"><span data-stu-id="650e8-111">Yes</span></span>|<span data-ttu-id="650e8-112">協調流程會 指定 TIBCO Rendezvous 傳送主體 。</span><span class="sxs-lookup"><span data-stu-id="650e8-112">Orchestration specifies the TIBCO Rendezvous send subject.</span></span> <span data-ttu-id="650e8-113">預設值是空值。</span><span class="sxs-lookup"><span data-stu-id="650e8-113">Default value is Null.</span></span> <span data-ttu-id="650e8-114">除非連接埠組態中已指定預設主體，否則為強制性。</span><span class="sxs-lookup"><span data-stu-id="650e8-114">Mandatory unless a default subject is specified in the port configuration.</span></span>|  
|<span data-ttu-id="650e8-115">回覆主體</span><span class="sxs-lookup"><span data-stu-id="650e8-115">Reply Subject</span></span>|<span data-ttu-id="650e8-116">string</span><span class="sxs-lookup"><span data-stu-id="650e8-116">string</span></span>|<span data-ttu-id="650e8-117">是</span><span class="sxs-lookup"><span data-stu-id="650e8-117">Yes</span></span>|<span data-ttu-id="650e8-118">協調流程會 提供用於回覆訊息的相關主體 。</span><span class="sxs-lookup"><span data-stu-id="650e8-118">Orchestration provides a subject for reply messages, when pertinent.</span></span> <span data-ttu-id="650e8-119">預設值是空值。</span><span class="sxs-lookup"><span data-stu-id="650e8-119">Default value is Null.</span></span>|  
  
## <a name="getting-a-tibco-reply"></a><span data-ttu-id="650e8-120">取得 TIBCO 回覆</span><span class="sxs-lookup"><span data-stu-id="650e8-120">Getting a TIBCO Reply</span></span>  
 <span data-ttu-id="650e8-121">**問題：** 怎麼 BizTalk Adapter for TIBCO Rendezvous 讀取及操作的協調流程內的回覆主旨，以便讓使用的傳送主體做為回應？</span><span class="sxs-lookup"><span data-stu-id="650e8-121">**Question:** How does BizTalk Adapter for TIBCO Rendezvous read and manipulate the reply subject inside an orchestration so that you can use it as the send subject for the response?</span></span> <span data-ttu-id="650e8-122">配接器如何找到來自 Rendezvous 之內送訊息的訊息內容？</span><span class="sxs-lookup"><span data-stu-id="650e8-122">How does the adapter get to the message context of an incoming message from Rendezvous?</span></span>  
  
 <span data-ttu-id="650e8-123">**答：** 回覆主旨會填入內容中的內送的訊息，以及協調流程可以讀取它。</span><span class="sxs-lookup"><span data-stu-id="650e8-123">**Answer:** The reply subject is populated in the context of the incoming message, and the orchestration can read it.</span></span> <span data-ttu-id="650e8-124">如果協調流程最終會產生回覆，即可使用該值來設定回覆訊息的傳送主體。</span><span class="sxs-lookup"><span data-stu-id="650e8-124">If the orchestration ultimately produces a reply, it can use that value to set the send subject of the reply message.</span></span>  
  
1. <span data-ttu-id="650e8-125">在 BizTalk Server 專案中，新增 <install_directory>\TibcoRV\bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="650e8-125">In a BizTalk Server project, add a reference to <install_directory>\TibcoRV\bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll.</span></span>  
  
2. <span data-ttu-id="650e8-126">在協調流程中的接收圖形 (內送 Rendezvous 訊息傳入之處) 與傳送圖形 (傳送回覆之處) 之間的某處，新增訊息建構/指派圖形 (或運算式圖形)，以對您所建構的回覆執行如下列範例的作業：</span><span class="sxs-lookup"><span data-stu-id="650e8-126">In the orchestration (somewhere between the Receive shape that is handed the incoming Rendezvous message and the Send shape that is sending the reply), add a message construction/assignment shape (or an expression shape) to do something like the following example to the reply you constructed:</span></span>  
  
   ```  
   OutgoingMsg(Rendezvous.SendSubject) = IncomingMsg  
   (Rendezvous.ReplySubject);  
   ```  
   ## <a name="management-assembly"></a><span data-ttu-id="650e8-127">管理組件</span><span class="sxs-lookup"><span data-stu-id="650e8-127">Management assembly</span></span>
   <span data-ttu-id="650e8-128">TIBCO Rendezvous 未提供中繼資料儲存機制，而 Microsoft BizTalk Adapter for TIBCO Rendezvous 管理組件未提供瀏覽功能或結構描述產生功能。</span><span class="sxs-lookup"><span data-stu-id="650e8-128">TIBCO Rendezvous does not provide metadata repositories, and Microsoft BizTalk Adapter for TIBCO Rendezvous management assembly does not provide browsing capabilities or schema generation.</span></span> <span data-ttu-id="650e8-129">因此，您必須提供描述結構給 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="650e8-129">Therefore, you must provide a schema to BizTalk Server.</span></span> <span data-ttu-id="650e8-130">如需詳細資訊，請參閱 <<c0> [ 安裝、 結構描述，與限制](../core/installing-biztalk-adapter-for-tibco-rendezvous.md)。</span><span class="sxs-lookup"><span data-stu-id="650e8-130">For more information, see [Install, schemas, & limitations](../core/installing-biztalk-adapter-for-tibco-rendezvous.md).</span></span>
  
   <span data-ttu-id="650e8-131">BizTalk Adapter for TIBCO Rendezvous 含有一個具有預先定義類型的結構描述。</span><span class="sxs-lookup"><span data-stu-id="650e8-131">BizTalk Adapter for TIBCO Rendezvous includes a schema with predefined types.</span></span> <span data-ttu-id="650e8-132">針對部分特定資料類型 (陣列) 產生訊息時，配接器會使用這些類型。</span><span class="sxs-lookup"><span data-stu-id="650e8-132">The adapter uses these types when generating messages for some specific data types (arrays).</span></span>

  
## <a name="see-also"></a><span data-ttu-id="650e8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="650e8-133">See Also</span></span>  
 <span data-ttu-id="650e8-134">[TIBCO Rendezvous 中的傳送處理常式的資料類型對應](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="650e8-134">[Data Type Mapping for Send Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="650e8-135">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="650e8-135">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)
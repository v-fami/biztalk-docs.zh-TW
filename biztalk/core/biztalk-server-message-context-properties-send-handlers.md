---
title: "BizTalk Server 訊息內容屬性 （傳送處理常式） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message context properties, BizTalk Server
- reply subjects
- send handlers, BizTalk Server message context properties
- replies
ms.assetid: a065ba89-9fdb-47dc-9021-fb95cf347cdc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c8e5ddb1feb02a015fdebd62d183d1b8442fe5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-message-context-properties-send-handlers"></a><span data-ttu-id="726d1-102">BizTalk Server 訊息內容屬性 （傳送處理常式）</span><span class="sxs-lookup"><span data-stu-id="726d1-102">BizTalk Server Message Context Properties (Send Handlers)</span></span>
<span data-ttu-id="726d1-103">在執行階段，必須可從 BizTalk Server 協調流程存取的，除了有訊息內容以外，還有訊息包含的補充資訊。</span><span class="sxs-lookup"><span data-stu-id="726d1-103">In addition to the message payload, the supplementary information that a message contains must be accessible from the BizTalk Server orchestration at run time.</span></span>  
  
## <a name="tibco-rv-message-information-promoted-as-message-context-properties"></a><span data-ttu-id="726d1-104">已升級為訊息內容屬性的 TIBCO RV 訊息資訊</span><span class="sxs-lookup"><span data-stu-id="726d1-104">TIBCO RV Message Information Promoted as Message Context Properties</span></span>  
  
|<span data-ttu-id="726d1-105">資料識別</span><span class="sxs-lookup"><span data-stu-id="726d1-105">Data Identification</span></span>|<span data-ttu-id="726d1-106">型別</span><span class="sxs-lookup"><span data-stu-id="726d1-106">Type</span></span>|<span data-ttu-id="726d1-107">可路由傳送</span><span class="sxs-lookup"><span data-stu-id="726d1-107">Routable</span></span>|<span data-ttu-id="726d1-108">傳送位置</span><span class="sxs-lookup"><span data-stu-id="726d1-108">Send Location</span></span>|  
|-------------------------|----------|--------------|-------------------|  
|<span data-ttu-id="726d1-109">傳送主體</span><span class="sxs-lookup"><span data-stu-id="726d1-109">Send Subject</span></span>|<span data-ttu-id="726d1-110">string</span><span class="sxs-lookup"><span data-stu-id="726d1-110">string</span></span>|<span data-ttu-id="726d1-111">是</span><span class="sxs-lookup"><span data-stu-id="726d1-111">Yes</span></span>|<span data-ttu-id="726d1-112">協調流程會 指定 TIBCO Rendezvous 傳送主體 。</span><span class="sxs-lookup"><span data-stu-id="726d1-112">Orchestration specifies the TIBCO Rendezvous send subject.</span></span> <span data-ttu-id="726d1-113">預設值是空值。</span><span class="sxs-lookup"><span data-stu-id="726d1-113">Default value is Null.</span></span> <span data-ttu-id="726d1-114">除非連接埠組態中已指定預設主體，否則為強制性。</span><span class="sxs-lookup"><span data-stu-id="726d1-114">Mandatory unless a default subject is specified in the port configuration.</span></span>|  
|<span data-ttu-id="726d1-115">回覆主體</span><span class="sxs-lookup"><span data-stu-id="726d1-115">Reply Subject</span></span>|<span data-ttu-id="726d1-116">string</span><span class="sxs-lookup"><span data-stu-id="726d1-116">string</span></span>|<span data-ttu-id="726d1-117">是</span><span class="sxs-lookup"><span data-stu-id="726d1-117">Yes</span></span>|<span data-ttu-id="726d1-118">協調流程會 提供用於回覆訊息的相關主體 。</span><span class="sxs-lookup"><span data-stu-id="726d1-118">Orchestration provides a subject for reply messages, when pertinent.</span></span> <span data-ttu-id="726d1-119">預設值是空值。</span><span class="sxs-lookup"><span data-stu-id="726d1-119">Default value is Null.</span></span>|  
  
## <a name="getting-a-tibco-reply"></a><span data-ttu-id="726d1-120">取得 TIBCO 回覆</span><span class="sxs-lookup"><span data-stu-id="726d1-120">Getting a TIBCO Reply</span></span>  
 <span data-ttu-id="726d1-121">**問題：**如何執行 BizTalk Adapter for TIBCO Rendezvous 讀取及操作的協調流程內的回覆主旨，以便讓使用的傳送主體做為回應？</span><span class="sxs-lookup"><span data-stu-id="726d1-121">**Question:** How does BizTalk Adapter for TIBCO Rendezvous read and manipulate the reply subject inside an orchestration so that you can use it as the send subject for the response?</span></span> <span data-ttu-id="726d1-122">配接器如何找到來自 Rendezvous 之內送訊息的訊息內容？</span><span class="sxs-lookup"><span data-stu-id="726d1-122">How does the adapter get to the message context of an incoming message from Rendezvous?</span></span>  
  
 <span data-ttu-id="726d1-123">**回答：**內送訊息的內容中填入回覆主體及協調流程可以讀取它。</span><span class="sxs-lookup"><span data-stu-id="726d1-123">**Answer:** The reply subject is populated in the context of the incoming message, and the orchestration can read it.</span></span> <span data-ttu-id="726d1-124">如果協調流程最終會產生回覆，即可使用該值來設定回覆訊息的傳送主體。</span><span class="sxs-lookup"><span data-stu-id="726d1-124">If the orchestration ultimately produces a reply, it can use that value to set the send subject of the reply message.</span></span>  
  
1.  <span data-ttu-id="726d1-125">在 BizTalk Server 專案中，新增 <install_directory>\TibcoRV\bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="726d1-125">In a BizTalk Server project, add a reference to <install_directory>\TibcoRV\bin\Microsoft.BizTalk.Adapters.TibRV.Properties.dll.</span></span>  
  
2.  <span data-ttu-id="726d1-126">在協調流程中的接收圖形 (內送 Rendezvous 訊息傳入之處) 與傳送圖形 (傳送回覆之處) 之間的某處，新增訊息建構/指派圖形 (或運算式圖形)，以對您所建構的回覆執行如下列範例的作業：</span><span class="sxs-lookup"><span data-stu-id="726d1-126">In the orchestration (somewhere between the Receive shape that is handed the incoming Rendezvous message and the Send shape that is sending the reply), add a message construction/assignment shape (or an expression shape) to do something like the following example to the reply you constructed:</span></span>  
  
    ```  
    OutgoingMsg(Rendezvous.SendSubject) = IncomingMsg  
    (Rendezvous.ReplySubject);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="726d1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="726d1-127">See Also</span></span>  
 <span data-ttu-id="726d1-128">[TIBCO Rendezvous 中的傳送處理常式的資料類型對應](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="726d1-128">[Data Type Mapping for Send Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-send-handlers-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="726d1-129">建立 TIBCO Rendezvous 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="726d1-129">Creating TIBCO Rendezvous Send Handlers</span></span>](../core/creating-tibco-rendezvous-send-handlers.md)
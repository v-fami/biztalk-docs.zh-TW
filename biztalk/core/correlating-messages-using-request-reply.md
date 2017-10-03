---
title: "相互關聯使用要求-回覆訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, MQSeries adapters
- messages, correlating
- MQSeries adapters, correlating messages
ms.assetid: 4615b586-663b-41d8-949c-fefb6143c590
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2f13d8dea9192e982f597311ca3ea13fa213ed0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="correlating-messages-using-request-reply"></a><span data-ttu-id="9d2ce-102">使用要求-回應相互關聯訊息</span><span class="sxs-lookup"><span data-stu-id="9d2ce-102">Correlating Messages Using Request-Reply</span></span>
<span data-ttu-id="9d2ce-103">有兩種方式可將 IBM WebSphere MQ 的 BizTalk 協調流程中的訊息，和 Windows 平台要求-回應實例的伺服器元件中的訊息相互關聯。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-103">There are two ways to correlate messages in BizTalk orchestrations for IBM WebSphere MQ, server component for Windows platforms request-reply scenarios.</span></span> <span data-ttu-id="9d2ce-104">第一個方法是將 messageid 來提供相互關聯識別項 (**MQMD_MSGID**) 與 CorrelationID (**MQMD_CorrelId**) 為相同的值。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-104">The first is to supply the correlation identifier by setting both the MessageID (**MQMD_MSGID**) and the CorrelationID (**MQMD_CorrelId**) to the same value.</span></span> <span data-ttu-id="9d2ce-105">第二個是使用**BizTalk_CorrelationId**內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-105">The second is to use the **BizTalk_CorrelationId** context property.</span></span>  
  
## <a name="setting-mqmdmsgid-and-mqmdcorrelid-to-the-same-value"></a><span data-ttu-id="9d2ce-106">將 MQMD_MsgId 與 MQMD_CorrelId 設為相同值</span><span class="sxs-lookup"><span data-stu-id="9d2ce-106">Setting MQMD_MsgId and MQMD_CorrelId to the Same value</span></span>  
 <span data-ttu-id="9d2ce-107">將訊息傳送到 IBM WebSphere MQ Queue Manager 時，您可以設定訊息識別項 (**MQMD_MSGID**) 和相互關聯識別項 (**MQMD_CorrelId**) 為外寄訊息中相同的值.</span><span class="sxs-lookup"><span data-stu-id="9d2ce-107">When sending the message to an IBM WebSphere MQ Queue Manager, you can set the message identifier (**MQMD_MSGID**) and the correlation identifier (**MQMD_CorrelId**) to the same value in the outgoing message.</span></span> <span data-ttu-id="9d2ce-108">IBM WebSphere MQ Queue Manager 會在回覆訊息中複製 MessageID 到 CorrelationID。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-108">The IBM WebSphere MQ Queue Manager copies the MessageID to the CorrelationID for the reply message.</span></span> <span data-ttu-id="9d2ce-109">下圖顯示此程序。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-109">The following figure shows the process.</span></span>  
  
 <span data-ttu-id="9d2ce-110">![簡單相互關聯](../core/media/bts-dev-mqsimplecorrelation.gif "BTS_Dev_MQSimpleCorrelation")</span><span class="sxs-lookup"><span data-stu-id="9d2ce-110">![Simple Correlation](../core/media/bts-dev-mqsimplecorrelation.gif "BTS_Dev_MQSimpleCorrelation")</span></span>  
  
 <span data-ttu-id="9d2ce-111">您可以初始化的相互關聯集內送訊息使用的值與外寄訊息的相互關聯集**MQMD_CorrelId**。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-111">You can initialize the correlation sets for the outgoing message and follow the correlation sets for the incoming message using the value of **MQMD_CorrelId**.</span></span>  
  
## <a name="using-the-mqseriesbiztalkcorrelationid-context-property"></a><span data-ttu-id="9d2ce-112">使用 MQSeries.BizTalk_CorrelationId 內容屬性</span><span class="sxs-lookup"><span data-stu-id="9d2ce-112">Using the MQSeries.BizTalk_CorrelationId Context Property</span></span>  
 <span data-ttu-id="9d2ce-113">而不是將 MessageID 與 CorrelationID 設外寄訊息中相同的值，您可以使用**BizTalk_CorrelationID**內容屬性與請求-回應傳送埠 MQSeries 配接器。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-113">Instead of setting the MessageID and CorrelationID to the same value in the outgoing message, you can use the **BizTalk_CorrelationID** context property with a solicit-response send port of the MQSeries adapter.</span></span> <span data-ttu-id="9d2ce-114">下圖顯示這個程序。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-114">The following figure shows this process.</span></span>  
  
 <span data-ttu-id="9d2ce-115">![使用請求 &#45;若要產生的相互關聯識別碼的回應](../core/media/bts-dev-mqgeneratedcorrelation.gif "BTS_Dev_MQGeneratedCorrelation")</span><span class="sxs-lookup"><span data-stu-id="9d2ce-115">![Using Solicit&#45;Response to generate CorrelationID](../core/media/bts-dev-mqgeneratedcorrelation.gif "BTS_Dev_MQGeneratedCorrelation")</span></span>  
  
 <span data-ttu-id="9d2ce-116">若要針對 BizTalk 協調流程中的相互關聯使用 IBM WebSphere MQ Server 提供的識別項，BizTalk Server 必須先取得識別項。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-116">To use identifiers provided by IBM WebSphere MQ Server for correlations in your BizTalk orchestration, BizTalk Server must first obtain the identifier.</span></span> <span data-ttu-id="9d2ce-117">您的應用程式透過請求-回應要求執行此工作。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-117">Your application does this through a solicit-response request.</span></span> <span data-ttu-id="9d2ce-118">BizTalk Server 使用 MQSeries 配接器傳送請求-回應要求到 IBM WebSphere MQ Server。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-118">BizTalk Server sends a solicit-response request to the IBM WebSphere MQ Server by using the MQSeries adapter.</span></span> <span data-ttu-id="9d2ce-119">會接收回應的訊息識別項 (**MQMD_MSGId**) 和相互關聯識別項 (**MQMD_CorrelId**)。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-119">In return, it receives a response with the message identifier (**MQMD_MSGId**) and the correlation identifier (**MQMD_CorrelId**).</span></span>  
  
 <span data-ttu-id="9d2ce-120">請求-回應傳送埠中的外寄訊息，配接器複製**MQMD_MSGID**到 IBM WebSphere MQ server 產生**MQSeries.BizTalk_CorrelationId**內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-120">For the outgoing message in a solicit-response send port, the adapter copies the **MQMD_MSGID** generated by IBM WebSphere MQ Server to the **MQSeries.BizTalk_CorrelationId** context property.</span></span>  
  
 <span data-ttu-id="9d2ce-121">配接器接收訊息時，會複製**MQMD_CorrelId**至**MQSeries.BizTalk_CorrelationId**。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-121">When receiving messages, the adapter copies the **MQMD_CorrelId** to the **MQSeries.BizTalk_CorrelationId**.</span></span> <span data-ttu-id="9d2ce-122">在此情況下，使用相互關聯集，您可以初始化外寄訊息和相互關聯集內送訊息使用的相互關聯集**MQSeries.BizTalk_CorrelationId**。</span><span class="sxs-lookup"><span data-stu-id="9d2ce-122">In this case, using correlation sets, you can initialize the correlation sets for the outgoing message and follow the correlation sets for the incoming message using the **MQSeries.BizTalk_CorrelationId**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2ce-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d2ce-123">See Also</span></span>  
 [<span data-ttu-id="9d2ce-124">MQSCorrelationSetOrchestrationWithSolicitResponse （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="9d2ce-124">MQSCorrelationSetOrchestrationWithSolicitResponse (BizTalk Server Sample)</span></span>](../core/mqscorrelationsetorchestrationwithsolicitresponse-biztalk-server-sample.md)
---
title: 批次處理外寄 EDI 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a2bd68-4974-4927-938a-8eaf8f007566
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9f99849a812e859f527b3f39a2184508d244a29
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004455"
---
# <a name="batching-outgoing-edi-messages"></a><span data-ttu-id="ec9d2-102">批次處理外寄 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="ec9d2-102">Batching Outgoing EDI Messages</span></span>
<span data-ttu-id="ec9d2-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會批次處理 EDI 交易集，前提是已經針對與接收它之商業夥伴相關聯的協議來啟用批次處理。</span><span class="sxs-lookup"><span data-stu-id="ec9d2-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will batch EDI transaction sets if batching has been enabled for the agreement associated with the business partner that will be receiving it.</span></span> <span data-ttu-id="ec9d2-104">協議的 EDI 屬性可讓您執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ec9d2-104">The EDI properties for an agreement enable you to do the following:</span></span>  
  
- <span data-ttu-id="ec9d2-105">定義多個外寄批次</span><span class="sxs-lookup"><span data-stu-id="ec9d2-105">Define multiple outgoing batches</span></span>  
  
- <span data-ttu-id="ec9d2-106">定義交換</span><span class="sxs-lookup"><span data-stu-id="ec9d2-106">Define the interchange</span></span>  
  
- <span data-ttu-id="ec9d2-107">定義交換內的群組</span><span class="sxs-lookup"><span data-stu-id="ec9d2-107">Define the groups in the interchange</span></span>  
  
- <span data-ttu-id="ec9d2-108">設定批次釋放準則</span><span class="sxs-lookup"><span data-stu-id="ec9d2-108">Set the batch release criteria</span></span>  
  
- <span data-ttu-id="ec9d2-109">設定批次啟動準則。</span><span class="sxs-lookup"><span data-stu-id="ec9d2-109">Set the batch activation criteria.</span></span>  
  
  <span data-ttu-id="ec9d2-110">Microsoft BizTalk Server EDI 和 AS2 可處理下列 EDI 交換：</span><span class="sxs-lookup"><span data-stu-id="ec9d2-110">Microsoft BizTalk Server EDI and AS2 enables the following processing of EDI interchanges:</span></span>  
  
- <span data-ttu-id="ec9d2-111">EDI 交換可包含交易集和 (或) 通知。</span><span class="sxs-lookup"><span data-stu-id="ec9d2-111">EDI interchanges can include transaction sets and/or acknowledgments.</span></span>  
  
- <span data-ttu-id="ec9d2-112">EDI 接收管線可將交換分割成 XML 交易集以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 進一步處理，也可以保留交換，再以其所接收的格式傳送給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ec9d2-112">The EDI receive pipeline can split an interchange into XML transaction sets for further processing by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], or it can preserve the interchange, passing it through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in its received form.</span></span>  
  
- <span data-ttu-id="ec9d2-113">EDI 路由協調流程可讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將單一交易集批次處理成多個外寄交換。</span><span class="sxs-lookup"><span data-stu-id="ec9d2-113">The EDI routing orchestration enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to batch a single transaction set into more than one outgoing interchange.</span></span>  
  
- <span data-ttu-id="ec9d2-114">EDI 批次處理協調流程會將 XML 交易集組合成 EDI 交換，並根據協議的 EDI 屬性驗證和傳遞交換。</span><span class="sxs-lookup"><span data-stu-id="ec9d2-114">The EDI batching orchestration assembles XML transaction sets into an EDI interchange, and validates and delivers the interchange according to an agreement's EDI properties.</span></span>  
  
  <span data-ttu-id="ec9d2-115">EDI 批次 (稱為交換) 包含訊息群組，而訊息群組包含個別訊息。</span><span class="sxs-lookup"><span data-stu-id="ec9d2-115">EDI batches, called interchanges, contain message groups, and message groups contain individual messages.</span></span> <span data-ttu-id="ec9d2-116">外寄批次可包含多個群組，但每種文件類型只能有一個群組。</span><span class="sxs-lookup"><span data-stu-id="ec9d2-116">Outgoing batches can include multiple groups, but only one group per document type.</span></span> <span data-ttu-id="ec9d2-117">一個群組可以包含多個交易集，但每個交易集的文件類型都必須相同。</span><span class="sxs-lookup"><span data-stu-id="ec9d2-117">A group can contain multiple transaction sets, but each must have the same document type.</span></span> <span data-ttu-id="ec9d2-118">訊息信封是用來包裝個別交易集、個別群組和整個交換。</span><span class="sxs-lookup"><span data-stu-id="ec9d2-118">Message envelopes are used to wrap individual transaction sets, individual groups, and the entire interchange.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec9d2-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="ec9d2-119">In This Section</span></span>  
  
-   [<span data-ttu-id="ec9d2-120">設定外寄批次</span><span class="sxs-lookup"><span data-stu-id="ec9d2-120">Configuring an Outgoing Batch</span></span>](../core/configuring-an-outgoing-batch.md)  
  
-   [<span data-ttu-id="ec9d2-121">組合批次 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="ec9d2-121">Assembling a Batched EDI Interchange</span></span>](../core/assembling-a-batched-edi-interchange.md)  
  
-   [<span data-ttu-id="ec9d2-122">傳送保留的批次交換</span><span class="sxs-lookup"><span data-stu-id="ec9d2-122">Sending a Preserved Batch Interchange</span></span>](../core/sending-a-preserved-batch-interchange.md)
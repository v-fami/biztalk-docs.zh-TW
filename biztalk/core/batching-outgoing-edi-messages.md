---
title: 批次處理外寄 EDI 訊息 |Microsoft 文件
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
ms.openlocfilehash: 852b85e0de23e01e39891adba56053683d18a9b8
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006559"
---
# <a name="batching-outgoing-edi-messages"></a><span data-ttu-id="c208d-102">批次處理外寄 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="c208d-102">Batching Outgoing EDI Messages</span></span>
<span data-ttu-id="c208d-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會批次處理 EDI 交易集，前提是已經針對與接收它之商業夥伴相關聯的協議來啟用批次處理。</span><span class="sxs-lookup"><span data-stu-id="c208d-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will batch EDI transaction sets if batching has been enabled for the agreement associated with the business partner that will be receiving it.</span></span> <span data-ttu-id="c208d-104">協議的 EDI 屬性可讓您執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="c208d-104">The EDI properties for an agreement enable you to do the following:</span></span>  
  
-   <span data-ttu-id="c208d-105">定義多個外寄批次</span><span class="sxs-lookup"><span data-stu-id="c208d-105">Define multiple outgoing batches</span></span>  
  
-   <span data-ttu-id="c208d-106">定義交換</span><span class="sxs-lookup"><span data-stu-id="c208d-106">Define the interchange</span></span>  
  
-   <span data-ttu-id="c208d-107">定義交換內的群組</span><span class="sxs-lookup"><span data-stu-id="c208d-107">Define the groups in the interchange</span></span>  
  
-   <span data-ttu-id="c208d-108">設定批次釋放準則</span><span class="sxs-lookup"><span data-stu-id="c208d-108">Set the batch release criteria</span></span>  
  
-   <span data-ttu-id="c208d-109">設定批次啟動準則。</span><span class="sxs-lookup"><span data-stu-id="c208d-109">Set the batch activation criteria.</span></span>  
  
 <span data-ttu-id="c208d-110">Microsoft BizTalk Server EDI 和 AS2 可處理下列 EDI 交換的：</span><span class="sxs-lookup"><span data-stu-id="c208d-110">Microsoft BizTalk Server EDI and AS2 enables the following processing of EDI interchanges:</span></span>  
  
-   <span data-ttu-id="c208d-111">EDI 交換可包含交易集和 (或) 通知。</span><span class="sxs-lookup"><span data-stu-id="c208d-111">EDI interchanges can include transaction sets and/or acknowledgments.</span></span>  
  
-   <span data-ttu-id="c208d-112">EDI 接收管線可將交換分割成 XML 交易集以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 進一步處理，也可以保留交換，再以其所接收的格式傳送給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c208d-112">The EDI receive pipeline can split an interchange into XML transaction sets for further processing by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], or it can preserve the interchange, passing it through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in its received form.</span></span>  
  
-   <span data-ttu-id="c208d-113">EDI 路由協調流程可讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將單一交易集批次處理成多個外寄交換。</span><span class="sxs-lookup"><span data-stu-id="c208d-113">The EDI routing orchestration enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to batch a single transaction set into more than one outgoing interchange.</span></span>  
  
-   <span data-ttu-id="c208d-114">EDI 批次處理協調流程會將 XML 交易集組合成 EDI 交換，並根據協議的 EDI 屬性驗證和傳遞交換。</span><span class="sxs-lookup"><span data-stu-id="c208d-114">The EDI batching orchestration assembles XML transaction sets into an EDI interchange, and validates and delivers the interchange according to an agreement's EDI properties.</span></span>  
  
 <span data-ttu-id="c208d-115">EDI 批次 (稱為交換) 包含訊息群組，而訊息群組包含個別訊息。</span><span class="sxs-lookup"><span data-stu-id="c208d-115">EDI batches, called interchanges, contain message groups, and message groups contain individual messages.</span></span> <span data-ttu-id="c208d-116">外寄批次可包含多個群組，但每種文件類型只能有一個群組。</span><span class="sxs-lookup"><span data-stu-id="c208d-116">Outgoing batches can include multiple groups, but only one group per document type.</span></span> <span data-ttu-id="c208d-117">一個群組可以包含多個交易集，但每個交易集的文件類型都必須相同。</span><span class="sxs-lookup"><span data-stu-id="c208d-117">A group can contain multiple transaction sets, but each must have the same document type.</span></span> <span data-ttu-id="c208d-118">訊息信封是用來包裝個別交易集、個別群組和整個交換。</span><span class="sxs-lookup"><span data-stu-id="c208d-118">Message envelopes are used to wrap individual transaction sets, individual groups, and the entire interchange.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c208d-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="c208d-119">In This Section</span></span>  
  
-   [<span data-ttu-id="c208d-120">設定外寄批次</span><span class="sxs-lookup"><span data-stu-id="c208d-120">Configuring an Outgoing Batch</span></span>](../core/configuring-an-outgoing-batch.md)  
  
-   [<span data-ttu-id="c208d-121">組合批次 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="c208d-121">Assembling a Batched EDI Interchange</span></span>](../core/assembling-a-batched-edi-interchange.md)  
  
-   [<span data-ttu-id="c208d-122">傳送保留的批次交換</span><span class="sxs-lookup"><span data-stu-id="c208d-122">Sending a Preserved Batch Interchange</span></span>](../core/sending-a-preserved-batch-interchange.md)
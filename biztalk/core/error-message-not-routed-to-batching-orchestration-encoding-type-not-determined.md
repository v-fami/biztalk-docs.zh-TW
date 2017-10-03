---
title: "訊息無法傳送至批次處理協調流程，因為無法判斷的編碼方式類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d2ee38d-22c0-4fcf-bb68-b2ef00088c4c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe5054f53f779274c9b25f2751fdcb9d85545560
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-message-cannot-be-routed-to-the-batching-orchestration-as-the-encoding-type-could-not-be-determined"></a><span data-ttu-id="f2ee7-102">訊息無法傳送至批次處理協調流程，因為無法判斷編碼類型</span><span class="sxs-lookup"><span data-stu-id="f2ee7-102">The message cannot be routed to the batching orchestration as the Encoding type could not be determined</span></span>
## <a name="details"></a><span data-ttu-id="f2ee7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f2ee7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2ee7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f2ee7-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f2ee7-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f2ee7-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f2ee7-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f2ee7-106">Event ID</span></span>|-|  
|<span data-ttu-id="f2ee7-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f2ee7-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f2ee7-108">EDI</span><span class="sxs-lookup"><span data-stu-id="f2ee7-108"> EDI</span></span>|  
|<span data-ttu-id="f2ee7-109">元件</span><span class="sxs-lookup"><span data-stu-id="f2ee7-109">Component</span></span>|<span data-ttu-id="f2ee7-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="f2ee7-110">Batching Engine</span></span>|  
|<span data-ttu-id="f2ee7-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f2ee7-111">Symbolic Name</span></span>|<span data-ttu-id="f2ee7-112">UnknownEncodingType</span><span class="sxs-lookup"><span data-stu-id="f2ee7-112">UnknownEncodingType</span></span>|  
|<span data-ttu-id="f2ee7-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f2ee7-113">Message Text</span></span>|<span data-ttu-id="f2ee7-114">無法將訊息路由至 「 批次處理協調流程，因為無法判斷編碼類型。</span><span class="sxs-lookup"><span data-stu-id="f2ee7-114">The message cannot be routed to the batching orchestration as the Encoding type could not be determined.</span></span> <span data-ttu-id="f2ee7-115">編碼的類型必須是 X12 或 EDIFACT 批次處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="f2ee7-115">The encoding type needs to be either X12 or EDIFACT for the message to be batched.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f2ee7-116">說明</span><span class="sxs-lookup"><span data-stu-id="f2ee7-116">Explanation</span></span>  
 <span data-ttu-id="f2ee7-117">這個錯誤/警告/資訊事件表示非 EDI 批次項目已無法路由傳送至批次處理協調流程執行個體，即使交易集符合篩選準則進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="f2ee7-117">This Error/Warning/Information event indicates that a non-EDI batch element was not routed to the batching orchestration instance, even though the transaction set meets the filter criteria for batching.</span></span> <span data-ttu-id="f2ee7-118">交易集可能不會路由傳送批次處理協調流程執行個體因為 EDI。對於 EDIFACT 不 EncodingType 內容屬性升級為 0 代表 X12，1 值。</span><span class="sxs-lookup"><span data-stu-id="f2ee7-118">The transaction set could not be routed to the batching orchestration instance because the EDI.EncodingType context property was not promoted with a value of 0 for X12 or 1 for EDIFACT.</span></span> <span data-ttu-id="f2ee7-119">當批次項目已路由傳送到路由協調流程中，BatchMarker 管線元件，但非 EDI 批次項目以對應未轉換成 EDI 訊息時，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="f2ee7-119">This error occurred when the batch element was routed by the BatchMarker pipeline component to the routing orchestration, but the non-EDI batch element was not converted by a map into an EDI message.</span></span> <span data-ttu-id="f2ee7-120">如此一來，路由協調流程無法判斷 EDI 標頭的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="f2ee7-120">As a result, the routing orchestration could not determine the encoding type from the EDI headers.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f2ee7-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f2ee7-121">User Action</span></span>  
 <span data-ttu-id="f2ee7-122">若要解決這個錯誤，請確定的非 EDI 訊息對應會將轉換成 EDI 訊息傳送至路由協調流程之前。</span><span class="sxs-lookup"><span data-stu-id="f2ee7-122">To resolve this error, make sure that the non-EDI message is converted by a map into an EDI message before it is routed to the routing orchestration.</span></span> <span data-ttu-id="f2ee7-123">您也必須包含自訂管線元件 （使用 BatchMarker 元件中） 或自訂協調流程來處理非 EDI 批次項目。</span><span class="sxs-lookup"><span data-stu-id="f2ee7-123">You must also include a custom pipeline component (with the BatchMarker component) or custom orchestration to process the non-EDI batch element.</span></span> <span data-ttu-id="f2ee7-124">如需詳細資訊，請參閱 「 組合批次 EDI 交換 」 中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="f2ee7-124">For more information, see "Assembling a Batched EDI Interchange" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>
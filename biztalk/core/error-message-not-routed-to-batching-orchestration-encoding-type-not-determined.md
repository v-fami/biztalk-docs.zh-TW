---
title: 訊息無法傳送至批次處理協調流程，因為無法判斷編碼類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d2ee38d-22c0-4fcf-bb68-b2ef00088c4c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 777f23ccfc1b79e2fca4ece8e67370513723ac27
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990183"
---
# <a name="the-message-cannot-be-routed-to-the-batching-orchestration-as-the-encoding-type-could-not-be-determined"></a><span data-ttu-id="65b4e-102">訊息無法傳送至批次處理協調流程，因為無法判斷編碼類型</span><span class="sxs-lookup"><span data-stu-id="65b4e-102">The message cannot be routed to the batching orchestration as the Encoding type could not be determined</span></span>
## <a name="details"></a><span data-ttu-id="65b4e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="65b4e-103">Details</span></span>  
  
|                 |                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="65b4e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="65b4e-104">Product Name</span></span>   |                                                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                      |
| <span data-ttu-id="65b4e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="65b4e-105">Product Version</span></span> |                                                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                  |
|    <span data-ttu-id="65b4e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="65b4e-106">Event ID</span></span>     |                                                                                              -                                                                                              |
|  <span data-ttu-id="65b4e-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="65b4e-107">Event Source</span></span>   |                                                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="65b4e-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="65b4e-108"> EDI</span></span>                                                    |
|    <span data-ttu-id="65b4e-109">元件</span><span class="sxs-lookup"><span data-stu-id="65b4e-109">Component</span></span>    |                                                                                       <span data-ttu-id="65b4e-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="65b4e-110">Batching Engine</span></span>                                                                                       |
|  <span data-ttu-id="65b4e-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="65b4e-111">Symbolic Name</span></span>  |                                                                                     <span data-ttu-id="65b4e-112">UnknownEncodingType</span><span class="sxs-lookup"><span data-stu-id="65b4e-112">UnknownEncodingType</span></span>                                                                                     |
|  <span data-ttu-id="65b4e-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="65b4e-113">Message Text</span></span>   | <span data-ttu-id="65b4e-114">訊息無法路由傳送到批次處理協調流程，因為無法判斷編碼類型。</span><span class="sxs-lookup"><span data-stu-id="65b4e-114">The message cannot be routed to the batching orchestration as the Encoding type could not be determined.</span></span> <span data-ttu-id="65b4e-115">編碼類型必須是 X12 或 EDIFACT 批次處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="65b4e-115">The encoding type needs to be either X12 or EDIFACT for the message to be batched.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="65b4e-116">說明</span><span class="sxs-lookup"><span data-stu-id="65b4e-116">Explanation</span></span>  
 <span data-ttu-id="65b4e-117">這個錯誤/警告/資訊事件表示非 EDI 批次元素已無法路由傳送到批次處理協調流程執行個體，即使交易集符合篩選準則進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="65b4e-117">This Error/Warning/Information event indicates that a non-EDI batch element was not routed to the batching orchestration instance, even though the transaction set meets the filter criteria for batching.</span></span> <span data-ttu-id="65b4e-118">交易集無法路由，批次處理協調流程執行個體因為 EDI。對於 EDIFACT 不 EncodingType 內容屬性升級為 X12 或 1 的 0 值。</span><span class="sxs-lookup"><span data-stu-id="65b4e-118">The transaction set could not be routed to the batching orchestration instance because the EDI.EncodingType context property was not promoted with a value of 0 for X12 or 1 for EDIFACT.</span></span> <span data-ttu-id="65b4e-119">當批次元素已路由傳送到路由協調流程中，BatchMarker 管線元件，但非 EDI 批次項目所對應並未轉換成 EDI 訊息時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="65b4e-119">This error occurred when the batch element was routed by the BatchMarker pipeline component to the routing orchestration, but the non-EDI batch element was not converted by a map into an EDI message.</span></span> <span data-ttu-id="65b4e-120">如此一來，路由協調流程無法判斷 EDI 標頭的編碼類型。</span><span class="sxs-lookup"><span data-stu-id="65b4e-120">As a result, the routing orchestration could not determine the encoding type from the EDI headers.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="65b4e-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="65b4e-121">User Action</span></span>  
 <span data-ttu-id="65b4e-122">若要解決這個錯誤，請確定非 EDI 訊息的對應來轉換成 EDI 訊息之前它會路由至路由協調流程。</span><span class="sxs-lookup"><span data-stu-id="65b4e-122">To resolve this error, make sure that the non-EDI message is converted by a map into an EDI message before it is routed to the routing orchestration.</span></span> <span data-ttu-id="65b4e-123">您也必須包含自訂管線元件 （使用 BatchMarker 元件中） 或自訂協調流程來處理非 EDI 批次項目。</span><span class="sxs-lookup"><span data-stu-id="65b4e-123">You must also include a custom pipeline component (with the BatchMarker component) or custom orchestration to process the non-EDI batch element.</span></span> <span data-ttu-id="65b4e-124">如需詳細資訊，請參閱 「 組合批次 EDI 交換 」，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="65b4e-124">For more information, see "Assembling a Batched EDI Interchange" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>
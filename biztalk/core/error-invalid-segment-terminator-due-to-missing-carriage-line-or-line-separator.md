---
title: 交換發生結構錯誤。 可能的原因是因為遺失歸位無效的區段結束字元和-或換行字元分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 035e37d5-d4a8-49d0-8d75-3bcf2426cac7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e1d3c90d69b3e482ac570538f5dcc6997a63aea
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988767"
---
# <a name="the-interchange-had-structural-error-a-likely-cause-is-invalid-segment-terminator-due-to-missing-carriage-line-and-or-line-feed-seperators"></a><span data-ttu-id="1bf04-103">交換發生結構錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bf04-103">The interchange had structural error.</span></span> <span data-ttu-id="1bf04-104">可能的原因是因為遺失歸位無效的區段結束字元和-或換行字元分隔符號</span><span class="sxs-lookup"><span data-stu-id="1bf04-104">A likely cause is invalid segment terminator due to missing Carriage Line and-or Line Feed seperators</span></span>
## <a name="details"></a><span data-ttu-id="1bf04-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1bf04-105">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="1bf04-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1bf04-106">Product Name</span></span>   |                                                                                                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                                   |
| <span data-ttu-id="1bf04-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="1bf04-107">Product Version</span></span> |                                                                                                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                                                               |
|    <span data-ttu-id="1bf04-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1bf04-108">Event ID</span></span>     |                                                                                                                                           -                                                                                                                                           |
|  <span data-ttu-id="1bf04-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="1bf04-109">Event Source</span></span>   |                                                                                                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1bf04-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="1bf04-110"> EDI</span></span>                                                                                                 |
|    <span data-ttu-id="1bf04-111">元件</span><span class="sxs-lookup"><span data-stu-id="1bf04-111">Component</span></span>    |                                                                                                                                      <span data-ttu-id="1bf04-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="1bf04-112">EDI Engine</span></span>                                                                                                                                       |
|  <span data-ttu-id="1bf04-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1bf04-113">Symbolic Name</span></span>  |                                                                                                                        <span data-ttu-id="1bf04-114">EfactInterchangeStructuralErrorAfterUnb</span><span class="sxs-lookup"><span data-stu-id="1bf04-114">EfactInterchangeStructuralErrorAfterUnb</span></span>                                                                                                                        |
|  <span data-ttu-id="1bf04-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1bf04-115">Message Text</span></span>   | <span data-ttu-id="1bf04-116">交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 發生結構錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bf04-116">The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error.</span></span> <span data-ttu-id="1bf04-117">可能的原因是因為遺失歸位/換行字元或分隔符號的無效的區段結束字元。</span><span class="sxs-lookup"><span data-stu-id="1bf04-117">A likely cause is invalid segment terminator due to missing Carriage Line and/or Line Feed seperators.</span></span> <span data-ttu-id="1bf04-118">錯誤後的部分已遭到擱置，請參閱擱置佇列，以取得詳細資料</span><span class="sxs-lookup"><span data-stu-id="1bf04-118">The part after the error is being suspended, refer to Suspended Queue for details</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="1bf04-119">說明</span><span class="sxs-lookup"><span data-stu-id="1bf04-119">Explanation</span></span>  
 <span data-ttu-id="1bf04-120">這個錯誤/警告/資訊事件表示接收管線，而傳送管線 」 或 「 批次處理協調流程無法處理 EDIFACT 交換，因為在交換中的線段沒有必要的區段結束字元。</span><span class="sxs-lookup"><span data-stu-id="1bf04-120">This Error/Warning/Information event indicates that the receive pipeline, send pipeline, or batching orchestration could not process the EDIFACT interchange, because a segment in the interchange did not have the required segment terminator.</span></span> <span data-ttu-id="1bf04-121">內送的交換，在 UNA 區段中，找到分隔符號或 UNA 區段不存在，如果 EfactDelimiters 管線屬性。</span><span class="sxs-lookup"><span data-stu-id="1bf04-121">For an incoming interchange, the separators are identified in the UNA Segment, or if the UNA segment is not present, the EfactDelimiters pipeline property.</span></span> <span data-ttu-id="1bf04-122">針對外寄交換的 [EDI 屬性] 對話方塊中的 [UNA 區段定義] 頁面中所識別的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="1bf04-122">For an outgoing interchange, the separators are identified in the UNA Segment Definition page of the EDI Properties dialog box.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1bf04-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1bf04-123">User Action</span></span>  
 <span data-ttu-id="1bf04-124">若要解決這個錯誤，確定交換中的所有區段具有必要的區段結束字元，就會重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="1bf04-124">To resolve this error, ensure that all segments in the interchange have the required segment terminator, and then have the interchange resent.</span></span>
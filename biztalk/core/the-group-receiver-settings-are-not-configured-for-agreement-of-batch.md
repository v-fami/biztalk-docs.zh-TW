---
title: 未針對批次協議設定群組接收者設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57b205e9-aaab-43d1-b373-17d206957814
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 534d426d192e27bbe7c6c7e866399b42360a8e3a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990639"
---
# <a name="the-group-receiver-settings-are-not-configured-for-agreement-of-batch"></a><span data-ttu-id="a4fbf-102">未針對批次協議設定群組接收者設定</span><span class="sxs-lookup"><span data-stu-id="a4fbf-102">The group receiver settings are not configured for agreement of batch</span></span>
## <a name="details"></a><span data-ttu-id="a4fbf-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a4fbf-103">Details</span></span>  
  
|                 |                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="a4fbf-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a4fbf-104">Product Name</span></span>   |                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                          |
| <span data-ttu-id="a4fbf-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a4fbf-105">Product Version</span></span> |                                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                      |
|    <span data-ttu-id="a4fbf-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4fbf-106">Event ID</span></span>     |                                                                  -                                                                  |
|  <span data-ttu-id="a4fbf-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="a4fbf-107">Event Source</span></span>   |                       [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a4fbf-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a4fbf-108"> EDI</span></span>                        |
|    <span data-ttu-id="a4fbf-109">元件</span><span class="sxs-lookup"><span data-stu-id="a4fbf-109">Component</span></span>    |                                                           <span data-ttu-id="a4fbf-110">批次引擎</span><span class="sxs-lookup"><span data-stu-id="a4fbf-110">Batching Engine</span></span>                                                           |
|  <span data-ttu-id="a4fbf-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a4fbf-111">Symbolic Name</span></span>  |                                                      <span data-ttu-id="a4fbf-112">GroupReceiverNotSelected</span><span class="sxs-lookup"><span data-stu-id="a4fbf-112">GroupReceiverNotSelected</span></span>                                                       |
|  <span data-ttu-id="a4fbf-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a4fbf-113">Message Text</span></span>   | <span data-ttu-id="a4fbf-114">未針對批次協議設定群組接收者設定{0}。</span><span class="sxs-lookup"><span data-stu-id="a4fbf-114">The group receiver settings are not configured for agreement of batch {0}.</span></span> <span data-ttu-id="a4fbf-115">這需要設定，才能進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="a4fbf-115">This needs to be configured before batching can proceed.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="a4fbf-116">說明</span><span class="sxs-lookup"><span data-stu-id="a4fbf-116">Explanation</span></span>  
 <span data-ttu-id="a4fbf-117">這個錯誤/警告/資訊事件表示已發生兩個條件之一：</span><span class="sxs-lookup"><span data-stu-id="a4fbf-117">This Error/Warning/Information event indicates that one of two conditions has occurred:</span></span>  
  
-   <span data-ttu-id="a4fbf-118">批次處理協調流程無法驗證，因為未設定 [UNB1.1] 欄位 （適用於 EDIFACT 編碼交換），其中包含編碼的語法已收到的批次項目。</span><span class="sxs-lookup"><span data-stu-id="a4fbf-118">The batching orchestration could not validate a batch element that it has received because the UNB1.1 field (for an EDIFACT-encoded interchange) that contains the encoding syntax was not set.</span></span>  
  
-   <span data-ttu-id="a4fbf-119">批次處理協調流程無法建立批次元素的信封設定，因為尚未完成的標頭屬性 (針對 X12 的 ISA、 GS 和 ST 屬性交換] 或 [EDIFACT 交換的 UNA、 UNB、 UNG 和 UNH 屬性)。</span><span class="sxs-lookup"><span data-stu-id="a4fbf-119">The batching orchestration could not create the envelope settings for the batch element because the header properties were not complete (ISA, GS, and ST properties for an X12 interchange or UNA, UNB, UNG, and UNH properties for an EDIFACT interchange).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a4fbf-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a4fbf-120">User Action</span></span>  
 <span data-ttu-id="a4fbf-121">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a4fbf-121">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="a4fbf-122">如果批次處理協調流程無法驗證，因為未設定編碼的語法已收到的批次項目，設定 [UNB1.1] 欄位的編碼語法中的 [EDI 屬性] 對話方塊中的 [UNB 區段定義] 頁面。</span><span class="sxs-lookup"><span data-stu-id="a4fbf-122">If the batching orchestration could not validate a batch element that it has received because the encoding syntax was not set, set the encoding syntax for the UNB1.1 field in the UNB Segment Definition page of the EDI Properties dialog box.</span></span>  
  
-   <span data-ttu-id="a4fbf-123">如果批次處理協調流程無法建立批次元素的信封設定，因為尚未完成的標頭屬性，確定交換是的 X12 的 ISA、 GS 和 ST 屬性設定或 UNA、 UNB、 UNG 和 UNH 屬性設定 EDIFACT 交換。</span><span class="sxs-lookup"><span data-stu-id="a4fbf-123">If the batching orchestration could not create the envelope settings for the batch element because the header properties were not complete, ensure that the ISA, GS, and ST properties for an X12 interchange are set or that the UNA, UNB, UNG, and UNH properties for an EDIFACT interchange are set.</span></span>
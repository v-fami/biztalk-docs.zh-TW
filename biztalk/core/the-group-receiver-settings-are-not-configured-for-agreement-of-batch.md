---
title: 群組接收者設定未批次的協議設定 |Microsoft 文件
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
ms.openlocfilehash: 8ea41ad5c8de88e446a86745b57ff282d5b90af5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279070"
---
# <a name="the-group-receiver-settings-are-not-configured-for-agreement-of-batch"></a><span data-ttu-id="75cf3-102">群組接收者設定未批次的協議設定</span><span class="sxs-lookup"><span data-stu-id="75cf3-102">The group receiver settings are not configured for agreement of batch</span></span>
## <a name="details"></a><span data-ttu-id="75cf3-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="75cf3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75cf3-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="75cf3-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="75cf3-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="75cf3-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="75cf3-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="75cf3-106">Event ID</span></span>|-|  
|<span data-ttu-id="75cf3-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="75cf3-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="75cf3-108">EDI</span><span class="sxs-lookup"><span data-stu-id="75cf3-108"> EDI</span></span>|  
|<span data-ttu-id="75cf3-109">元件</span><span class="sxs-lookup"><span data-stu-id="75cf3-109">Component</span></span>|<span data-ttu-id="75cf3-110">批次處理引擎</span><span class="sxs-lookup"><span data-stu-id="75cf3-110">Batching Engine</span></span>|  
|<span data-ttu-id="75cf3-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="75cf3-111">Symbolic Name</span></span>|<span data-ttu-id="75cf3-112">GroupReceiverNotSelected</span><span class="sxs-lookup"><span data-stu-id="75cf3-112">GroupReceiverNotSelected</span></span>|  
|<span data-ttu-id="75cf3-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="75cf3-113">Message Text</span></span>|<span data-ttu-id="75cf3-114">群組接收者設定未批次 {0} 的協議設定。</span><span class="sxs-lookup"><span data-stu-id="75cf3-114">The group receiver settings are not configured for agreement of batch {0}.</span></span> <span data-ttu-id="75cf3-115">這必須設定批次處理才能繼續。</span><span class="sxs-lookup"><span data-stu-id="75cf3-115">This needs to be configured before batching can proceed.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="75cf3-116">說明</span><span class="sxs-lookup"><span data-stu-id="75cf3-116">Explanation</span></span>  
 <span data-ttu-id="75cf3-117">這個錯誤/警告/資訊事件表示已發生兩個條件的其中一個：</span><span class="sxs-lookup"><span data-stu-id="75cf3-117">This Error/Warning/Information event indicates that one of two conditions has occurred:</span></span>  
  
-   <span data-ttu-id="75cf3-118">批次處理協調流程無法驗證因為沒有設定 UNB1.1 欄位 （適用於 EDIFACT 編碼交換），其中包含編碼的語法已收到的批次項目。</span><span class="sxs-lookup"><span data-stu-id="75cf3-118">The batching orchestration could not validate a batch element that it has received because the UNB1.1 field (for an EDIFACT-encoded interchange) that contains the encoding syntax was not set.</span></span>  
  
-   <span data-ttu-id="75cf3-119">批次處理協調流程無法建立批次項目的信封設定值，因為未完成的標頭屬性 (x12 的 ISA、 GS 和 ST 屬性交換] 或 [EDIFACT 交換的 UNA、 UNB、 UNG 和 UNH 屬性)。</span><span class="sxs-lookup"><span data-stu-id="75cf3-119">The batching orchestration could not create the envelope settings for the batch element because the header properties were not complete (ISA, GS, and ST properties for an X12 interchange or UNA, UNB, UNG, and UNH properties for an EDIFACT interchange).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="75cf3-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="75cf3-120">User Action</span></span>  
 <span data-ttu-id="75cf3-121">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="75cf3-121">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="75cf3-122">如果批次處理協調流程無法驗證，因為沒有設定編碼的語法已收到的批次項目，UNB1.1 欄位的編碼語法中設定 EDI 屬性 對話方塊的 UNB 區段定義 頁面。</span><span class="sxs-lookup"><span data-stu-id="75cf3-122">If the batching orchestration could not validate a batch element that it has received because the encoding syntax was not set, set the encoding syntax for the UNB1.1 field in the UNB Segment Definition page of the EDI Properties dialog box.</span></span>  
  
-   <span data-ttu-id="75cf3-123">如果批次處理協調流程無法建立批次項目的信封設定值，因為未完成的標頭屬性，確定交換是的 X12 的 ISA、 GS 和 ST 屬性設定或 UNA、 UNB、 UNG 和 UNH 屬性設定 EDIFACT 交換。</span><span class="sxs-lookup"><span data-stu-id="75cf3-123">If the batching orchestration could not create the envelope settings for the batch element because the header properties were not complete, ensure that the ISA, GS, and ST properties for an X12 interchange are set or that the UNA, UNB, UNG, and UNH properties for an EDIFACT interchange are set.</span></span>
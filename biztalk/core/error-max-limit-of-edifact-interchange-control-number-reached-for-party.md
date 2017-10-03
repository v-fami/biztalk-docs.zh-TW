---
title: "合作對象已達到可接受 Edifact 交換控制編號的最高上限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c00c357-4c7b-42ea-a031-15bad0195a75
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fdb92781d137f57a09ce8c45693c2928646af24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-interchange-control-number-has-reached-for-party"></a><span data-ttu-id="386f5-102">合作對象已達到可接受 Edifact 交換控制編號的最高上限</span><span class="sxs-lookup"><span data-stu-id="386f5-102">Max limit of acceptable Edifact interchange control number has reached for party</span></span>
## <a name="details"></a><span data-ttu-id="386f5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="386f5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="386f5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="386f5-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="386f5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="386f5-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="386f5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="386f5-106">Event ID</span></span>|-|  
|<span data-ttu-id="386f5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="386f5-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="386f5-108">EDI</span><span class="sxs-lookup"><span data-stu-id="386f5-108"> EDI</span></span>|  
|<span data-ttu-id="386f5-109">元件</span><span class="sxs-lookup"><span data-stu-id="386f5-109">Component</span></span>|<span data-ttu-id="386f5-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="386f5-110">EDI Engine</span></span>|  
|<span data-ttu-id="386f5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="386f5-111">Symbolic Name</span></span>|<span data-ttu-id="386f5-112">PartyEdifactUnbNumberError</span><span class="sxs-lookup"><span data-stu-id="386f5-112">PartyEdifactUnbNumberError</span></span>|  
|<span data-ttu-id="386f5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="386f5-113">Message Text</span></span>|<span data-ttu-id="386f5-114">合作對象 {0}，已達到可接受 Edifact 交換控制編號的最高上限。</span><span class="sxs-lookup"><span data-stu-id="386f5-114">Max limit of acceptable Edifact interchange control number has reached for party {0}.</span></span> <span data-ttu-id="386f5-115">瀏覽至合作對象中接收者角色畫面，欄位 UNB 5 在夥伴協議管理員 中，重設計數器</span><span class="sxs-lookup"><span data-stu-id="386f5-115">Reset counter by navigating to Party in receiver role screen, field UNB 5 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="386f5-116">說明</span><span class="sxs-lookup"><span data-stu-id="386f5-116">Explanation</span></span>  
 <span data-ttu-id="386f5-117">這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄交換的交換控制編號，指定在合作對象設定中，特別是參考編號欄位 UNB5.2 中的 UNB5 欄位中，因此大於允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="386f5-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing interchange because the interchange control number in the UNB5 field specified in the party settings, specifically the reference number in field UNB5.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="386f5-118">交換控制編號允許的最大值取決於 UNB5 中三個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="386f5-118">The maximum allowable value for the interchange control number depends upon the values of the three fields in UNB5.</span></span> <span data-ttu-id="386f5-119">字元數上限為 14 個欄位 UNB5.2，13 for UNB5.1 中的前置詞和 13 for UNB5.3，在後置詞結合的所有三個欄位 14 中的參考編號。</span><span class="sxs-lookup"><span data-stu-id="386f5-119">The maximum number of characters is 14 for the reference number in field UNB5.2, 13 for the prefix in UNB5.1 and 13 for the suffix in UNB5.3, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="386f5-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="386f5-120">User Action</span></span>  
 <span data-ttu-id="386f5-121">若要解決這個錯誤，重設的交換控制編號，參考編號欄位 (UNB5.2)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="386f5-121">To resolve this error, reset the reference number field (UNB5.2) of the interchange control number, as follows:</span></span>  
  
1.  <span data-ttu-id="386f5-122">在 EDI 屬性 對話方塊中的 合作對象的交換解析，開啟做為交換接收者的合作對象的 UNB 區段定義 頁面。</span><span class="sxs-lookup"><span data-stu-id="386f5-122">In the EDI Properties dialog box for the party resolved for the interchange, open the UNB Segment Definition page for the party as interchange receiver.</span></span>  
  
2.  <span data-ttu-id="386f5-123">按一下 UNB5 欄位相關聯的編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="386f5-123">Click the Edit field associated with the UNB5 field.</span></span>  
  
3.  <span data-ttu-id="386f5-124">新的值設定交換控制編號 （UNB5.2 中的參考編號） 的中間欄位的欄位具有可接受數。</span><span class="sxs-lookup"><span data-stu-id="386f5-124">Set the middle field of the interchange control number (the reference number in UNB5.2) to a new value such that the field has an acceptable number of digits.</span></span>
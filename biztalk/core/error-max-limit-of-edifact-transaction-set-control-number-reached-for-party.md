---
title: "可接受 Edifact 交易集控制編號已達到合作對象的最高上限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a64cc5d3-a845-4044-9c6e-879ecda15fce
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcbd2ce29ddeb99ba8c06e5dac9ff01be8c300b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-transaction-set-control-number-has-reached-for-party"></a><span data-ttu-id="e3fc2-102">合作對象的 Edifact 交易集控制編號已達到可接受的最高上限</span><span class="sxs-lookup"><span data-stu-id="e3fc2-102">Max limit of acceptable Edifact transaction set control number has reached for party</span></span>
## <a name="details"></a><span data-ttu-id="e3fc2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e3fc2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3fc2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e3fc2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e3fc2-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e3fc2-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="e3fc2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e3fc2-106">Event ID</span></span>|-|  
|<span data-ttu-id="e3fc2-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e3fc2-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e3fc2-108">EDI</span><span class="sxs-lookup"><span data-stu-id="e3fc2-108"> EDI</span></span>|  
|<span data-ttu-id="e3fc2-109">元件</span><span class="sxs-lookup"><span data-stu-id="e3fc2-109">Component</span></span>|<span data-ttu-id="e3fc2-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e3fc2-110">EDI Engine</span></span>|  
|<span data-ttu-id="e3fc2-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e3fc2-111">Symbolic Name</span></span>|<span data-ttu-id="e3fc2-112">GlobalEdifactUnhNumberError</span><span class="sxs-lookup"><span data-stu-id="e3fc2-112">GlobalEdifactUnhNumberError</span></span>|  
|<span data-ttu-id="e3fc2-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e3fc2-113">Message Text</span></span>|<span data-ttu-id="e3fc2-114">合作對象 {0} 的 Edifact 交易集控制編號已達到可接受的最高上限。</span><span class="sxs-lookup"><span data-stu-id="e3fc2-114">Max limit of acceptable Edifact transaction set control number has reached for party {0}.</span></span> <span data-ttu-id="e3fc2-115">請瀏覽至 [夥伴協議] 管理員中接收者角色畫面中的 [合作對象]，欄位 [UNH 1]，重設計數器</span><span class="sxs-lookup"><span data-stu-id="e3fc2-115">Reset counter by navigating to Party in receiver role screen, field UNH 1 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e3fc2-116">說明</span><span class="sxs-lookup"><span data-stu-id="e3fc2-116">Explanation</span></span>  
 <span data-ttu-id="e3fc2-117">這個錯誤/警告/資訊事件表示傳送管線無法處理外寄交換，因為合作對象設定中指定之 UNH1 欄位的交易集控制編號，特別是欄位 UNH1.2 中的參考編號，大於允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="e3fc2-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing interchange because the transaction set control number in the UNH1 field specified in the party settings, specifically the reference number in field UNH1.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="e3fc2-118">交易集控制編號允許的最大值取決於 UNH1 中三個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="e3fc2-118">The maximum allowable value for the transaction set control number depends upon the values of the three fields in UNH1.</span></span> <span data-ttu-id="e3fc2-119">最大字元數是參考編號欄位 UNH1.2，13 for UNH1.1 中的前置詞和 13 for UNH1.3，在後置詞結合的所有三個欄位 14 中 14。</span><span class="sxs-lookup"><span data-stu-id="e3fc2-119">The maximum number of characters is 14 for the reference number in field UNH1.2, 13 for the prefix in UNH1.1 and 13 for the suffix in UNH1.3, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e3fc2-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e3fc2-120">User Action</span></span>  
 <span data-ttu-id="e3fc2-121">若要解決這個錯誤，重設的交易集控制編號，參考編號欄位 (UNH1.2)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e3fc2-121">To resolve this error, reset the reference number field (UNH1.2) of the transaction set control number, as follows:</span></span>  
  
1.  <span data-ttu-id="e3fc2-122">在 EDI 屬性 對話方塊中的 合作對象的交換解析，開啟 UNG 和 UNH 區段定義頁面。</span><span class="sxs-lookup"><span data-stu-id="e3fc2-122">In the EDI Properties dialog box for the party resolved for the interchange, open the UNG and UNH Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="e3fc2-123">按一下 UNH1 欄位相關聯的編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="e3fc2-123">Click the Edit field associated with the UNH1 field.</span></span>  
  
3.  <span data-ttu-id="e3fc2-124">新的值設定交易集控制編號 （UNH1.2 中的參考編號） 的中間欄位的欄位具有可接受數。</span><span class="sxs-lookup"><span data-stu-id="e3fc2-124">Set the middle field of the transaction set control number (the reference number in UNH1.2) to a new value such that the field has an acceptable number of digits.</span></span>
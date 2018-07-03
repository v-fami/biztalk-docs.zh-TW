---
title: 可接受 Edifact 交易集控制編號已達到合作對象的最高上限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a64cc5d3-a845-4044-9c6e-879ecda15fce
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85fd53beb1484d1e9ffbddf1bbc4f4ac69ae1e67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004535"
---
# <a name="max-limit-of-acceptable-edifact-transaction-set-control-number-has-reached-for-party"></a><span data-ttu-id="8fc93-102">合作對象的 Edifact 交易集控制編號已達到可接受的最高上限</span><span class="sxs-lookup"><span data-stu-id="8fc93-102">Max limit of acceptable Edifact transaction set control number has reached for party</span></span>
## <a name="details"></a><span data-ttu-id="8fc93-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8fc93-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="8fc93-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8fc93-104">Product Name</span></span>   |                                                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                        |
| <span data-ttu-id="8fc93-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="8fc93-105">Product Version</span></span> |                                                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                    |
|    <span data-ttu-id="8fc93-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8fc93-106">Event ID</span></span>     |                                                                                                -                                                                                                 |
|  <span data-ttu-id="8fc93-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="8fc93-107">Event Source</span></span>   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8fc93-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="8fc93-108"> EDI</span></span>                                                      |
|    <span data-ttu-id="8fc93-109">元件</span><span class="sxs-lookup"><span data-stu-id="8fc93-109">Component</span></span>    |                                                                                            <span data-ttu-id="8fc93-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="8fc93-110">EDI Engine</span></span>                                                                                            |
|  <span data-ttu-id="8fc93-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8fc93-111">Symbolic Name</span></span>  |                                                                                   <span data-ttu-id="8fc93-112">GlobalEdifactUnhNumberError</span><span class="sxs-lookup"><span data-stu-id="8fc93-112">GlobalEdifactUnhNumberError</span></span>                                                                                    |
|  <span data-ttu-id="8fc93-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8fc93-113">Message Text</span></span>   | <span data-ttu-id="8fc93-114">可接受 Edifact 交易集控制編號已達到合作對象的最高上限{0}。</span><span class="sxs-lookup"><span data-stu-id="8fc93-114">Max limit of acceptable Edifact transaction set control number has reached for party {0}.</span></span> <span data-ttu-id="8fc93-115">請瀏覽至 [夥伴協議] 管理員中接收者角色畫面中的 [合作對象]，欄位 [UNH 1]，重設計數器</span><span class="sxs-lookup"><span data-stu-id="8fc93-115">Reset counter by navigating to Party in receiver role screen, field UNH 1 in Partner Agreement manager</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="8fc93-116">說明</span><span class="sxs-lookup"><span data-stu-id="8fc93-116">Explanation</span></span>  
 <span data-ttu-id="8fc93-117">這個錯誤/警告/資訊事件表示傳送管線無法處理外寄交換，因為合作對象設定中指定之 UNH1 欄位的交易集控制編號，特別是欄位 UNH1.2 中的參考編號，大於允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="8fc93-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing interchange because the transaction set control number in the UNH1 field specified in the party settings, specifically the reference number in field UNH1.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="8fc93-118">交易集控制編號允許的最大值取決於 UNH1 中三個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="8fc93-118">The maximum allowable value for the transaction set control number depends upon the values of the three fields in UNH1.</span></span> <span data-ttu-id="8fc93-119">字元數上限為 14 個欄位 UNH1.2，13 個 UNH1.1 中的前置詞和 UNH1.3，在後置詞的 13 和 14 個結合的所有三個欄位中的參考編號。</span><span class="sxs-lookup"><span data-stu-id="8fc93-119">The maximum number of characters is 14 for the reference number in field UNH1.2, 13 for the prefix in UNH1.1 and 13 for the suffix in UNH1.3, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8fc93-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8fc93-120">User Action</span></span>  
 <span data-ttu-id="8fc93-121">若要解決這個錯誤，重設的交易集控制編號，參考編號欄位 (UNH1.2)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8fc93-121">To resolve this error, reset the reference number field (UNH1.2) of the transaction set control number, as follows:</span></span>  
  
1.  <span data-ttu-id="8fc93-122">在 EDI 屬性 對話方塊中的 合作對象的交換解析，開啟 UNG 和 UNH 區段定義頁面。</span><span class="sxs-lookup"><span data-stu-id="8fc93-122">In the EDI Properties dialog box for the party resolved for the interchange, open the UNG and UNH Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="8fc93-123">按一下 [UNH1] 欄位相關聯的編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="8fc93-123">Click the Edit field associated with the UNH1 field.</span></span>  
  
3.  <span data-ttu-id="8fc93-124">新的值設定交易集控制編號 （UNH1.2 中的參考編號） 的中間欄位的欄位具有一個可接受的數字。</span><span class="sxs-lookup"><span data-stu-id="8fc93-124">Set the middle field of the transaction set control number (the reference number in UNH1.2) to a new value such that the field has an acceptable number of digits.</span></span>
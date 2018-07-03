---
title: Guest 設定的已達到可接受的 Edifact 功能群組控制編號的最高上限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93ea1bd6-8c39-4d11-81a5-75d4a861e041
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 533f1067effa99f4152c908c70adf16eeb067c7f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010447"
---
# <a name="max-limit-of-acceptable-edifact-functional-group-control-number-has-reached-for-guest-settings"></a><span data-ttu-id="a4aba-102">Guest 設定的 Edifact 功能群組控制編號已達到可接受的最高上限</span><span class="sxs-lookup"><span data-stu-id="a4aba-102">Max limit of acceptable Edifact functional group control number has reached for Guest settings</span></span>
## <a name="details"></a><span data-ttu-id="a4aba-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a4aba-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="a4aba-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a4aba-104">Product Name</span></span>   |                                                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                 |
| <span data-ttu-id="a4aba-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a4aba-105">Product Version</span></span> |                                                                             [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                             |
|    <span data-ttu-id="a4aba-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a4aba-106">Event ID</span></span>     |                                                                                                         -                                                                                                          |
|  <span data-ttu-id="a4aba-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="a4aba-107">Event Source</span></span>   |                                                               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a4aba-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a4aba-108"> EDI</span></span>                                                               |
|    <span data-ttu-id="a4aba-109">元件</span><span class="sxs-lookup"><span data-stu-id="a4aba-109">Component</span></span>    |                                                                                                     <span data-ttu-id="a4aba-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="a4aba-110">EDI Engine</span></span>                                                                                                     |
|  <span data-ttu-id="a4aba-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a4aba-111">Symbolic Name</span></span>  |                                                                                            <span data-ttu-id="a4aba-112">GlobalEdifactUngNumberError</span><span class="sxs-lookup"><span data-stu-id="a4aba-112">GlobalEdifactUngNumberError</span></span>                                                                                             |
|  <span data-ttu-id="a4aba-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a4aba-113">Message Text</span></span>   | <span data-ttu-id="a4aba-114">Guest 設定的 Edifact 功能群組控制編號已達到可接受的最高上限。</span><span class="sxs-lookup"><span data-stu-id="a4aba-114">Max limit of acceptable Edifact functional group control number has reached for Guest settings.</span></span> <span data-ttu-id="a4aba-115">請瀏覽到全域組態 receiver 角色畫面中，夥伴協議管理員的 [UNG 5] 欄位，以重設計數器</span><span class="sxs-lookup"><span data-stu-id="a4aba-115">Reset counter by navigating to Global configuration receiver role screen, field UNG 5 in Partner Agreement manager</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="a4aba-116">說明</span><span class="sxs-lookup"><span data-stu-id="a4aba-116">Explanation</span></span>  
 <span data-ttu-id="a4aba-117">這個錯誤/警告/資訊事件表示傳送管線無法處理外寄交換，因為全域設定中指定之 UGN5 欄位的群組控制編號，特別是欄位 UNG5.2 中的參考編號，大於允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="a4aba-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing interchange because the group control number in the UNG5 field specified in the global settings, specifically the reference number in field UNG5.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="a4aba-118">群組控制編號允許的最大值取決於 UNG5 中的三個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="a4aba-118">The maximum allowable value for the group control number depends upon the values of the three fields in UNG5.</span></span> <span data-ttu-id="a4aba-119">字元數上限為 14 個欄位 UNG5.2，13 個 UNG5.1 中的前置詞和 UNG5.3，在後置詞的 13 和 14 個結合的所有三個欄位中的參考編號。</span><span class="sxs-lookup"><span data-stu-id="a4aba-119">The maximum number of characters is 14 for the reference number in field UNG5.2, 13 for the prefix in UNG5.1 and 13 for the suffix in UNG5.3, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a4aba-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a4aba-120">User Action</span></span>  
 <span data-ttu-id="a4aba-121">若要解決這個錯誤，重設的群組控制編號，參考編號欄位 (UNG5.2)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a4aba-121">To resolve this error, reset the reference number field (UNG5.2) of the group control number, as follows:</span></span>  
  
1.  <span data-ttu-id="a4aba-122">開啟 [EDI 全域屬性] 對話方塊中的 [UNG 和 UNH 區段定義] 頁面。</span><span class="sxs-lookup"><span data-stu-id="a4aba-122">In the EDI Global Properties dialog box, open the UNG and UNH Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="a4aba-123">按一下 編輯欄位之 ugn5 欄位相關聯。</span><span class="sxs-lookup"><span data-stu-id="a4aba-123">Click the Edit field associated with the UNG5 field.</span></span>  
  
3.  <span data-ttu-id="a4aba-124">新的值設定的群組控制編號 （UNG5.2 中的參考編號） 的中間欄位的欄位具有一個可接受的數字。</span><span class="sxs-lookup"><span data-stu-id="a4aba-124">Set the middle field of the group control number (the reference number in UNG5.2) to a new value such that the field has an acceptable number of digits.</span></span>
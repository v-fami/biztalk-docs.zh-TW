---
title: 可接受 X12 交易集控制編號已達到合作對象的最高上限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a402f6d0-4399-47c9-a39a-56d7fa1efa86
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bafbafdd799330b9c34179cfd1949629eee4ca3b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001815"
---
# <a name="max-limit-of-acceptable-x12-transaction-set-control-number-has-reached-for-party"></a><span data-ttu-id="ae650-102">可接受 X12 交易集控制編號已達到合作對象的最高上限</span><span class="sxs-lookup"><span data-stu-id="ae650-102">Max limit of acceptable X12 transaction set control number has reached for party</span></span>
## <a name="details"></a><span data-ttu-id="ae650-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ae650-103">Details</span></span>  
  
|                 |                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="ae650-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ae650-104">Product Name</span></span>   |                                                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                      |
| <span data-ttu-id="ae650-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ae650-105">Product Version</span></span> |                                                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                  |
|    <span data-ttu-id="ae650-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ae650-106">Event ID</span></span>     |                                                                                              -                                                                                              |
|  <span data-ttu-id="ae650-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ae650-107">Event Source</span></span>   |                                                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ae650-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="ae650-108"> EDI</span></span>                                                    |
|    <span data-ttu-id="ae650-109">元件</span><span class="sxs-lookup"><span data-stu-id="ae650-109">Component</span></span>    |                                                                                         <span data-ttu-id="ae650-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="ae650-110">EDI Engine</span></span>                                                                                          |
|  <span data-ttu-id="ae650-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ae650-111">Symbolic Name</span></span>  |                                                                                    <span data-ttu-id="ae650-112">PartyX12TsNumberError</span><span class="sxs-lookup"><span data-stu-id="ae650-112">PartyX12TsNumberError</span></span>                                                                                    |
|  <span data-ttu-id="ae650-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ae650-113">Message Text</span></span>   | <span data-ttu-id="ae650-114">可接受 X12 交易集控制編號已達到合作對象的最高上限{0}。</span><span class="sxs-lookup"><span data-stu-id="ae650-114">Max limit of acceptable X12 transaction set control number has reached for party {0}.</span></span> <span data-ttu-id="ae650-115">在接收者角色畫面中，欄位 [ST 2 在夥伴協議] 管理員中瀏覽至合作對象，重設計數器</span><span class="sxs-lookup"><span data-stu-id="ae650-115">Reset counter by navigating to Party in receiver role screen, field ST 2 in Partner Agreement manager</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="ae650-116">說明</span><span class="sxs-lookup"><span data-stu-id="ae650-116">Explanation</span></span>  
 <span data-ttu-id="ae650-117">這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為交易集設定中指定合作對象，特別是參考編號欄位 ST02.2 中的 [ST02] 欄位中的控制編號已超過允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="ae650-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the transaction set control number in the ST02 field specified in the party settings, specifically the reference number in field ST02.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="ae650-118">交易集控制編號允許的最大值取決於 ST02 中的三個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="ae650-118">The maximum allowable value for the transaction set control number depends upon the values of the three fields in ST02.</span></span> <span data-ttu-id="ae650-119">字元數上限是 9 參考編號欄位 ST02.2，8 ST02.1 中的前置詞和 ST02.3，在後置詞的 8 和 9，結合的所有三個欄位中。</span><span class="sxs-lookup"><span data-stu-id="ae650-119">The maximum number of characters is 9 for the reference number in field ST02.2, 8 for the prefix in ST02.1 and 8 for the suffix in ST02.3, and 9 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ae650-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ae650-120">User Action</span></span>  
 <span data-ttu-id="ae650-121">若要解決這個錯誤，重設的交易集控制編號，參考編號欄位 (UNH1.2)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ae650-121">To resolve this error, reset the reference number field (UNH1.2) of the transaction set control number, as follows:</span></span>  
  
1.  <span data-ttu-id="ae650-122">在 EDI 屬性 對話方塊中的 合作對象的交換解析，開啟 UNG 和 UNH 區段定義頁面。</span><span class="sxs-lookup"><span data-stu-id="ae650-122">In the EDI Properties dialog box for the party resolved for the interchange, open the UNG and UNH Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="ae650-123">按一下 [UNH1] 欄位相關聯的編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="ae650-123">Click the Edit field associated with the UNH1 field.</span></span>  
  
3.  <span data-ttu-id="ae650-124">新的值設定交易集控制編號 （UNH1.2 中的參考編號） 的中間欄位的欄位具有一個可接受的數字。</span><span class="sxs-lookup"><span data-stu-id="ae650-124">Set the middle field of the transaction set control number (the reference number in UNH1.2) to a new value such that the field has an acceptable number of digits.</span></span>
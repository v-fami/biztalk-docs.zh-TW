---
title: X12 交易集控制編號已達到 Guest 設定的可接受的最高上限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e5a4aa5c-13a7-4234-916e-562b52644c51
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b90021a672b3aec71198d8fd6533a2037772346
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014079"
---
# <a name="max-limit-of-acceptable-x12-transaction-set-control-number-has-reached-for-guest-settings"></a><span data-ttu-id="b479a-102">X12 交易集控制編號已達到 Guest 設定的可接受的最高上限</span><span class="sxs-lookup"><span data-stu-id="b479a-102">Max limit of acceptable X12 transaction set control number has reached for Guest settings</span></span>
## <a name="details"></a><span data-ttu-id="b479a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b479a-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                            |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="b479a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b479a-104">Product Name</span></span>   |                                                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                             |
| <span data-ttu-id="b479a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="b479a-105">Product Version</span></span> |                                                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                         |
|    <span data-ttu-id="b479a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b479a-106">Event ID</span></span>     |                                                                                                     -                                                                                                      |
|  <span data-ttu-id="b479a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="b479a-107">Event Source</span></span>   |                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b479a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="b479a-108"> EDI</span></span>                                                           |
|    <span data-ttu-id="b479a-109">元件</span><span class="sxs-lookup"><span data-stu-id="b479a-109">Component</span></span>    |                                                                                                 <span data-ttu-id="b479a-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="b479a-110">EDI Engine</span></span>                                                                                                 |
|  <span data-ttu-id="b479a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b479a-111">Symbolic Name</span></span>  |                                                                                           <span data-ttu-id="b479a-112">GlobalX12TsNumberError</span><span class="sxs-lookup"><span data-stu-id="b479a-112">GlobalX12TsNumberError</span></span>                                                                                           |
|  <span data-ttu-id="b479a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b479a-113">Message Text</span></span>   | <span data-ttu-id="b479a-114">可接受 X12 交易集控制編號已達到 Guest 設定的最大限制。</span><span class="sxs-lookup"><span data-stu-id="b479a-114">Max limit of acceptable X12 transaction set control number has reached for Guest settings.</span></span> <span data-ttu-id="b479a-115">瀏覽至 全域設定寄件者角色畫面，欄位 ST 2 在夥伴協議管理員重設計數器</span><span class="sxs-lookup"><span data-stu-id="b479a-115">Reset counter by navigating to Global configuration sender role screen, field ST 2 in Partner Agreement manager</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="b479a-116">說明</span><span class="sxs-lookup"><span data-stu-id="b479a-116">Explanation</span></span>  
 <span data-ttu-id="b479a-117">這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為交易集控制編號，特別是參考編號欄位 ST02.2 中所述的全域設定，而 ST02 欄位中大於允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="b479a-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the transaction set control number in the ST02 field specified in the global settings, specifically the reference number in field ST02.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="b479a-118">交易集控制編號允許的最大值取決於 ST02 中的三個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="b479a-118">The maximum allowable value for the transaction set control number depends upon the values of the three fields in ST02.</span></span> <span data-ttu-id="b479a-119">最大字元數是欄位 UNH1.2，8 UNH1.1 中的前置詞和 UNH1.3，在後置詞的 8 和 9，結合的所有三個欄位中的參考編號的 9。</span><span class="sxs-lookup"><span data-stu-id="b479a-119">The maximum number of characters is 9 for the reference number in field UNH1.2, 8 for the prefix in UNH1.1 and 8 for the suffix in UNH1.3, and 9 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b479a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b479a-120">User Action</span></span>  
 <span data-ttu-id="b479a-121">若要解決這個錯誤，重設的交易集控制編號，參考編號欄位 (ST02.2)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b479a-121">To resolve this error, reset the reference number field (ST02.2) of the transaction set control number, as follows:</span></span>  
  
1.  <span data-ttu-id="b479a-122">在 EDI 全域屬性 對話方塊中，開啟 GS 和 ST 區段定義頁面。</span><span class="sxs-lookup"><span data-stu-id="b479a-122">In the EDI Global Properties dialog box, open the GS and ST Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="b479a-123">按一下 編輯欄位與 ST02 欄位相關聯。</span><span class="sxs-lookup"><span data-stu-id="b479a-123">Click the Edit field associated with the ST02 field.</span></span>  
  
3.  <span data-ttu-id="b479a-124">新的值設定的群組控制編號 （ST02.2 中的參考編號） 的中間欄位的欄位具有一個可接受的數字。</span><span class="sxs-lookup"><span data-stu-id="b479a-124">Set the middle field of the group control number (the reference number in ST02.2) to a new value such that the field has an acceptable number of digits.</span></span>
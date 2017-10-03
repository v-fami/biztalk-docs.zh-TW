---
title: "合作對象已達到可接受的 Edifact 功能群組控制編號的最高上限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fde516b-59f1-49a1-8456-127469df0e02
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d4a47e0866c78e692f8c992afbd6b24cde95632
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-functional-group-control-number-has-reached-for-party"></a><span data-ttu-id="3a075-102">合作對象已達到可接受的 Edifact 功能群組控制編號的最高上限</span><span class="sxs-lookup"><span data-stu-id="3a075-102">Max limit of acceptable Edifact functional group control number has reached for party</span></span>
## <a name="details"></a><span data-ttu-id="3a075-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a075-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a075-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3a075-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3a075-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3a075-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3a075-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3a075-106">Event ID</span></span>|-|  
|<span data-ttu-id="3a075-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="3a075-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3a075-108">EDI</span><span class="sxs-lookup"><span data-stu-id="3a075-108"> EDI</span></span>|  
|<span data-ttu-id="3a075-109">元件</span><span class="sxs-lookup"><span data-stu-id="3a075-109">Component</span></span>|<span data-ttu-id="3a075-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="3a075-110">EDI Engine</span></span>|  
|<span data-ttu-id="3a075-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3a075-111">Symbolic Name</span></span>|<span data-ttu-id="3a075-112">PartyEdifactUngNumberError</span><span class="sxs-lookup"><span data-stu-id="3a075-112">PartyEdifactUngNumberError</span></span>|  
|<span data-ttu-id="3a075-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3a075-113">Message Text</span></span>|<span data-ttu-id="3a075-114">合作對象 {0}，已達到可接受的 Edifact 功能群組控制編號的最高上限。</span><span class="sxs-lookup"><span data-stu-id="3a075-114">Max limit of acceptable Edifact functional group control number has reached for party {0}.</span></span> <span data-ttu-id="3a075-115">瀏覽至合作對象中接收者角色畫面，欄位 UNG 5 在夥伴協議管理員 中，重設計數器</span><span class="sxs-lookup"><span data-stu-id="3a075-115">Reset counter by navigating to Party in receiver role screen, field UNG 5 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3a075-116">說明</span><span class="sxs-lookup"><span data-stu-id="3a075-116">Explanation</span></span>  
 <span data-ttu-id="3a075-117">這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄 EDIFACT 交換的合作對象設定，特別是欄位 UNG5.2 中的參考編號所指定之 ugn5 欄位的群組控制編號，因此大於允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="3a075-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing EDIFACT interchange because the group control number in the UNG5 field specified in the party settings, specifically the reference number in field UNG5.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="3a075-118">群組控制編號允許的最大值取決於 UNG5 中三個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="3a075-118">The maximum allowable value for the group control number depends upon the values of the three fields in UNG5.</span></span> <span data-ttu-id="3a075-119">最大字元數是參考編號欄位 UNG5.2，13 for UNG5.1 中的前置詞和 13 for UNG5.3，在後置詞結合的所有三個欄位 14 中 14。</span><span class="sxs-lookup"><span data-stu-id="3a075-119">The maximum number of characters is 14 for the reference number in field UNG5.2, 13 for the prefix in UNG5.1 and 13 for the suffix in UNG5.3, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3a075-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3a075-120">User Action</span></span>  
 <span data-ttu-id="3a075-121">若要解決這個錯誤，重設的群組控制編號，參考編號欄位 (UNG5.2)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3a075-121">To resolve this error, reset the reference number field (UNG5.2) of the group control number, as follows:</span></span>  
  
1.  <span data-ttu-id="3a075-122">在 EDI 屬性 對話方塊中的 合作對象的交換解析，開啟做為交換接收者的合作對象的 UNG 和 UNH 區段定義頁面。</span><span class="sxs-lookup"><span data-stu-id="3a075-122">In the EDI Properties dialog box for the party resolved for the interchange, open the UNG and UNH Segment Definition page for the party as interchange receiver.</span></span>  
  
2.  <span data-ttu-id="3a075-123">按一下 UNG5 欄位相關聯的編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="3a075-123">Click the Edit field associated with the UNG5 field.</span></span>  
  
3.  <span data-ttu-id="3a075-124">新的值設定的群組控制編號 （UNG5.2 中的參考編號） 的中間欄位的欄位具有可接受數。</span><span class="sxs-lookup"><span data-stu-id="3a075-124">Set the middle field of the group control number (the reference number in UNG5.2) to a new value such that the field has an acceptable number of digits.</span></span>
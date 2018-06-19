---
title: 可接受 Edifact 交易集控制編號已達到 Guest 設定的最高上限 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3924a18c-87bc-4727-b7cd-598d3e5ade2a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 709d6069d143cea2271e6311fad571a0290133db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241150"
---
# <a name="max-limit-of-acceptable-edifact-transaction-set-control-number-has-reached-for-guest-settings"></a><span data-ttu-id="0c39a-102">Guest 設定的 Edifact 交易集控制編號已達到可接受的最高上限</span><span class="sxs-lookup"><span data-stu-id="0c39a-102">Max limit of acceptable Edifact transaction set control number has reached for Guest settings</span></span>
## <a name="details"></a><span data-ttu-id="0c39a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0c39a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c39a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0c39a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0c39a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0c39a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0c39a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0c39a-106">Event ID</span></span>|-|  
|<span data-ttu-id="0c39a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="0c39a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0c39a-108">EDI</span><span class="sxs-lookup"><span data-stu-id="0c39a-108"> EDI</span></span>|  
|<span data-ttu-id="0c39a-109">元件</span><span class="sxs-lookup"><span data-stu-id="0c39a-109">Component</span></span>|<span data-ttu-id="0c39a-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="0c39a-110">EDI Engine</span></span>|  
|<span data-ttu-id="0c39a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0c39a-111">Symbolic Name</span></span>|<span data-ttu-id="0c39a-112">GlobalEdifactUnhNumberError</span><span class="sxs-lookup"><span data-stu-id="0c39a-112">GlobalEdifactUnhNumberError</span></span>|  
|<span data-ttu-id="0c39a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0c39a-113">Message Text</span></span>|<span data-ttu-id="0c39a-114">Guest 設定的 Edifact 交易集控制編號已達到可接受的最高上限。</span><span class="sxs-lookup"><span data-stu-id="0c39a-114">Max limit of acceptable Edifact transaction set control number has reached for Guest settings.</span></span> <span data-ttu-id="0c39a-115">請瀏覽至 [夥伴協議] 管理員中的全域組態接收者角色畫面，欄位 [UNH 1]，重設計數器</span><span class="sxs-lookup"><span data-stu-id="0c39a-115">Reset counter by  navigating to Global configuration receiver role screen, field UNH 1 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0c39a-116">說明</span><span class="sxs-lookup"><span data-stu-id="0c39a-116">Explanation</span></span>  
 <span data-ttu-id="0c39a-117">這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄交換的交易集控制編號中指定的全域設定，特別是欄位 UNH1.2 中的參考編號的 UNH1 欄位因為已超過允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="0c39a-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing interchange because the transaction set control number in the UNH1 field specified in the global settings, specifically the reference number in field UNH1.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="0c39a-118">群組控制編號允許的最大值取決於 UNH1 中三個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="0c39a-118">The maximum allowable value for the group control number depends upon the values of the three fields in UNH1.</span></span> <span data-ttu-id="0c39a-119">最大字元數是參考編號欄位 UNH1.2，13 for UNH1.1 中的前置詞和 13 for UNH1.3，在後置詞結合的所有三個欄位 14 中 14。</span><span class="sxs-lookup"><span data-stu-id="0c39a-119">The maximum number of characters is 14 for the reference number in field UNH1.2, 13 for the prefix in UNH1.1 and 13 for the suffix in UNH1.3, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0c39a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0c39a-120">User Action</span></span>  
 <span data-ttu-id="0c39a-121">若要解決這個錯誤，重設的交易集控制編號，參考編號欄位 (UNH1.2)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0c39a-121">To resolve this error, reset the reference number field (UNH1.2) of the transaction set control number, as follows:</span></span>  
  
1.  <span data-ttu-id="0c39a-122">在 EDI 全域屬性 對話方塊中，開啟 UNH 區段定義頁面。</span><span class="sxs-lookup"><span data-stu-id="0c39a-122">In the EDI Global Properties dialog box, open the UNH Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="0c39a-123">按一下 UNH1 欄位相關聯的編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="0c39a-123">Click the Edit field associated with the UNH1 field.</span></span>  
  
3.  <span data-ttu-id="0c39a-124">新的值設定的群組控制編號 （UNH1.2 中的參考編號） 的中間欄位的欄位具有可接受數。</span><span class="sxs-lookup"><span data-stu-id="0c39a-124">Set the middle field of the group control number (the reference number in UNH1.2) to a new value such that the field has an acceptable number of digits.</span></span>
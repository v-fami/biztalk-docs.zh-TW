---
title: Guest 設定的已達到可接受 Edifact 交換控制編號的最高上限 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a5d2dcc0-61fd-47c9-9339-8a85319c5398
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dc8110f9aa9a48e098f970383b65266cc544c19
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241526"
---
# <a name="max-limit-of-acceptable-edifact-interchange-control-number-has-reached-for-guest-settings"></a><span data-ttu-id="dfc92-102">Guest 設定的已達到可接受 Edifact 交換控制編號的最高上限</span><span class="sxs-lookup"><span data-stu-id="dfc92-102">Max limit of acceptable Edifact interchange control number has reached for Guest settings</span></span>
## <a name="details"></a><span data-ttu-id="dfc92-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dfc92-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dfc92-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dfc92-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="dfc92-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="dfc92-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="dfc92-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dfc92-106">Event ID</span></span>|-|  
|<span data-ttu-id="dfc92-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="dfc92-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dfc92-108">EDI</span><span class="sxs-lookup"><span data-stu-id="dfc92-108"> EDI</span></span>|  
|<span data-ttu-id="dfc92-109">元件</span><span class="sxs-lookup"><span data-stu-id="dfc92-109">Component</span></span>|<span data-ttu-id="dfc92-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="dfc92-110">EDI Engine</span></span>|  
|<span data-ttu-id="dfc92-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dfc92-111">Symbolic Name</span></span>|<span data-ttu-id="dfc92-112">GlobalEdifactUnbNumberError</span><span class="sxs-lookup"><span data-stu-id="dfc92-112">GlobalEdifactUnbNumberError</span></span>|  
|<span data-ttu-id="dfc92-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dfc92-113">Message Text</span></span>|<span data-ttu-id="dfc92-114">Guest 設定的已達到可接受 Edifact 交換控制編號的最高上限。</span><span class="sxs-lookup"><span data-stu-id="dfc92-114">Max limit of acceptable Edifact interchange control number has reached for Guest settings.</span></span> <span data-ttu-id="dfc92-115">瀏覽到全域組態接收者角色畫面，欄位 UNB 5 在夥伴協議管理員 中，重設計數器</span><span class="sxs-lookup"><span data-stu-id="dfc92-115">Reset counter by navigating to Global configuration receiver role screen, field UNB 5 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dfc92-116">說明</span><span class="sxs-lookup"><span data-stu-id="dfc92-116">Explanation</span></span>  
 <span data-ttu-id="dfc92-117">這個錯誤/警告/資訊事件表示，傳送管線無法處理外寄交換的交換控制編號，在通用設定，特別是參考編號欄位 UNB5.2，在指定的 ISA13 欄位中，因此大於允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="dfc92-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing interchange because the interchange control number in the ISA13 field specified in the global settings, specifically the reference number in field UNB5.2, was greater than the maximum allowable value.</span></span> <span data-ttu-id="dfc92-118">交換控制編號允許的最大值取決於 UNB5 中三個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="dfc92-118">The maximum allowable value for the interchange control number depends upon the values of the three fields in UNB5.</span></span> <span data-ttu-id="dfc92-119">字元數上限為 14 個欄位 UNB5.2，13 for UNB5.1 中的前置詞和 13 for UNB5.3，在後置詞結合的所有三個欄位 14 中的參考編號。</span><span class="sxs-lookup"><span data-stu-id="dfc92-119">The maximum number of characters is 14 for the reference number in field UNB5.2, 13 for the prefix in UNB5.1 and 13 for the suffix in UNB5.3, and 14 for all three fields combined.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dfc92-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dfc92-120">User Action</span></span>  
 <span data-ttu-id="dfc92-121">若要解決這個錯誤，重設的交換控制編號，參考編號欄位 (UNB5.2)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="dfc92-121">To resolve this error, reset the reference number field (UNB5.2) of the interchange control number, as follows:</span></span>  
  
1.  <span data-ttu-id="dfc92-122">在 EDI 全域屬性 對話方塊中，開啟 UNB 區段定義頁面。</span><span class="sxs-lookup"><span data-stu-id="dfc92-122">In the EDI Global Properties dialog box, open the UNB Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="dfc92-123">按一下 UNB5 欄位相關聯的編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="dfc92-123">Click the Edit field associated with the UNB5 field.</span></span>  
  
3.  <span data-ttu-id="dfc92-124">新的值設定交換控制編號 （UNB5.2 中的參考編號） 的中間欄位的欄位具有可接受數。</span><span class="sxs-lookup"><span data-stu-id="dfc92-124">Set the middle field of the interchange control number (the reference number in UNB5.2) to a new value such that the field has an acceptable number of digits.</span></span>
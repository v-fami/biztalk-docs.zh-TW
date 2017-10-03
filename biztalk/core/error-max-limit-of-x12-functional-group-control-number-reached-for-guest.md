---
title: "可接受的 X12 功能群組控制編號已達到 Guest 設定的最高上限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05cba774-fa35-4694-aa34-d7151f8cd75c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3210fb773b7093c2e28f98e0cf1aa223e1a63936
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-functional-group-control-number-has-reached-for-guest-settings"></a><span data-ttu-id="afd65-102">可接受的 X12 功能群組控制編號已達到 Guest 設定的最高上限</span><span class="sxs-lookup"><span data-stu-id="afd65-102">Max limit of acceptable X12 functional group control number has reached for Guest settings</span></span>
## <a name="details"></a><span data-ttu-id="afd65-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="afd65-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="afd65-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="afd65-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="afd65-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="afd65-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="afd65-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="afd65-106">Event ID</span></span>|-|  
|<span data-ttu-id="afd65-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="afd65-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="afd65-108">EDI</span><span class="sxs-lookup"><span data-stu-id="afd65-108"> EDI</span></span>|  
|<span data-ttu-id="afd65-109">元件</span><span class="sxs-lookup"><span data-stu-id="afd65-109">Component</span></span>|<span data-ttu-id="afd65-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="afd65-110">EDI Engine</span></span>|  
|<span data-ttu-id="afd65-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="afd65-111">Symbolic Name</span></span>|<span data-ttu-id="afd65-112">GlobalEdifactUnhNumberError</span><span class="sxs-lookup"><span data-stu-id="afd65-112">GlobalEdifactUnhNumberError</span></span>|  
|<span data-ttu-id="afd65-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="afd65-113">Message Text</span></span>|<span data-ttu-id="afd65-114">可接受的 X12 功能群組控制編號已達到 Guest 設定的最高上限。</span><span class="sxs-lookup"><span data-stu-id="afd65-114">Max limit of acceptable X12 functional group control number has reached for Guest settings.</span></span> <span data-ttu-id="afd65-115">瀏覽到全域組態接收者角色畫面，欄位 GS 6 在夥伴協議管理員 中，重設計數器</span><span class="sxs-lookup"><span data-stu-id="afd65-115">Reset counter by navigating to Global configuration receiver role screen, field GS 6 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="afd65-116">說明</span><span class="sxs-lookup"><span data-stu-id="afd65-116">Explanation</span></span>  
 <span data-ttu-id="afd65-117">這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為全域設定中指定的 GS06 欄位中的群組控制編號大於允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="afd65-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the group control number in the GS06 field specified in the global settings was greater than the maximum allowable value.</span></span> <span data-ttu-id="afd65-118">群組控制編號的字元數目上限是 9。</span><span class="sxs-lookup"><span data-stu-id="afd65-118">The maximum number of characters for the group control number is 9.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="afd65-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="afd65-119">User Action</span></span>  
 <span data-ttu-id="afd65-120">若要解決這個錯誤，重設群組控制編號，如下所示：</span><span class="sxs-lookup"><span data-stu-id="afd65-120">To resolve this error, reset the group control number, as follows:</span></span>  
  
1.  <span data-ttu-id="afd65-121">在 EDI 全域屬性 對話方塊中，開啟 GS 和 ST 區段定義頁面。</span><span class="sxs-lookup"><span data-stu-id="afd65-121">In the EDI Global Properties dialog box, open the GS and ST Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="afd65-122">按一下 GS06 欄位相關聯的編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="afd65-122">Click the Edit field associated with the GS06 field.</span></span>  
  
3.  <span data-ttu-id="afd65-123">設定為新值，此欄位有九個或更少的數字的群組控制編號。</span><span class="sxs-lookup"><span data-stu-id="afd65-123">Set the group control number to a new value such that the field has nine or fewer digits.</span></span>
---
title: "可接受的 X12 交換控制編號已達到 Guest 設定的最高上限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9737053d-6065-4c88-8dfa-5f69b48e0e82
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c72fc565367477d9dbd09f3c0d4c4f9d6ab686a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-interchange-control-number-has-reached-for-guest-settings"></a><span data-ttu-id="cb1e6-102">可接受的 X12 交換控制編號已達到 Guest 設定的最高上限</span><span class="sxs-lookup"><span data-stu-id="cb1e6-102">Max limit of acceptable X12 interchange control number has reached for Guest settings</span></span>
## <a name="details"></a><span data-ttu-id="cb1e6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cb1e6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb1e6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cb1e6-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="cb1e6-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="cb1e6-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="cb1e6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cb1e6-106">Event ID</span></span>|-|  
|<span data-ttu-id="cb1e6-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="cb1e6-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="cb1e6-108">EDI</span><span class="sxs-lookup"><span data-stu-id="cb1e6-108"> EDI</span></span>|  
|<span data-ttu-id="cb1e6-109">元件</span><span class="sxs-lookup"><span data-stu-id="cb1e6-109">Component</span></span>|<span data-ttu-id="cb1e6-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="cb1e6-110">EDI Engine</span></span>|  
|<span data-ttu-id="cb1e6-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cb1e6-111">Symbolic Name</span></span>|<span data-ttu-id="cb1e6-112">GlobalX12IsaNumberError</span><span class="sxs-lookup"><span data-stu-id="cb1e6-112">GlobalX12IsaNumberError</span></span>|  
|<span data-ttu-id="cb1e6-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cb1e6-113">Message Text</span></span>|<span data-ttu-id="cb1e6-114">可接受的 X12 交換控制編號已達到 Guest 設定的最高上限。</span><span class="sxs-lookup"><span data-stu-id="cb1e6-114">Max limit of acceptable X12 interchange control number has reached for Guest settings.</span></span> <span data-ttu-id="cb1e6-115">瀏覽到全域組態接收者角色畫面，欄位 ISA 13 在夥伴協議管理員 中，重設計數器</span><span class="sxs-lookup"><span data-stu-id="cb1e6-115">Reset counter by navigating to Global configuration receiver role screen, field ISA 13 in Partner Agreement manager</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cb1e6-116">說明</span><span class="sxs-lookup"><span data-stu-id="cb1e6-116">Explanation</span></span>  
 <span data-ttu-id="cb1e6-117">這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為全域設定中指定 [ISA13] 欄位中的交換控制編號大於允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="cb1e6-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the interchange control number in the ISA13 field specified in the global settings was greater than the maximum allowable value.</span></span> <span data-ttu-id="cb1e6-118">交換控制編號的字元數目上限是 9。</span><span class="sxs-lookup"><span data-stu-id="cb1e6-118">The maximum number of characters for the interchange control number is nine.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cb1e6-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cb1e6-119">User Action</span></span>  
 <span data-ttu-id="cb1e6-120">若要解決這個錯誤，重設交換控制編號，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cb1e6-120">To resolve this error, reset the interchange control number, as follows:</span></span>  
  
1.  <span data-ttu-id="cb1e6-121">在 EDI 全域屬性 對話方塊中，開啟 ISA 區段定義頁面。</span><span class="sxs-lookup"><span data-stu-id="cb1e6-121">In the EDI Global Properties dialog box, open the ISA Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="cb1e6-122">按一下 [ISA13] 欄位相關聯的編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="cb1e6-122">Click the Edit field associated with the ISA13 field.</span></span>  
  
3.  <span data-ttu-id="cb1e6-123">設定為新值，欄位具有可接受的數量的數字的交換控制編號。</span><span class="sxs-lookup"><span data-stu-id="cb1e6-123">Set the interchange control number to a new value such that the field has an acceptable number of digits.</span></span>
---
title: X12 功能群組控制編號已達到 Guest 設定的可接受的最高上限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05cba774-fa35-4694-aa34-d7151f8cd75c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70855ad87ad18c29c51a4d87878339b014bb47d8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010407"
---
# <a name="max-limit-of-acceptable-x12-functional-group-control-number-has-reached-for-guest-settings"></a><span data-ttu-id="a2162-102">X12 功能群組控制編號已達到 Guest 設定的可接受的最高上限</span><span class="sxs-lookup"><span data-stu-id="a2162-102">Max limit of acceptable X12 functional group control number has reached for Guest settings</span></span>
## <a name="details"></a><span data-ttu-id="a2162-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a2162-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                               |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="a2162-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a2162-104">Product Name</span></span>   |                                                              [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                               |
| <span data-ttu-id="a2162-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a2162-105">Product Version</span></span> |                                                                          [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                           |
|    <span data-ttu-id="a2162-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a2162-106">Event ID</span></span>     |                                                                                                       -                                                                                                       |
|  <span data-ttu-id="a2162-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="a2162-107">Event Source</span></span>   |                                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a2162-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a2162-108"> EDI</span></span>                                                             |
|    <span data-ttu-id="a2162-109">元件</span><span class="sxs-lookup"><span data-stu-id="a2162-109">Component</span></span>    |                                                                                                  <span data-ttu-id="a2162-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="a2162-110">EDI Engine</span></span>                                                                                                   |
|  <span data-ttu-id="a2162-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a2162-111">Symbolic Name</span></span>  |                                                                                          <span data-ttu-id="a2162-112">GlobalEdifactUnhNumberError</span><span class="sxs-lookup"><span data-stu-id="a2162-112">GlobalEdifactUnhNumberError</span></span>                                                                                          |
|  <span data-ttu-id="a2162-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a2162-113">Message Text</span></span>   | <span data-ttu-id="a2162-114">可接受的 X12 功能群組控制編號已達到 Guest 設定的最大限制。</span><span class="sxs-lookup"><span data-stu-id="a2162-114">Max limit of acceptable X12 functional group control number has reached for Guest settings.</span></span> <span data-ttu-id="a2162-115">瀏覽至全域組態接收者角色畫面，在夥伴協議 管理員中的欄位 GS 6，重設計數器</span><span class="sxs-lookup"><span data-stu-id="a2162-115">Reset counter by navigating to Global configuration receiver role screen, field GS 6 in Partner Agreement manager</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="a2162-116">說明</span><span class="sxs-lookup"><span data-stu-id="a2162-116">Explanation</span></span>  
 <span data-ttu-id="a2162-117">這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為全域設定中指定的 GS06 欄位中的群組控制編號大於允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="a2162-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing X12 interchange because the group control number in the GS06 field specified in the global settings was greater than the maximum allowable value.</span></span> <span data-ttu-id="a2162-118">群組控制編號的字元數目上限是 9。</span><span class="sxs-lookup"><span data-stu-id="a2162-118">The maximum number of characters for the group control number is 9.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a2162-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a2162-119">User Action</span></span>  
 <span data-ttu-id="a2162-120">若要解決這個錯誤，重設群組控制編號，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a2162-120">To resolve this error, reset the group control number, as follows:</span></span>  
  
1.  <span data-ttu-id="a2162-121">在 EDI 全域屬性 對話方塊中，開啟 GS 和 ST 區段定義頁面。</span><span class="sxs-lookup"><span data-stu-id="a2162-121">In the EDI Global Properties dialog box, open the GS and ST Segment Definition page.</span></span>  
  
2.  <span data-ttu-id="a2162-122">按一下 GS06 欄位相關聯的編輯欄位。</span><span class="sxs-lookup"><span data-stu-id="a2162-122">Click the Edit field associated with the GS06 field.</span></span>  
  
3.  <span data-ttu-id="a2162-123">使欄位具有九個或更少的數字，則您可以設為新的值的群組控制編號。</span><span class="sxs-lookup"><span data-stu-id="a2162-123">Set the group control number to a new value such that the field has nine or fewer digits.</span></span>
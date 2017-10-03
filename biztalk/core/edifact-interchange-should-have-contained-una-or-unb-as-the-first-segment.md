---
title: "Edifact 交換應該包含 UNA 或 UNB 作為第一個區段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc43fd17-31d0-48df-93cd-524b40034764
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e673df728dea00852e9713aed12f8ced902a4fdc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-interchange-should-have-contained-una-or-unb-as-the-first-segment"></a><span data-ttu-id="bb4e7-102">Edifact 交換應該包含 UNA 或 UNB 作為第一個區段</span><span class="sxs-lookup"><span data-stu-id="bb4e7-102">Edifact interchange should have contained UNA or UNB as the first segment</span></span>
## <a name="details"></a><span data-ttu-id="bb4e7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bb4e7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bb4e7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bb4e7-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="bb4e7-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="bb4e7-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="bb4e7-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bb4e7-106">Event ID</span></span>|-|  
|<span data-ttu-id="bb4e7-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="bb4e7-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bb4e7-108">EDI</span><span class="sxs-lookup"><span data-stu-id="bb4e7-108"> EDI</span></span>|  
|<span data-ttu-id="bb4e7-109">元件</span><span class="sxs-lookup"><span data-stu-id="bb4e7-109">Component</span></span>|<span data-ttu-id="bb4e7-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="bb4e7-110">EDI Engine</span></span>|  
|<span data-ttu-id="bb4e7-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bb4e7-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="bb4e7-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bb4e7-112">Message Text</span></span>|<span data-ttu-id="bb4e7-113">Edifact 交換應該包含 UNA 或 UNB 作為第一個區段。</span><span class="sxs-lookup"><span data-stu-id="bb4e7-113">Edifact interchange should have contained UNA or UNB as the first segment.</span></span> <span data-ttu-id="bb4e7-114">而是找到 {0}</span><span class="sxs-lookup"><span data-stu-id="bb4e7-114">Instead {0} was found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bb4e7-115">說明</span><span class="sxs-lookup"><span data-stu-id="bb4e7-115">Explanation</span></span>  
 <span data-ttu-id="bb4e7-116">這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送 EDIFACT 交換，因為第一個區段未 UNA 或 UNB 區段。</span><span class="sxs-lookup"><span data-stu-id="bb4e7-116">This Error/Warning/Information event indicates that the EDI receive pipeline could not process the incoming EDIFACT interchange because the first segment was neither a UNA nor a UNB segment.</span></span> <span data-ttu-id="bb4e7-117">UNA 區段是選擇性的。UNB 區段是必要的。</span><span class="sxs-lookup"><span data-stu-id="bb4e7-117">The UNA segment is optional; the UNB segment is mandatory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bb4e7-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bb4e7-118">User Action</span></span>  
 <span data-ttu-id="bb4e7-119">若要解決這個錯誤，請確認交換的寄件者包含 UNA 或 UNB 區段的第一個區段的交換，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="bb4e7-119">To resolve this error, ensure that the sender of the interchange includes the UNA or UNB segment as the first segment of the interchange, and then resends the interchange.</span></span>
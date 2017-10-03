---
title: "區段超出最大的使用描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4e1704a-5d49-4549-af50-d1a89a1e70f0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71f5e5a0ae590be850a4560324814c756d51e9fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="segment-exceeds-maximum-use-description"></a><span data-ttu-id="bb81e-102">區段超出最大的使用說明</span><span class="sxs-lookup"><span data-stu-id="bb81e-102">Segment Exceeds Maximum Use Description</span></span>
## <a name="details"></a><span data-ttu-id="bb81e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bb81e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bb81e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bb81e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="bb81e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="bb81e-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="bb81e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bb81e-106">Event ID</span></span>|-|  
|<span data-ttu-id="bb81e-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="bb81e-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bb81e-108">EDI</span><span class="sxs-lookup"><span data-stu-id="bb81e-108"> EDI</span></span>|  
|<span data-ttu-id="bb81e-109">元件</span><span class="sxs-lookup"><span data-stu-id="bb81e-109">Component</span></span>|<span data-ttu-id="bb81e-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="bb81e-110">EDI Engine</span></span>|  
|<span data-ttu-id="bb81e-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bb81e-111">Symbolic Name</span></span>|<span data-ttu-id="bb81e-112">X12SegmentExceedsMaximumUseDescription</span><span class="sxs-lookup"><span data-stu-id="bb81e-112">X12SegmentExceedsMaximumUseDescription</span></span>|  
|<span data-ttu-id="bb81e-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bb81e-113">Message Text</span></span>|<span data-ttu-id="bb81e-114">區段超出最大的使用說明</span><span class="sxs-lookup"><span data-stu-id="bb81e-114">Segment Exceeds Maximum Use Description</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="bb81e-115">說明</span><span class="sxs-lookup"><span data-stu-id="bb81e-115">Explanation</span></span>  
 <span data-ttu-id="bb81e-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換包含多個區段的執行個體超過允許的結構描述。</span><span class="sxs-lookup"><span data-stu-id="bb81e-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained more instances of a segment than allowed by the schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bb81e-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bb81e-117">User Action</span></span>  
 <span data-ttu-id="bb81e-118">若要解決這個錯誤，請確定交換不會不擁有超過最大允許數目的區段，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="bb81e-118">To resolve this error, make sure that the interchange does not have more than the maximum allowed number of segments, and then resend the interchange.</span></span>
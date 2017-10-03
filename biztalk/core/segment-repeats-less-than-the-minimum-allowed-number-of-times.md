---
title: "小於允許的最小次數區段重複 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8ca6c3d-f923-49bc-b5d9-65dc2d7adab1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee7aeb488fb2f8634fba73e7ddf3f44cd02a6529
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="segment-repeats-less-than-the-minimum-allowed-number-of-times"></a><span data-ttu-id="1732e-102">區段重複次數少於允許的最小時間數目</span><span class="sxs-lookup"><span data-stu-id="1732e-102">Segment repeats less than the minimum allowed number of times</span></span>
## <a name="details"></a><span data-ttu-id="1732e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1732e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1732e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1732e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="1732e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1732e-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="1732e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1732e-106">Event ID</span></span>|-|  
|<span data-ttu-id="1732e-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="1732e-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1732e-108">EDI</span><span class="sxs-lookup"><span data-stu-id="1732e-108"> EDI</span></span>|  
|<span data-ttu-id="1732e-109">元件</span><span class="sxs-lookup"><span data-stu-id="1732e-109">Component</span></span>|<span data-ttu-id="1732e-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="1732e-110">EDI Engine</span></span>|  
|<span data-ttu-id="1732e-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1732e-111">Symbolic Name</span></span>|<span data-ttu-id="1732e-112">X12SeSegmentRepeatsLessTimesDescription</span><span class="sxs-lookup"><span data-stu-id="1732e-112">X12SeSegmentRepeatsLessTimesDescription</span></span>|  
|<span data-ttu-id="1732e-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1732e-113">Message Text</span></span>|<span data-ttu-id="1732e-114">區段重複次數少於允許的最小時間數目</span><span class="sxs-lookup"><span data-stu-id="1732e-114">Segment repeats less than the minimum allowed number of times</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1732e-115">說明</span><span class="sxs-lookup"><span data-stu-id="1732e-115">Explanation</span></span>  
 <span data-ttu-id="1732e-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換，因為交換中的區段不會重複文件結構描述所需最少次數。</span><span class="sxs-lookup"><span data-stu-id="1732e-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because a segment in the interchange does not repeat the minimum number of times required by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1732e-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1732e-117">User Action</span></span>  
 <span data-ttu-id="1732e-118">若要解決這個錯誤，做為區段的重複交換的寄件者重複執行，但是至少文件結構描述所需最少次數後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="1732e-118">To resolve this error, have the sender of the interchange as repetition of the segment so that it repeats at least the minimum number of times required by the document schema, and then resend the interchange.</span></span>
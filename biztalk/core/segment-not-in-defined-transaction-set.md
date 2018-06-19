---
title: 區段不在定義的交易集 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914e333f-96e4-4094-880d-51a5f25915c3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2f0b330110ef08196681e54e543173c3f2bd0f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269518"
---
# <a name="segment-not-in-defined-transaction-set"></a><span data-ttu-id="e86bc-102">設定區段不在定義的交易</span><span class="sxs-lookup"><span data-stu-id="e86bc-102">Segment Not In Defined Transaction set</span></span>
## <a name="details"></a><span data-ttu-id="e86bc-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e86bc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e86bc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e86bc-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e86bc-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e86bc-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="e86bc-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e86bc-106">Event ID</span></span>|-|  
|<span data-ttu-id="e86bc-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e86bc-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e86bc-108">EDI</span><span class="sxs-lookup"><span data-stu-id="e86bc-108"> EDI</span></span>|  
|<span data-ttu-id="e86bc-109">元件</span><span class="sxs-lookup"><span data-stu-id="e86bc-109">Component</span></span>|<span data-ttu-id="e86bc-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e86bc-110">EDI Engine</span></span>|  
|<span data-ttu-id="e86bc-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e86bc-111">Symbolic Name</span></span>|<span data-ttu-id="e86bc-112">X12SegmentNotInDefinedTSDescription</span><span class="sxs-lookup"><span data-stu-id="e86bc-112">X12SegmentNotInDefinedTSDescription</span></span>|  
|<span data-ttu-id="e86bc-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e86bc-113">Message Text</span></span>|<span data-ttu-id="e86bc-114">設定區段不在定義的交易</span><span class="sxs-lookup"><span data-stu-id="e86bc-114">Segment Not In Defined Transaction set</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e86bc-115">說明</span><span class="sxs-lookup"><span data-stu-id="e86bc-115">Explanation</span></span>  
 <span data-ttu-id="e86bc-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換因為該交換中的交易集不包含文件結構描述所需的區段。</span><span class="sxs-lookup"><span data-stu-id="e86bc-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because a transaction set in that interchange does not contain a segment required by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e86bc-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e86bc-117">User Action</span></span>  
 <span data-ttu-id="e86bc-118">若要解決這個錯誤，有交換傳送者將必要的區段新增至交換中交易集，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="e86bc-118">To resolve this error, have the sender of the interchange add the required segment to the transaction set in the interchange, and then resend the interchange.</span></span>
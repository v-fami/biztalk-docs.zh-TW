---
title: 區段有資料項目錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 469622e2-6500-4f55-ab53-f8d89ee0a978
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27c8c9e43bfe0a733a3e95b7812195a0b7f3990c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269422"
---
# <a name="segment-has-data-element-errors"></a><span data-ttu-id="61c0f-102">區段有資料元素錯誤</span><span class="sxs-lookup"><span data-stu-id="61c0f-102">Segment has data element errors</span></span>
## <a name="details"></a><span data-ttu-id="61c0f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="61c0f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="61c0f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="61c0f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="61c0f-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="61c0f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="61c0f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="61c0f-106">Event ID</span></span>|-|  
|<span data-ttu-id="61c0f-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="61c0f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="61c0f-108">EDI</span><span class="sxs-lookup"><span data-stu-id="61c0f-108"> EDI</span></span>|  
|<span data-ttu-id="61c0f-109">元件</span><span class="sxs-lookup"><span data-stu-id="61c0f-109">Component</span></span>|<span data-ttu-id="61c0f-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="61c0f-110">EDI Engine</span></span>|  
|<span data-ttu-id="61c0f-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="61c0f-111">Symbolic Name</span></span>|<span data-ttu-id="61c0f-112">X12SegmentHasDataElementErrorsDescription</span><span class="sxs-lookup"><span data-stu-id="61c0f-112">X12SegmentHasDataElementErrorsDescription</span></span>|  
|<span data-ttu-id="61c0f-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="61c0f-113">Message Text</span></span>|<span data-ttu-id="61c0f-114">區段有資料項目錯誤</span><span class="sxs-lookup"><span data-stu-id="61c0f-114">Segment Has Data Element Errors</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="61c0f-115">說明</span><span class="sxs-lookup"><span data-stu-id="61c0f-115">Explanation</span></span>  
 <span data-ttu-id="61c0f-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換包含區段包含文件結構描述不符合的資料元素。</span><span class="sxs-lookup"><span data-stu-id="61c0f-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained segments that included data elements that did not conform to the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="61c0f-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="61c0f-117">User Action</span></span>  
 <span data-ttu-id="61c0f-118">若要解決這個錯誤，請確定交換中的資料元素符合文件結構描述，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="61c0f-118">To resolve this error, make sure that the data elements in the interchange conform to the document schema, and then resend the interchange.</span></span>
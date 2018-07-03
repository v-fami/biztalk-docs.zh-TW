---
title: 區段有資料項目錯誤 |Microsoft Docs
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
ms.openlocfilehash: 30b000f670e4329c68540b51f291097f5bbd4dc2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998887"
---
# <a name="segment-has-data-element-errors"></a><span data-ttu-id="8c48b-102">區段有資料元素錯誤</span><span class="sxs-lookup"><span data-stu-id="8c48b-102">Segment has data element errors</span></span>
## <a name="details"></a><span data-ttu-id="8c48b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8c48b-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="8c48b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8c48b-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="8c48b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="8c48b-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="8c48b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8c48b-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="8c48b-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="8c48b-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8c48b-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="8c48b-108"> EDI</span></span> |
|    <span data-ttu-id="8c48b-109">元件</span><span class="sxs-lookup"><span data-stu-id="8c48b-109">Component</span></span>    |                                       <span data-ttu-id="8c48b-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="8c48b-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="8c48b-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8c48b-111">Symbolic Name</span></span>  |                       <span data-ttu-id="8c48b-112">X12SegmentHasDataElementErrorsDescription</span><span class="sxs-lookup"><span data-stu-id="8c48b-112">X12SegmentHasDataElementErrorsDescription</span></span>                        |
|  <span data-ttu-id="8c48b-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8c48b-113">Message Text</span></span>   |                            <span data-ttu-id="8c48b-114">區段有資料項目錯誤</span><span class="sxs-lookup"><span data-stu-id="8c48b-114">Segment Has Data Element Errors</span></span>                             |
  
## <a name="explanation"></a><span data-ttu-id="8c48b-115">說明</span><span class="sxs-lookup"><span data-stu-id="8c48b-115">Explanation</span></span>  
 <span data-ttu-id="8c48b-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換包含區段包含文件結構描述不符合的資料元素。</span><span class="sxs-lookup"><span data-stu-id="8c48b-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained segments that included data elements that did not conform to the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8c48b-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8c48b-117">User Action</span></span>  
 <span data-ttu-id="8c48b-118">若要解決這個錯誤，請確定交換中的資料元素符合文件結構描述，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="8c48b-118">To resolve this error, make sure that the data elements in the interchange conform to the document schema, and then resend the interchange.</span></span>
---
title: "太多資料項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5000577d-5748-4e81-a394-86b2a780d70f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebf1fb61e4870b2a661876bf9375b3d3fe9abdd2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="too-many-data-elements"></a><span data-ttu-id="6c3f4-102">資料元素太多</span><span class="sxs-lookup"><span data-stu-id="6c3f4-102">Too many data elements</span></span>
## <a name="details"></a><span data-ttu-id="6c3f4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6c3f4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6c3f4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6c3f4-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6c3f4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="6c3f4-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="6c3f4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6c3f4-106">Event ID</span></span>|-|  
|<span data-ttu-id="6c3f4-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="6c3f4-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6c3f4-108">EDI</span><span class="sxs-lookup"><span data-stu-id="6c3f4-108"> EDI</span></span>|  
|<span data-ttu-id="6c3f4-109">元件</span><span class="sxs-lookup"><span data-stu-id="6c3f4-109">Component</span></span>|<span data-ttu-id="6c3f4-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="6c3f4-110">EDI Engine</span></span>|  
|<span data-ttu-id="6c3f4-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6c3f4-111">Symbolic Name</span></span>|<span data-ttu-id="6c3f4-112">X12DeTooManyDataElementsDescription</span><span class="sxs-lookup"><span data-stu-id="6c3f4-112">X12DeTooManyDataElementsDescription</span></span>|  
|<span data-ttu-id="6c3f4-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6c3f4-113">Message Text</span></span>|<span data-ttu-id="6c3f4-114">資料元素太多</span><span class="sxs-lookup"><span data-stu-id="6c3f4-114">Too many data elements</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6c3f4-115">說明</span><span class="sxs-lookup"><span data-stu-id="6c3f4-115">Explanation</span></span>  
 <span data-ttu-id="6c3f4-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，或傳送管線無法處理外寄交換，因為交換中的區段包含超過允許的更多的資料元素文件結構描述或服務結構描述。</span><span class="sxs-lookup"><span data-stu-id="6c3f4-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because a segment in the interchange contained more data elements than allowed by the document schema or the service schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6c3f4-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6c3f4-117">User Action</span></span>  
 <span data-ttu-id="6c3f4-118">若要解決這個錯誤，有交換傳送者確認區段包含的必要的資料元素，從區段，如有必要，移除多餘的資料元素，直到符合結構描述的區段數目。</span><span class="sxs-lookup"><span data-stu-id="6c3f4-118">To resolve this error, have the sender of the interchange ensure that segments include the required number of data elements, removing excess data elements from the segment if necessary, until the segment conforms to the schema.</span></span>
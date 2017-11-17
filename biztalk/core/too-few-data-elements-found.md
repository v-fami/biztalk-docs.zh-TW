---
title: "找到的資料元素太少 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6eca6c1-73ee-4b9a-be84-461051eda963
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8244f927cb7aff9cd0cb517dd132b986d53d67f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="too-few-data-elements-found"></a><span data-ttu-id="82f28-102">找到的資料元素太少</span><span class="sxs-lookup"><span data-stu-id="82f28-102">Too few data elements found</span></span>
## <a name="details"></a><span data-ttu-id="82f28-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="82f28-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="82f28-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="82f28-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="82f28-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="82f28-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="82f28-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="82f28-106">Event ID</span></span>|-|  
|<span data-ttu-id="82f28-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="82f28-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="82f28-108">EDI</span><span class="sxs-lookup"><span data-stu-id="82f28-108"> EDI</span></span>|  
|<span data-ttu-id="82f28-109">元件</span><span class="sxs-lookup"><span data-stu-id="82f28-109">Component</span></span>|<span data-ttu-id="82f28-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="82f28-110">EDI Engine</span></span>|  
|<span data-ttu-id="82f28-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="82f28-111">Symbolic Name</span></span>|<span data-ttu-id="82f28-112">X12FeTooFewDataElementsFoundDescription</span><span class="sxs-lookup"><span data-stu-id="82f28-112">X12FeTooFewDataElementsFoundDescription</span></span>|  
|<span data-ttu-id="82f28-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="82f28-113">Message Text</span></span>|<span data-ttu-id="82f28-114">找到的資料元素太少</span><span class="sxs-lookup"><span data-stu-id="82f28-114">Too few data elements found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="82f28-115">說明</span><span class="sxs-lookup"><span data-stu-id="82f28-115">Explanation</span></span>  
 <span data-ttu-id="82f28-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，或傳送管線無法處理外寄交換，因為交換中的區段包含較少的資料元素比要求文件結構描述或服務結構描述。</span><span class="sxs-lookup"><span data-stu-id="82f28-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because a segment in the interchange contained fewer data elements than required by the document schema or the service schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="82f28-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="82f28-117">User Action</span></span>  
 <span data-ttu-id="82f28-118">若要解決這個錯誤，有交換傳送者確定區段包含資料元素的必要的數目，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="82f28-118">To resolve this error, have the sender of the interchange ensure that segments include the required number of data elements, and then resend the interchange.</span></span>
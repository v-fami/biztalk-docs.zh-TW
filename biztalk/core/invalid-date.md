---
title: "無效的日期 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a41da9c5-9dcf-44cd-be5b-922e6c267ec3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 259456e781f5f5255f9fed8a51c8eb0569dd57b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-date"></a><span data-ttu-id="ae3bc-102">無效的日期</span><span class="sxs-lookup"><span data-stu-id="ae3bc-102">Invalid Date</span></span>
## <a name="details"></a><span data-ttu-id="ae3bc-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ae3bc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae3bc-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ae3bc-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ae3bc-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ae3bc-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ae3bc-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ae3bc-106">Event ID</span></span>|-|  
|<span data-ttu-id="ae3bc-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ae3bc-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ae3bc-108">EDI</span><span class="sxs-lookup"><span data-stu-id="ae3bc-108"> EDI</span></span>|  
|<span data-ttu-id="ae3bc-109">元件</span><span class="sxs-lookup"><span data-stu-id="ae3bc-109">Component</span></span>|<span data-ttu-id="ae3bc-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="ae3bc-110">EDI Engine</span></span>|  
|<span data-ttu-id="ae3bc-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ae3bc-111">Symbolic Name</span></span>|<span data-ttu-id="ae3bc-112">X12DeInvalidDateDescription</span><span class="sxs-lookup"><span data-stu-id="ae3bc-112">X12DeInvalidDateDescription</span></span>|  
|<span data-ttu-id="ae3bc-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ae3bc-113">Message Text</span></span>|<span data-ttu-id="ae3bc-114">無效的日期</span><span class="sxs-lookup"><span data-stu-id="ae3bc-114">Invalid Date</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ae3bc-115">說明</span><span class="sxs-lookup"><span data-stu-id="ae3bc-115">Explanation</span></span>  
 <span data-ttu-id="ae3bc-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，或傳送管線無法處理外寄交換，因為資料元素中的 date 值不符合所指定之資料類型EDI 結構描述或 GS04 欄位標頭服務結構描述不符合交換的 X12 中的日期值 (BaseArtifacts.dll 中的 X12ServiceSchema)。</span><span class="sxs-lookup"><span data-stu-id="ae3bc-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because a date value in a data element did not conform to the data type specified by the EDI schema or the date value in the GS04 field header in an X12 interchange did not conform to the service schema (X12ServiceSchema in BaseArtifacts.dll).</span></span> <span data-ttu-id="ae3bc-117">對於 X12，服務結構描述會定義日期為準，X12_DT 資料類型和長度為六個到八個字元之間的 GS04 欄位中。</span><span class="sxs-lookup"><span data-stu-id="ae3bc-117">For X12, the service schema defines a date in the GS04 field as of the X12_DT data type and between six and eight characters in length.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ae3bc-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ae3bc-118">User Action</span></span>  
 <span data-ttu-id="ae3bc-119">若要解決這個錯誤，請確定的時間中的資料元素的值符合 EDI 結構描述或 GS04 標頭的 X12 交換服務，符合結構描述中的日期值所指定的資料型別，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="ae3bc-119">To resolve this error, make sure that the time value in a data element conforms to the data type specified by the EDI schema or the date value in the GS04 header of an X12 interchange conforms to the service schema, and then have the interchange resent.</span></span>
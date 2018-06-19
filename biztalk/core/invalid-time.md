---
title: 無效的時間 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6942eb77-3ef1-460c-ac4f-8f1339c25d1b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aae508a945cc6934e83408b2a9b78c324947e0e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261974"
---
# <a name="invalid-time"></a><span data-ttu-id="3bc7c-102">無效的時間</span><span class="sxs-lookup"><span data-stu-id="3bc7c-102">Invalid Time</span></span>
## <a name="details"></a><span data-ttu-id="3bc7c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3bc7c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3bc7c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3bc7c-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3bc7c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3bc7c-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3bc7c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3bc7c-106">Event ID</span></span>|-|  
|<span data-ttu-id="3bc7c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="3bc7c-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3bc7c-108">EDI</span><span class="sxs-lookup"><span data-stu-id="3bc7c-108"> EDI</span></span>|  
|<span data-ttu-id="3bc7c-109">元件</span><span class="sxs-lookup"><span data-stu-id="3bc7c-109">Component</span></span>|<span data-ttu-id="3bc7c-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="3bc7c-110">EDI Engine</span></span>|  
|<span data-ttu-id="3bc7c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3bc7c-111">Symbolic Name</span></span>|<span data-ttu-id="3bc7c-112">X12Ta1InvalidTimeDescription</span><span class="sxs-lookup"><span data-stu-id="3bc7c-112">X12Ta1InvalidTimeDescription</span></span>|  
|<span data-ttu-id="3bc7c-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3bc7c-113">Message Text</span></span>|<span data-ttu-id="3bc7c-114">無效的時間</span><span class="sxs-lookup"><span data-stu-id="3bc7c-114">Invalid Time</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3bc7c-115">說明</span><span class="sxs-lookup"><span data-stu-id="3bc7c-115">Explanation</span></span>  
 <span data-ttu-id="3bc7c-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換的 EDI 結構描述或 GS05 欄位標頭在 X12 中的時間值所指定的資料類型不符合時間值中的資料元素因為服務結構描述不符合交換 (BaseArtifacts.dll 中的 X12ServiceSchema)。</span><span class="sxs-lookup"><span data-stu-id="3bc7c-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because a time value in a data element did not conform to the data type specified by the EDI schema or the time value in the GS05 field header in an X12 interchange did not conform to the service schema (X12ServiceSchema in BaseArtifacts.dll).</span></span> <span data-ttu-id="3bc7c-117">對於 X12，服務結構描述會定義時間為準，X12_TM 資料類型，及介於四到八個字元的長度 GS05 欄位中。</span><span class="sxs-lookup"><span data-stu-id="3bc7c-117">For X12, the service schema defines a time in the GS05 field as of the X12_TM data type and between four and eight characters in length.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3bc7c-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3bc7c-118">User Action</span></span>  
 <span data-ttu-id="3bc7c-119">若要解決這個錯誤，請確定時間，資料元素中的值符合 EDI 結構描述或 GS05 標頭的 X12 交換服務，符合結構描述中的時間值所指定的資料型別，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="3bc7c-119">To resolve this error, make sure that a time value in a data element conforms to the data type specified by the EDI schema or a time value in the GS05 header of an X12 interchange conforms to the service schema, and then have the interchange resent.</span></span>
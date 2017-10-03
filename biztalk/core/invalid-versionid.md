---
title: "無效的 VersionId |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 563af6e8-f496-46c9-8b5f-7b941b2d08a5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5edd2dddc5df19d99c434ec60cad46664ba378e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-versionid"></a><span data-ttu-id="ac30d-102">無效的 VersionId</span><span class="sxs-lookup"><span data-stu-id="ac30d-102">Invalid VersionId</span></span>
## <a name="details"></a><span data-ttu-id="ac30d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ac30d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ac30d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ac30d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ac30d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ac30d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ac30d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ac30d-106">Event ID</span></span>|-|  
|<span data-ttu-id="ac30d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ac30d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ac30d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="ac30d-108"> EDI</span></span>|  
|<span data-ttu-id="ac30d-109">元件</span><span class="sxs-lookup"><span data-stu-id="ac30d-109">Component</span></span>|<span data-ttu-id="ac30d-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="ac30d-110">EDI Engine</span></span>|  
|<span data-ttu-id="ac30d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ac30d-111">Symbolic Name</span></span>|<span data-ttu-id="ac30d-112">X12Ta1InvalidVersionIdDescription</span><span class="sxs-lookup"><span data-stu-id="ac30d-112">X12Ta1InvalidVersionIdDescription</span></span>|  
|<span data-ttu-id="ac30d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ac30d-113">Message Text</span></span>|<span data-ttu-id="ac30d-114">無效的 VersionId</span><span class="sxs-lookup"><span data-stu-id="ac30d-114">Invalid VersionId</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ac30d-115">說明</span><span class="sxs-lookup"><span data-stu-id="ac30d-115">Explanation</span></span>  
 <span data-ttu-id="ac30d-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換，因為交換中的版本識別項 (GS08 欄位中的 X12 交換] 或 [EDIFACT 交換中的 [UNG7] 欄位) 不提供支援符合的資料類型和服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立的數字的數目。</span><span class="sxs-lookup"><span data-stu-id="ac30d-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the version identifier in the interchange (the GS08 field in an X12 interchange or the UNG7 field in an EDIFACT interchange) did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span> <span data-ttu-id="ac30d-117">GS08 欄位必須是 X12_AN 資料類型，而且介於 1 到 12 的數字。</span><span class="sxs-lookup"><span data-stu-id="ac30d-117">The GS08 field must be of the X12_AN data type and between 1 and 12 digits.</span></span> <span data-ttu-id="ac30d-118">UNG7.1 中的版本必須是 EDIFACT_AN 資料類型，而且介於 1 到 3 的數字。</span><span class="sxs-lookup"><span data-stu-id="ac30d-118">The version in UNG7.1 must be of the EDIFACT_AN data type and between 1 and 3 digits.</span></span> <span data-ttu-id="ac30d-119">EDIFACT_AN 資料型別且 1 和 3 個數字之間，必須是 UNG7.2 中的發行。</span><span class="sxs-lookup"><span data-stu-id="ac30d-119">The release in UNG7.2 must be of the EDIFACT_AN data type and between 1 and 3 digits.</span></span> <span data-ttu-id="ac30d-120">關聯指派碼 UNG7.3 中的必須是 EDIFACT_AN 資料類型，而且介於 1 到 6 的數字。</span><span class="sxs-lookup"><span data-stu-id="ac30d-120">The Association assigned code in UNG7.3 must be of the EDIFACT_AN data type and between 1 and 6 digits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ac30d-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ac30d-121">User Action</span></span>  
 <span data-ttu-id="ac30d-122">若要解決這個錯誤，請確定在 GS08 或 UNG7 版本符合的資料類型和服務結構描述所指定的位數，而且再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="ac30d-122">To resolve this error, make sure that the version in GS08 or UNG7 conforms to the data type and number of digits specified by the service schema, and then have the interchange resent.</span></span>
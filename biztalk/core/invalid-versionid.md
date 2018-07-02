---
title: 無效的 VersionId |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 563af6e8-f496-46c9-8b5f-7b941b2d08a5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b845c2d7380667ca05bba3567175df04479ae9a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976151"
---
# <a name="invalid-versionid"></a><span data-ttu-id="2a74b-102">無效的 VersionId</span><span class="sxs-lookup"><span data-stu-id="2a74b-102">Invalid VersionId</span></span>
## <a name="details"></a><span data-ttu-id="2a74b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2a74b-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="2a74b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2a74b-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="2a74b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="2a74b-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="2a74b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2a74b-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="2a74b-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="2a74b-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2a74b-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="2a74b-108"> EDI</span></span> |
|    <span data-ttu-id="2a74b-109">元件</span><span class="sxs-lookup"><span data-stu-id="2a74b-109">Component</span></span>    |                                       <span data-ttu-id="2a74b-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="2a74b-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="2a74b-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2a74b-111">Symbolic Name</span></span>  |                           <span data-ttu-id="2a74b-112">X12Ta1InvalidVersionIdDescription</span><span class="sxs-lookup"><span data-stu-id="2a74b-112">X12Ta1InvalidVersionIdDescription</span></span>                            |
|  <span data-ttu-id="2a74b-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2a74b-113">Message Text</span></span>   |                                   <span data-ttu-id="2a74b-114">無效的 VersionId</span><span class="sxs-lookup"><span data-stu-id="2a74b-114">Invalid VersionId</span></span>                                    |
  
## <a name="explanation"></a><span data-ttu-id="2a74b-115">說明</span><span class="sxs-lookup"><span data-stu-id="2a74b-115">Explanation</span></span>  
 <span data-ttu-id="2a74b-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中的版本識別項 (GS08 欄位中的 X12 交換 或 EDIFACT 交換中的 UNG7 欄位) 不提供支援符合的資料類型和服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立的數字數目。</span><span class="sxs-lookup"><span data-stu-id="2a74b-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the version identifier in the interchange (the GS08 field in an X12 interchange or the UNG7 field in an EDIFACT interchange) did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span> <span data-ttu-id="2a74b-117">如果是 X12_AN 資料型別，而且介於 1 到 12 個數字之間，必須是 GS08 欄位。</span><span class="sxs-lookup"><span data-stu-id="2a74b-117">The GS08 field must be of the X12_AN data type and between 1 and 12 digits.</span></span> <span data-ttu-id="2a74b-118">UNG7.1 中的版本必須是 EDIFACT_AN 資料型別，而且介於 1 到 3 個數字之間。</span><span class="sxs-lookup"><span data-stu-id="2a74b-118">The version in UNG7.1 must be of the EDIFACT_AN data type and between 1 and 3 digits.</span></span> <span data-ttu-id="2a74b-119">發行的 UNG7.2 必須 EDIFACT_AN 資料型別，而且介於 1 到 3 個數字之間。</span><span class="sxs-lookup"><span data-stu-id="2a74b-119">The release in UNG7.2 must be of the EDIFACT_AN data type and between 1 and 3 digits.</span></span> <span data-ttu-id="2a74b-120">關聯指定代碼在 UNG7.3 必須 EDIFACT_AN 資料型別，而且 1 到 6 位數字之間。</span><span class="sxs-lookup"><span data-stu-id="2a74b-120">The Association assigned code in UNG7.3 must be of the EDIFACT_AN data type and between 1 and 6 digits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2a74b-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2a74b-121">User Action</span></span>  
 <span data-ttu-id="2a74b-122">若要解決這個錯誤，請確定在 GS08 或 UNG7 版本符合的資料類型和服務結構描述所指定的數字的數目，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="2a74b-122">To resolve this error, make sure that the version in GS08 or UNG7 conforms to the data type and number of digits specified by the service schema, and then have the interchange resent.</span></span>
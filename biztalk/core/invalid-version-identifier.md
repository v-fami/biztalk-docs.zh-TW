---
title: 無效的版本識別碼 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 504b0b16-7d23-45ef-ae2a-ce1962b83f34
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de725a51ba89312c7cb394e249c1ef40353f256b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022852"
---
# <a name="invalid-version-identifier"></a><span data-ttu-id="02a74-102">無效的版本識別碼</span><span class="sxs-lookup"><span data-stu-id="02a74-102">Invalid Version Identifier</span></span>
## <a name="details"></a><span data-ttu-id="02a74-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="02a74-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="02a74-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="02a74-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="02a74-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="02a74-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="02a74-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="02a74-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="02a74-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="02a74-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="02a74-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="02a74-108"> EDI</span></span> |
|    <span data-ttu-id="02a74-109">元件</span><span class="sxs-lookup"><span data-stu-id="02a74-109">Component</span></span>    |                                       <span data-ttu-id="02a74-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="02a74-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="02a74-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="02a74-111">Symbolic Name</span></span>  |                       <span data-ttu-id="02a74-112">X12Ta1InvalidVersionIdentifierDescription</span><span class="sxs-lookup"><span data-stu-id="02a74-112">X12Ta1InvalidVersionIdentifierDescription</span></span>                        |
|  <span data-ttu-id="02a74-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="02a74-113">Message Text</span></span>   |                               <span data-ttu-id="02a74-114">無效的版本識別碼</span><span class="sxs-lookup"><span data-stu-id="02a74-114">Invalid Version Identifier</span></span>                               |
  
## <a name="explanation"></a><span data-ttu-id="02a74-115">說明</span><span class="sxs-lookup"><span data-stu-id="02a74-115">Explanation</span></span>  
 <span data-ttu-id="02a74-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中的版本識別項 (GS08 欄位中的 X12 交換 或 EDIFACT 交換中的 UNG7 欄位) 不提供支援符合的資料類型和服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立的數字數目。</span><span class="sxs-lookup"><span data-stu-id="02a74-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the version identifier in the interchange (the GS08 field in an X12 interchange or the UNG7 field in an EDIFACT interchange) did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span> <span data-ttu-id="02a74-117">如果是 X12_AN 資料型別，而且介於 1 到 12 個數字之間，必須是 GS08 欄位。</span><span class="sxs-lookup"><span data-stu-id="02a74-117">The GS08 field must be of the X12_AN data type and between 1 and 12 digits.</span></span> <span data-ttu-id="02a74-118">UNG7.1 中的版本必須是 EDIFACT_AN 資料型別，而且介於 1 到 3 個數字之間。</span><span class="sxs-lookup"><span data-stu-id="02a74-118">The version in UNG7.1 must be of the EDIFACT_AN data type and between 1 and 3 digits.</span></span> <span data-ttu-id="02a74-119">發行的 UNG7.2 必須 EDIFACT_AN 資料型別，而且介於 1 到 3 個數字之間。</span><span class="sxs-lookup"><span data-stu-id="02a74-119">The release in UNG7.2 must be of the EDIFACT_AN data type and between 1 and 3 digits.</span></span> <span data-ttu-id="02a74-120">關聯指定代碼在 UNG7.3 必須 EDIFACT_AN 資料型別，而且 1 到 6 位數字之間。</span><span class="sxs-lookup"><span data-stu-id="02a74-120">The Association assigned code in UNG7.3 must be of the EDIFACT_AN data type and between 1 and 6 digits.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="02a74-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="02a74-121">User Action</span></span>  
 <span data-ttu-id="02a74-122">若要解決這個錯誤，請確定在 GS08 或 UNG7 版本符合的資料類型和服務結構描述所指定的數字的數目，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="02a74-122">To resolve this error, make sure that the version in GS08 or UNG7 conforms to the data type and number of digits specified by the service schema, and then have the interchange resent.</span></span>
---
title: 無效的安全性值 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee380da7-c05e-4b9b-84ee-f7ffee90eb0e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d5c8cd6f07449ba426a9cb17f9f4aa880ff1b3e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013743"
---
# <a name="invalid-security-value"></a><span data-ttu-id="4907d-102">無效的安全性值</span><span class="sxs-lookup"><span data-stu-id="4907d-102">Invalid Security Value</span></span>
## <a name="details"></a><span data-ttu-id="4907d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4907d-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="4907d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4907d-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="4907d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="4907d-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="4907d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4907d-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="4907d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="4907d-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4907d-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="4907d-108"> EDI</span></span> |
|    <span data-ttu-id="4907d-109">元件</span><span class="sxs-lookup"><span data-stu-id="4907d-109">Component</span></span>    |                                       <span data-ttu-id="4907d-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="4907d-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="4907d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4907d-111">Symbolic Name</span></span>  |                         <span data-ttu-id="4907d-112">X12Ta1InvalidSecurityValueDescription</span><span class="sxs-lookup"><span data-stu-id="4907d-112">X12Ta1InvalidSecurityValueDescription</span></span>                          |
|  <span data-ttu-id="4907d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4907d-113">Message Text</span></span>   |                                 <span data-ttu-id="4907d-114">無效的安全性值</span><span class="sxs-lookup"><span data-stu-id="4907d-114">Invalid Security Value</span></span>                                 |
  
## <a name="explanation"></a><span data-ttu-id="4907d-115">說明</span><span class="sxs-lookup"><span data-stu-id="4907d-115">Explanation</span></span>  
 <span data-ttu-id="4907d-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為 ISA04 欄位中的安全性資訊或收件者參考密碼值，在 [UNB6.1] 欄位不符合的資料類型和服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立的數字數目。</span><span class="sxs-lookup"><span data-stu-id="4907d-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the Security Information in the ISA04 field or the Recipient Reference Password Value in the UNB6.1 field did not conform to the data type and number of digits established by the service schema (X12ServiceSchema or the EdifactServiceSchema in BaseArtifacts.dll).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4907d-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4907d-117">User Action</span></span>  
 <span data-ttu-id="4907d-118">若要解決這個錯誤，請確定 ISA04 欄位是 X12_AN 資料類型，而是 10 個字元長度 （不論有無結尾的空格），或 UNB6.1 欄位 EDIFACT_AN 資料類型，且是介於 1 到 14 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="4907d-118">To resolve this error, make sure that the ISA04 field is of the X12_AN data type and is 10 characters long (with or without trailing spaces) or that the UNB6.1 field is of the EDIFACT_AN data type and is between 1 and 14 characters long.</span></span> <span data-ttu-id="4907d-119">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="4907d-119">Have the interchange resent.</span></span>
---
title: UNA 區段無效。 它未包含 6 個欄位 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c939d8d3-e6fb-4505-836d-31559fc5f1a3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 469ce2e3d8b82b876053df93bb66fbea0ec1354f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001687"
---
# <a name="una-segment-is-invalid-it-did-not-contain-6-fields"></a><span data-ttu-id="53fa5-103">UNA 區段無效。</span><span class="sxs-lookup"><span data-stu-id="53fa5-103">UNA segment is invalid.</span></span> <span data-ttu-id="53fa5-104">它未包含 6 個欄位</span><span class="sxs-lookup"><span data-stu-id="53fa5-104">It did not contain 6 fields</span></span>
## <a name="details"></a><span data-ttu-id="53fa5-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="53fa5-105">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="53fa5-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="53fa5-106">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="53fa5-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="53fa5-107">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="53fa5-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="53fa5-108">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="53fa5-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="53fa5-109">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="53fa5-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="53fa5-110"> EDI</span></span> |
|    <span data-ttu-id="53fa5-111">元件</span><span class="sxs-lookup"><span data-stu-id="53fa5-111">Component</span></span>    |                                       <span data-ttu-id="53fa5-112">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="53fa5-112">EDI Engine</span></span>                                       |
|  <span data-ttu-id="53fa5-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="53fa5-113">Symbolic Name</span></span>  |                             <span data-ttu-id="53fa5-114">UnaDidNotContainSixDelimiters</span><span class="sxs-lookup"><span data-stu-id="53fa5-114">UnaDidNotContainSixDelimiters</span></span>                              |
|  <span data-ttu-id="53fa5-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="53fa5-115">Message Text</span></span>   |                  <span data-ttu-id="53fa5-116">UNA 區段無效。</span><span class="sxs-lookup"><span data-stu-id="53fa5-116">UNA segment is invalid.</span></span> <span data-ttu-id="53fa5-117">它未包含 6 個欄位</span><span class="sxs-lookup"><span data-stu-id="53fa5-117">It did not contain 6 fields</span></span>                   |
  
## <a name="explanation"></a><span data-ttu-id="53fa5-118">說明</span><span class="sxs-lookup"><span data-stu-id="53fa5-118">Explanation</span></span>  
 <span data-ttu-id="53fa5-119">這個錯誤/警告/資訊事件表示，接收管線無法處理內送 EDIFACT 交換因為 UNA 區段包含少於六個資料元素。</span><span class="sxs-lookup"><span data-stu-id="53fa5-119">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming EDIFACT interchange because the UNA segment contained fewer than six data elements.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="53fa5-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="53fa5-120">User Action</span></span>  
 <span data-ttu-id="53fa5-121">若要解決這個錯誤，必須交換傳送者確定 UNA 區段包含六個資料元素，然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="53fa5-121">To resolve this error, have the sender of the interchange make sure that the UNA segment contains six data elements, and then resend the interchange.</span></span>
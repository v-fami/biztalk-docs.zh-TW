---
title: 無效的區段結束字元 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 508dac21-4731-439d-bf4a-a50858f1ffa0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0249c16bf495f9103759ec4eba9a9c6776b87ca2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001823"
---
# <a name="invalid-segment-terminator"></a><span data-ttu-id="c05d9-102">無效的區段結束字元</span><span class="sxs-lookup"><span data-stu-id="c05d9-102">Invalid Segment Terminator</span></span>
## <a name="details"></a><span data-ttu-id="c05d9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c05d9-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="c05d9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c05d9-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="c05d9-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c05d9-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="c05d9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c05d9-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="c05d9-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="c05d9-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c05d9-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c05d9-108"> EDI</span></span> |
|    <span data-ttu-id="c05d9-109">元件</span><span class="sxs-lookup"><span data-stu-id="c05d9-109">Component</span></span>    |                                       <span data-ttu-id="c05d9-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="c05d9-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="c05d9-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c05d9-111">Symbolic Name</span></span>  |                       <span data-ttu-id="c05d9-112">X12Ta1InvalidSegmentTerminatorDescription</span><span class="sxs-lookup"><span data-stu-id="c05d9-112">X12Ta1InvalidSegmentTerminatorDescription</span></span>                        |
|  <span data-ttu-id="c05d9-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c05d9-113">Message Text</span></span>   |                               <span data-ttu-id="c05d9-114">無效的區段結束字元</span><span class="sxs-lookup"><span data-stu-id="c05d9-114">Invalid Segment Terminator</span></span>                               |
  
## <a name="explanation"></a><span data-ttu-id="c05d9-115">說明</span><span class="sxs-lookup"><span data-stu-id="c05d9-115">Explanation</span></span>  
 <span data-ttu-id="c05d9-116">這個錯誤/警告/資訊事件表示，由於內送交換中的區段結束字元值有 ASCII 字元集之外的字元，因此接收管線無法處理該交換。</span><span class="sxs-lookup"><span data-stu-id="c05d9-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the segment terminator in the interchange was not limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="c05d9-117">在 X12 中，區段結束字元定義為 ISA 區段的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="c05d9-117">In X12, the segment terminator is defined as the last character in the ISA segment.</span></span> <span data-ttu-id="c05d9-118">在 EDIFACT 中，區段結束字元是 [UNA6] 欄位。</span><span class="sxs-lookup"><span data-stu-id="c05d9-118">In EDIFACT, the segment terminator is the UNA6 field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c05d9-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c05d9-119">User Action</span></span>  
 <span data-ttu-id="c05d9-120">若要解決這個錯誤，請確認區段結束字元 (X12 交換中 ISA 區段的最後一個字元，或 EDIFACT 交換中的 [UNA6] 欄位) 皆為 ASCII 字元集中的字元。</span><span class="sxs-lookup"><span data-stu-id="c05d9-120">To resolve this error, make sure that the segment terminator (the last character of the ISA segment in an X12 interchange or the UNA6 field in an EDIFACT interchange) is limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="c05d9-121">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="c05d9-121">Have the interchange resent.</span></span>
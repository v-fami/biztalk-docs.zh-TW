---
title: 無效的元件元素分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 738a1107-86e6-4475-a61d-ed1d9ab7e5d2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 927a33124fdb624df79d3b2f99b07f61345289e9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997551"
---
# <a name="invalid-component-element-separator"></a><span data-ttu-id="bb5d4-102">無效的元件元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="bb5d4-102">Invalid Component Element Separator</span></span>
## <a name="details"></a><span data-ttu-id="bb5d4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="bb5d4-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="bb5d4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="bb5d4-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="bb5d4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="bb5d4-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="bb5d4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="bb5d4-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="bb5d4-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="bb5d4-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bb5d4-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="bb5d4-108"> EDI</span></span> |
|    <span data-ttu-id="bb5d4-109">元件</span><span class="sxs-lookup"><span data-stu-id="bb5d4-109">Component</span></span>    |                                       <span data-ttu-id="bb5d4-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="bb5d4-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="bb5d4-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="bb5d4-111">Symbolic Name</span></span>  |                   <span data-ttu-id="bb5d4-112">X12Ta1InvalidComponentElementSeparatorDescription\\</span><span class="sxs-lookup"><span data-stu-id="bb5d4-112">X12Ta1InvalidComponentElementSeparatorDescription\\</span></span>                   |
|  <span data-ttu-id="bb5d4-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="bb5d4-113">Message Text</span></span>   |                          <span data-ttu-id="bb5d4-114">無效的元件元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="bb5d4-114">Invalid Component Element Separator</span></span>                           |
  
## <a name="explanation"></a><span data-ttu-id="bb5d4-115">說明</span><span class="sxs-lookup"><span data-stu-id="bb5d4-115">Explanation</span></span>  
 <span data-ttu-id="bb5d4-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中的元件分隔符號的值不是限制為 ASCII 字元集中的字元。</span><span class="sxs-lookup"><span data-stu-id="bb5d4-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the component separator in the interchange was not limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="bb5d4-117">在 X12 中，區段結束字元是 [ISA16] 欄位。</span><span class="sxs-lookup"><span data-stu-id="bb5d4-117">In X12, the segment terminator is the ISA16 field.</span></span> <span data-ttu-id="bb5d4-118">在 EDIFACT 中，區段結束字元是 UNA1 欄位。</span><span class="sxs-lookup"><span data-stu-id="bb5d4-118">In EDIFACT, the segment terminator is the UNA1 field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="bb5d4-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="bb5d4-119">User Action</span></span>  
 <span data-ttu-id="bb5d4-120">若要解決這個錯誤，請確認區段結束字元 (ISA16 欄位中的 X12 交換 或 UNA1 欄位，EDIFACT 交換中的) 僅限於 ASCII 字元集中的字元。</span><span class="sxs-lookup"><span data-stu-id="bb5d4-120">To resolve this error, make sure that the segment terminator (the ISA16 field in an X12 interchange or the UNA1 field in an EDIFACT interchange) is limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="bb5d4-121">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="bb5d4-121">Have the interchange resent.</span></span>
---
title: "無效的資料元素分隔符號 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c50a8b-274f-4f4a-9826-4f6f8123e9d1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d83b8ce3099ebb940507d391881cfd92cde5034d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-data-element-separator"></a><span data-ttu-id="21701-102">無效的資料元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="21701-102">Invalid Data Element Separator</span></span>
## <a name="details"></a><span data-ttu-id="21701-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="21701-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21701-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="21701-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="21701-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="21701-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="21701-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="21701-106">Event ID</span></span>|-|  
|<span data-ttu-id="21701-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="21701-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="21701-108">EDI</span><span class="sxs-lookup"><span data-stu-id="21701-108"> EDI</span></span>|  
|<span data-ttu-id="21701-109">元件</span><span class="sxs-lookup"><span data-stu-id="21701-109">Component</span></span>|<span data-ttu-id="21701-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="21701-110">EDI Engine</span></span>|  
|<span data-ttu-id="21701-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="21701-111">Symbolic Name</span></span>|<span data-ttu-id="21701-112">X12Ta1InvalidDataElementSeparatorDescription</span><span class="sxs-lookup"><span data-stu-id="21701-112">X12Ta1InvalidDataElementSeparatorDescription</span></span>|  
|<span data-ttu-id="21701-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="21701-113">Message Text</span></span>|<span data-ttu-id="21701-114">無效的資料元素分隔符號</span><span class="sxs-lookup"><span data-stu-id="21701-114">Invalid Data Element Separator</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="21701-115">說明</span><span class="sxs-lookup"><span data-stu-id="21701-115">Explanation</span></span>  
 <span data-ttu-id="21701-116">這個錯誤/警告/資訊事件表示，由於內送交換中的區段結束字元值有 ASCII 字元集之外的字元，因此接收管線無法處理該交換。</span><span class="sxs-lookup"><span data-stu-id="21701-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the segment terminator in the interchange was not limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="21701-117">在 X12 中，區段結束字元定義為 ISA 區段中的第四個字元。</span><span class="sxs-lookup"><span data-stu-id="21701-117">In X12, the segment terminator is defined as the fourth character in the ISA segment.</span></span> <span data-ttu-id="21701-118">在 EDIFACT 中，區段結束字元是 UNA2 欄位。</span><span class="sxs-lookup"><span data-stu-id="21701-118">In EDIFACT, the segment terminator is the UNA2 field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="21701-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="21701-119">User Action</span></span>  
 <span data-ttu-id="21701-120">若要解決這個錯誤，請確定區段結束字元 (x12 ISA 區段的第四個字元的交換或 UNA2 欄位，EDIFACT 交換中的) 限制為 ASCII 字元集中的字元。</span><span class="sxs-lookup"><span data-stu-id="21701-120">To resolve this error, make sure that the segment terminator (the fourth character of the ISA segment in an X12 interchange or the UNA2 field in an EDIFACT interchange) is limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="21701-121">重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="21701-121">Have the interchange resent.</span></span>
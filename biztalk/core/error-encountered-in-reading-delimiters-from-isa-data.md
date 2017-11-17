---
title: "讀取 ISA 資料分隔符號中發生錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cb60abd-53c8-45e1-a840-d27dc974aad7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fcde2519740adc5531363911146164f460f9b3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-in-reading-delimiters-from-isa-data"></a><span data-ttu-id="5d5ac-102">讀取 ISA 資料分隔符號中發生錯誤</span><span class="sxs-lookup"><span data-stu-id="5d5ac-102">Error encountered in reading delimiters from ISA data</span></span>
## <a name="details"></a><span data-ttu-id="5d5ac-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5d5ac-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d5ac-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5d5ac-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5d5ac-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="5d5ac-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5d5ac-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5d5ac-106">Event ID</span></span>|-|  
|<span data-ttu-id="5d5ac-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="5d5ac-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5d5ac-108">EDI</span><span class="sxs-lookup"><span data-stu-id="5d5ac-108"> EDI</span></span>|  
|<span data-ttu-id="5d5ac-109">元件</span><span class="sxs-lookup"><span data-stu-id="5d5ac-109">Component</span></span>|<span data-ttu-id="5d5ac-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="5d5ac-110">EDI Engine</span></span>|  
|<span data-ttu-id="5d5ac-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5d5ac-111">Symbolic Name</span></span>|<span data-ttu-id="5d5ac-112">InvalidIsaData</span><span class="sxs-lookup"><span data-stu-id="5d5ac-112">InvalidIsaData</span></span>|  
|<span data-ttu-id="5d5ac-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5d5ac-113">Message Text</span></span>|<span data-ttu-id="5d5ac-114">讀取 ISA 資料分隔符號中發生錯誤</span><span class="sxs-lookup"><span data-stu-id="5d5ac-114">Error encountered in reading delimiters from ISA data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5d5ac-115">說明</span><span class="sxs-lookup"><span data-stu-id="5d5ac-115">Explanation</span></span>  
 <span data-ttu-id="5d5ac-116">這個錯誤/警告/資訊事件表示 EDI 接收管線發生錯誤時正在處理內送 X12 交換因為無法剖析從 ISA 區段的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="5d5ac-116">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when processing an incoming X12 interchange because it could not parse the separators from the ISA segment.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5d5ac-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5d5ac-117">User Action</span></span>  
 <span data-ttu-id="5d5ac-118">若要解決這個錯誤，請確認內送交換的 ISA 區段中的分隔符號是唯一且有效。</span><span class="sxs-lookup"><span data-stu-id="5d5ac-118">To resolve this error, verify that the separators in the ISA segment of the incoming interchange are unique and valid.</span></span> <span data-ttu-id="5d5ac-119">否則，請將傳送者交換的唯一且有效的值輸入至每個分隔符號欄位 （ISA11 區段做為重複分隔符號與 ISA16 區段的元件分隔符號），然後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="5d5ac-119">If not, have the sender of the interchange enter unique and valid values into each of the separator fields (the ISA11 segment for the repetition separator and the ISA16 segment for the component separator), and then resend the interchange.</span></span>
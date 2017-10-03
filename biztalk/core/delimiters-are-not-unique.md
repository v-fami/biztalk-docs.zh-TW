---
title: "不是唯一分隔符號 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c37cc55-8923-4124-9004-91ee5093df9c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cc4f9c8eeb3a16fdd45222313bfb013dbf32ae5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique"></a><span data-ttu-id="ed3bf-102">不是唯一分隔符號</span><span class="sxs-lookup"><span data-stu-id="ed3bf-102">Delimiters are not unique</span></span>
## <a name="details"></a><span data-ttu-id="ed3bf-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ed3bf-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ed3bf-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ed3bf-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ed3bf-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="ed3bf-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ed3bf-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ed3bf-106">Event ID</span></span>|-|  
|<span data-ttu-id="ed3bf-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="ed3bf-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ed3bf-108">EDI</span><span class="sxs-lookup"><span data-stu-id="ed3bf-108"> EDI</span></span>|  
|<span data-ttu-id="ed3bf-109">元件</span><span class="sxs-lookup"><span data-stu-id="ed3bf-109">Component</span></span>|<span data-ttu-id="ed3bf-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="ed3bf-110">EDI Engine</span></span>|  
|<span data-ttu-id="ed3bf-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ed3bf-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="ed3bf-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ed3bf-112">Message Text</span></span>|<span data-ttu-id="ed3bf-113">不是唯一分隔符號</span><span class="sxs-lookup"><span data-stu-id="ed3bf-113">Delimiters are not unique</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ed3bf-114">說明</span><span class="sxs-lookup"><span data-stu-id="ed3bf-114">Explanation</span></span>  
 <span data-ttu-id="ed3bf-115">這個錯誤/警告/資訊事件表示，EDI 傳送管線無法處理外寄交換因為兩個或多個分隔符號的交換，識別，且用來分隔的交換，facet 都相同。</span><span class="sxs-lookup"><span data-stu-id="ed3bf-115">This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because two or more of the separators identified in the interchange, and used to separate facets of the interchange, were the same.</span></span> <span data-ttu-id="ed3bf-116">X12 的 ISA 區段中所識別的分隔符號交換和 EDIFACT 的 UNA 區段中交換。</span><span class="sxs-lookup"><span data-stu-id="ed3bf-116">The separators are identified in the ISA segment of an X12 interchange and in the UNA segment of an EDIFACT interchange.</span></span> <span data-ttu-id="ed3bf-117">保留批次的情況下，可能會發生兩個或多個具有相同值的分隔符號或交換是透過傳遞傳輸接收，然後挑選向上為 MessageBox 中 XML 檔案傳送埠。</span><span class="sxs-lookup"><span data-stu-id="ed3bf-117">Two or more separators with the same value can occur in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.</span></span> <span data-ttu-id="ed3bf-118">這個錯誤狀況會導致失敗之交換的處理。</span><span class="sxs-lookup"><span data-stu-id="ed3bf-118">This error condition will cause processing of the interchange to fail.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ed3bf-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ed3bf-119">User Action</span></span>  
 <span data-ttu-id="ed3bf-120">若要解決這個錯誤，找出交換內的分隔符號有相同的值，並變更其中一個分隔符號的值。</span><span class="sxs-lookup"><span data-stu-id="ed3bf-120">To resolve this error, identify which separators in the interchange have the same value, and change the value of one of the separators.</span></span>
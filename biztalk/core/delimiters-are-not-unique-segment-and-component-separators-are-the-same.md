---
title: "不是唯一分隔符號，區段和元件分隔符號相同 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13c41899-02af-4678-a4ad-f3dc48c1fdfb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69475949b404474ff4dc9fe53d553c24e125939c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique-segment-and-component-separators-are-the-same"></a><span data-ttu-id="0b035-102">不是唯一分隔符號，區段和元件分隔符號相同</span><span class="sxs-lookup"><span data-stu-id="0b035-102">Delimiters are not unique, segment and component separators are the same</span></span>
## <a name="details"></a><span data-ttu-id="0b035-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0b035-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0b035-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0b035-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0b035-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0b035-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0b035-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0b035-106">Event ID</span></span>|-|  
|<span data-ttu-id="0b035-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="0b035-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0b035-108">EDI</span><span class="sxs-lookup"><span data-stu-id="0b035-108"> EDI</span></span>|  
|<span data-ttu-id="0b035-109">元件</span><span class="sxs-lookup"><span data-stu-id="0b035-109">Component</span></span>|<span data-ttu-id="0b035-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="0b035-110">EDI Engine</span></span>|  
|<span data-ttu-id="0b035-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0b035-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="0b035-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0b035-112">Message Text</span></span>|<span data-ttu-id="0b035-113">不是唯一分隔符號，區段和元件分隔符號相同</span><span class="sxs-lookup"><span data-stu-id="0b035-113">Delimiters are not unique, segment and component separators are the same</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0b035-114">說明</span><span class="sxs-lookup"><span data-stu-id="0b035-114">Explanation</span></span>  
 <span data-ttu-id="0b035-115">這個錯誤/警告/資訊事件表示，EDI 傳送管線無法處理外寄交換因為區段結束字元或元件分隔符號相同的值。</span><span class="sxs-lookup"><span data-stu-id="0b035-115">This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because the segment terminator or the component separator were the same value.</span></span> <span data-ttu-id="0b035-116">在 X12 交換，區段結束字元是最後一個字元位置的 ISA 區段中的字元和元件分隔符號是 ISA16 欄位中的字元。</span><span class="sxs-lookup"><span data-stu-id="0b035-116">In an X12 interchange, the segment terminator is character in the last character position of the ISA segment and the component separator is the character in the ISA16 field.</span></span> <span data-ttu-id="0b035-117">在 EDIFACT 交換中，區段結束字元是 [UNA6] 欄位中的字元和元件分隔符號是 UNA1 欄位中的字元。</span><span class="sxs-lookup"><span data-stu-id="0b035-117">In an EDIFACT interchange, the segment terminator is the character in the UNA6 field and the component separator is the character in the UNA1 field.</span></span> <span data-ttu-id="0b035-118">兩個具有相同值的分隔符號可能 （但會導致錯誤狀況） 中保留的批次的案例中，或交換是透過傳遞傳輸接收，然後挑選向上為 MessageBox 中 XML 檔案傳送埠。</span><span class="sxs-lookup"><span data-stu-id="0b035-118">Two separators with the same value can occur (but will cause an error condition) in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0b035-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0b035-119">User Action</span></span>  
 <span data-ttu-id="0b035-120">若要解決這個錯誤，區段結束字元或交換中的元件分隔符號的值變更，然後再重新送出交換。</span><span class="sxs-lookup"><span data-stu-id="0b035-120">To resolve this error, change the value of either the segment terminator or the component separator in the interchange, and then resubmit the interchange.</span></span>
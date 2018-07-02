---
title: 不是唯一分隔符號，欄位及區段分隔符號相同 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1441434a-e969-4803-8e44-c7738d9b23ed
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff43a9b86fc39589cd513c82c5d9bed9055f5902
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969527"
---
# <a name="delimiters-are-not-unique-field-and-segment-separator-are-the-same"></a><span data-ttu-id="d1dda-102">分隔符號不是唯一的，欄位及區段的分隔符號相同</span><span class="sxs-lookup"><span data-stu-id="d1dda-102">Delimiters are not unique, field and segment separator are the same</span></span>
## <a name="details"></a><span data-ttu-id="d1dda-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d1dda-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="d1dda-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d1dda-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="d1dda-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d1dda-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="d1dda-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d1dda-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="d1dda-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d1dda-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d1dda-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="d1dda-108"> EDI</span></span> |
|    <span data-ttu-id="d1dda-109">元件</span><span class="sxs-lookup"><span data-stu-id="d1dda-109">Component</span></span>    |                                       <span data-ttu-id="d1dda-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d1dda-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="d1dda-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d1dda-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="d1dda-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d1dda-112">Message Text</span></span>   |          <span data-ttu-id="d1dda-113">分隔符號不是唯一的，欄位及區段的分隔符號相同</span><span class="sxs-lookup"><span data-stu-id="d1dda-113">Delimiters are not unique, field and segment separator are the same</span></span>           |
  
## <a name="explanation"></a><span data-ttu-id="d1dda-114">說明</span><span class="sxs-lookup"><span data-stu-id="d1dda-114">Explanation</span></span>  
 <span data-ttu-id="d1dda-115">這個錯誤/警告/資訊事件表示 EDI 傳送管線無法處理外寄交換，因為資料元素與區段分隔符號值相同。</span><span class="sxs-lookup"><span data-stu-id="d1dda-115">This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because the data element and segment separators were the same value.</span></span> <span data-ttu-id="d1dda-116">在 X12 中資料元素分隔符號的交換，在 ISA 區段的第四個字元位置的字元而區段結束字元是最後一個字元位置的 ISA 區段中的字元。</span><span class="sxs-lookup"><span data-stu-id="d1dda-116">In an X12 interchange, the data element separator is the character in the fourth character position of the ISA segment and the segment terminator is the character in the last character position of the ISA segment.</span></span> <span data-ttu-id="d1dda-117">在 EDIFACT 交換，資料元素分隔符號是 UNA2 欄位中的字元，區段結束字元是 [una6] 欄位中的字元。</span><span class="sxs-lookup"><span data-stu-id="d1dda-117">In an EDIFACT interchange, the data element separator is the character in the UNA2 field and the segment terminator is the character in the UNA6 field.</span></span> <span data-ttu-id="d1dda-118">具有相同值的兩個分隔符號可能會發生 （但會導致錯誤狀況） 在保留批次案例中，或如果交換是透過通過傳輸接收，然後挑選最多的傳送埠即 MessageBox 中的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d1dda-118">Two separators with the same value can occur (but will cause an error condition) in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d1dda-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d1dda-119">User Action</span></span>  
 <span data-ttu-id="d1dda-120">若要解決這個錯誤，請變更的值中的資料元素或區段分隔符號的交換，然後再重新送出交換。</span><span class="sxs-lookup"><span data-stu-id="d1dda-120">To resolve this error, change the value of either the data element or segment separator in the interchange, and then resubmit the interchange.</span></span>
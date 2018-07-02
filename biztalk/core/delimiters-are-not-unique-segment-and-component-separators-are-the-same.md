---
title: 不是唯一分隔符號，區段和元件分隔符號相同 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 13c41899-02af-4678-a4ad-f3dc48c1fdfb
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6068b13502b8893fd5065957b6dd73072236126
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983775"
---
# <a name="delimiters-are-not-unique-segment-and-component-separators-are-the-same"></a><span data-ttu-id="e8f5a-102">不是唯一分隔符號，區段和元件分隔符號相同</span><span class="sxs-lookup"><span data-stu-id="e8f5a-102">Delimiters are not unique, segment and component separators are the same</span></span>
## <a name="details"></a><span data-ttu-id="e8f5a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e8f5a-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="e8f5a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e8f5a-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="e8f5a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e8f5a-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="e8f5a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e8f5a-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="e8f5a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e8f5a-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e8f5a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="e8f5a-108"> EDI</span></span> |
|    <span data-ttu-id="e8f5a-109">元件</span><span class="sxs-lookup"><span data-stu-id="e8f5a-109">Component</span></span>    |                                       <span data-ttu-id="e8f5a-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="e8f5a-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="e8f5a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e8f5a-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="e8f5a-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e8f5a-112">Message Text</span></span>   |        <span data-ttu-id="e8f5a-113">不是唯一分隔符號，區段和元件分隔符號相同</span><span class="sxs-lookup"><span data-stu-id="e8f5a-113">Delimiters are not unique, segment and component separators are the same</span></span>        |
  
## <a name="explanation"></a><span data-ttu-id="e8f5a-114">說明</span><span class="sxs-lookup"><span data-stu-id="e8f5a-114">Explanation</span></span>  
 <span data-ttu-id="e8f5a-115">這個錯誤/警告/資訊事件表示，EDI 傳送管線無法處理外寄交換因為區段結束字元或元件分隔符號相同的值。</span><span class="sxs-lookup"><span data-stu-id="e8f5a-115">This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because the segment terminator or the component separator were the same value.</span></span> <span data-ttu-id="e8f5a-116">在 X12 交換，區段結束字元是最後一個字元位置的 ISA 區段中的字元，元件分隔符號是 ISA16 欄位中的字元。</span><span class="sxs-lookup"><span data-stu-id="e8f5a-116">In an X12 interchange, the segment terminator is character in the last character position of the ISA segment and the component separator is the character in the ISA16 field.</span></span> <span data-ttu-id="e8f5a-117">在 EDIFACT 交換，區段結束字元是 una6 欄位中的字元，和元件分隔符號是 UNA1 欄位中的字元。</span><span class="sxs-lookup"><span data-stu-id="e8f5a-117">In an EDIFACT interchange, the segment terminator is the character in the UNA6 field and the component separator is the character in the UNA1 field.</span></span> <span data-ttu-id="e8f5a-118">具有相同值的兩個分隔符號可能會發生 （但會導致錯誤狀況） 在保留批次案例中，或如果交換是透過通過傳輸接收，然後挑選最多的傳送埠即 MessageBox 中的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="e8f5a-118">Two separators with the same value can occur (but will cause an error condition) in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e8f5a-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e8f5a-119">User Action</span></span>  
 <span data-ttu-id="e8f5a-120">若要解決這個錯誤，區段結束字元或交換中的元件分隔符號的值變更，然後再重新送出交換。</span><span class="sxs-lookup"><span data-stu-id="e8f5a-120">To resolve this error, change the value of either the segment terminator or the component separator in the interchange, and then resubmit the interchange.</span></span>
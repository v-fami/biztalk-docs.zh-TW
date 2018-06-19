---
title: 分隔符號不是唯一的是相同的欄位及區段分隔符號 |Microsoft 文件
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
ms.openlocfilehash: 440ffb1213936fba4b08a8ee478f6c141eba38fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238726"
---
# <a name="delimiters-are-not-unique-field-and-segment-separator-are-the-same"></a><span data-ttu-id="1a827-102">分隔符號不是唯一的，欄位及區段的分隔符號相同</span><span class="sxs-lookup"><span data-stu-id="1a827-102">Delimiters are not unique, field and segment separator are the same</span></span>
## <a name="details"></a><span data-ttu-id="1a827-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1a827-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a827-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1a827-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="1a827-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1a827-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="1a827-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1a827-106">Event ID</span></span>|-|  
|<span data-ttu-id="1a827-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="1a827-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1a827-108">EDI</span><span class="sxs-lookup"><span data-stu-id="1a827-108"> EDI</span></span>|  
|<span data-ttu-id="1a827-109">元件</span><span class="sxs-lookup"><span data-stu-id="1a827-109">Component</span></span>|<span data-ttu-id="1a827-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="1a827-110">EDI Engine</span></span>|  
|<span data-ttu-id="1a827-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1a827-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="1a827-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1a827-112">Message Text</span></span>|<span data-ttu-id="1a827-113">分隔符號不是唯一的，欄位及區段的分隔符號相同</span><span class="sxs-lookup"><span data-stu-id="1a827-113">Delimiters are not unique, field and segment separator are the same</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1a827-114">說明</span><span class="sxs-lookup"><span data-stu-id="1a827-114">Explanation</span></span>  
 <span data-ttu-id="1a827-115">這個錯誤/警告/資訊事件表示 EDI 傳送管線無法處理外寄交換，因為資料元素與區段分隔符號值相同。</span><span class="sxs-lookup"><span data-stu-id="1a827-115">This Error/Warning/Information event indicates that the EDI send pipeline could not process an outgoing interchange because the data element and segment separators were the same value.</span></span> <span data-ttu-id="1a827-116">中的 X12 交換，資料元素分隔符號是 ISA 區段的第四個字元的位置中的字元，區段結束字元是最後一個字元位置的 ISA 區段中的字元。</span><span class="sxs-lookup"><span data-stu-id="1a827-116">In an X12 interchange, the data element separator is the character in the fourth character position of the ISA segment and the segment terminator is the character in the last character position of the ISA segment.</span></span> <span data-ttu-id="1a827-117">在 EDIFACT 交換中，資料元素分隔符號是 UNA2 欄位中的字元，區段結束字元是 [UNA6] 欄位中的字元。</span><span class="sxs-lookup"><span data-stu-id="1a827-117">In an EDIFACT interchange, the data element separator is the character in the UNA2 field and the segment terminator is the character in the UNA6 field.</span></span> <span data-ttu-id="1a827-118">兩個具有相同值的分隔符號可能 （但會導致錯誤狀況） 中保留的批次的案例中，或交換是透過傳遞傳輸接收，然後挑選向上為 MessageBox 中 XML 檔案傳送埠。</span><span class="sxs-lookup"><span data-stu-id="1a827-118">Two separators with the same value can occur (but will cause an error condition) in a preserved batch scenario, or if an interchange is received via a passthrough transmit and then picked up by the send port as an XML file in the MessageBox.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1a827-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1a827-119">User Action</span></span>  
 <span data-ttu-id="1a827-120">若要解決這個錯誤，變更值的其中一個交換中的資料元素或區段分隔符號，並再重新送出交換。</span><span class="sxs-lookup"><span data-stu-id="1a827-120">To resolve this error, change the value of either the data element or segment separator in the interchange, and then resubmit the interchange.</span></span>